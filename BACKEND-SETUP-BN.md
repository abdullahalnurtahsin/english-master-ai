# English Master AI 1.0 — Backend Setup (বাংলা)

## গুরুত্বপূর্ণ: এই কাজটি অভিভাবক/অভিভাবিকার তত্ত্বাবধানে হবে

এই অ্যাপ কিশোর শিক্ষার্থীরাও ব্যবহার করতে পারে। OpenAI-এর Under-18 API Guidance অনুযায়ী অপ্রাপ্তবয়স্কদের জন্য বয়সোপযোগী AI অভিজ্ঞতা, কনটেন্ট ফিল্টার, যথাযথ তদারকি ও প্রযোজ্য অভিভাবকীয় সম্মতি দরকার। OpenAI Services Agreement-এও অপ্রাপ্তবয়স্ক End User-দের জন্য parent/guardian consent-এর কথা আছে। তাই API account, billing, Worker backend, secret এবং deployment একজন অভিভাবক/প্রাপ্তবয়স্ক পরিচালনা করবেন।

**Google Gemini API ব্যবহার করা হয়নি**: এর বর্তমান Additional Terms-এ API ব্যবহারকারীর বয়স ১৮+ এবং under-18 audience-এ থাকা অ্যাপের ব্যবহার নিষিদ্ধ বলা আছে।

## আর্কিটেকচার

- Public frontend: GitHub Pages (`https://abdullahalnurtahsin.github.io/english-master-ai/`)
- Secure backend: Cloudflare Worker (`worker.js`)
- AI provider: OpenAI Responses API
- Safety: input/output Moderation API, safe tutor instructions, Turnstile server verification, rate limit binding, request size limits
- Privacy: chat transcript browser Local Storage-এ রাখা হয় না; Worker-এ log করা হয় না; Responses API request-এ `store:false` দেওয়া হয়। এটি provider-side abuse monitoring বা আইনগত retention শূন্য করার নিশ্চয়তা নয়।

## খরচ

Cloudflare Workers Free plan-এ বর্তমানে 100,000 requests/day সীমা দেখানো হয়েছে; এটি Cloudflare Worker-এর সীমা, OpenAI API usage এর অন্তর্ভুক্ত নয়। OpenAI API আলাদা token-based billed service—এটি ChatGPT Go/Plus সাবস্ক্রিপশনের মধ্যে ফ্রি API credit নয়। `gpt-6-astra` বেছে নেওয়া হয়েছে কারণ under-18 guidance সর্বশেষ flagship model ব্যবহারের পরামর্শ দেয়; এতে খরচ হতে পারে। শুরু করার আগে অভিভাবক Project budget/usage alert ও ছোট usage limit নির্ধারণ করবেন।

## অভিভাবক/পরিচালকের কাজ (Cloudflare Dashboard; Android Browser থেকেও করা যায়)

1. অভিভাবক নিজের উপযুক্ত Cloudflare account দিয়ে Workers & Pages খুলবেন।
2. Turnstile-এ একটি Widget তৈরি করবেন এবং hostname হিসেবে `abdullahalnurtahsin.github.io` যুক্ত করবেন। Site Key (public) ও Secret Key (private) পাবেন।
3. Workers & Pages → Create → Worker → নাম `english-master-ai-api` দিয়ে Worker তৈরি করবেন।
4. Worker code editor-এ `worker.js` ফাইলের সম্পূর্ণ কোড বসিয়ে Save and Deploy করবেন।
5. Worker → Settings → Variables and Secrets → Add → **Secret** থেকে `OPENAI_API_KEY` নামে API key সংরক্ষণ করবেন। আবার Add → **Secret** থেকে `TURNSTILE_SECRET` নামে Turnstile Secret সংরক্ষণ করবেন। Secret কখনো Plaintext variable, GitHub, `index.html`, এই অ্যাপ, বা Chat-এ লিখবেন না। Cloudflare secret values encrypted ভাবে Worker-এ দেয়।
6. Worker → Settings → Bindings-এ Rate Limiting binding যোগ করুন:
   - Binding name: `CHAT_LIMITER`
   - Namespace ID: `1001001`
   - Limit: `8`
   - Period: `60` seconds
   Dashboard-এ এই binding option না থাকলে Wrangler configuration-এ থাকা `wrangler.jsonc` ব্যবহার করে deploy করতে হবে। Binding ছাড়া Worker ইচ্ছাকৃতভাবে Live AI request বন্ধ রাখবে। Rate limiting approximate এবং Cloudflare location অনুযায়ী সীমা প্রয়োগ হয়; এটি exact billing cap নয়।
7. Worker-এর `workers.dev` URL কপি করুন। উদাহরণ: `https://english-master-ai-api.<account>.workers.dev`।
8. English Master AI ওয়েবসাইটে AI Tutor → Live AI সংযোগ অংশে Backend URL এবং Turnstile **Site Key** (Secret Key নয়) বসিয়ে সংরক্ষণ ও পরীক্ষা করুন।
9. Health check-এ `Backend ready` হলে Turnstile verification সম্পন্ন করে AI Tutor-এ ছোট নিরীহ ইংরেজি শেখার প্রশ্ন পাঠান।

## GitHub-এ কোন ফাইল আপলোড হবে?

GitHub-এর Public Repository-তে শুধু এই ৬টি frontend ফাইল আপলোড/Replace করুন:

- `index.html`
- `manifest.json`
- `service-worker.js`
- `icon-192.png`
- `icon-512.png`
- `README-BN.md`

**`worker.js`, `wrangler.jsonc`, `BACKEND-SETUP-BN.md` GitHub Pages-এর frontend হিসাবে আপলোড করা প্রয়োজন নেই।** এগুলো অভিভাবক/পরিচালক Cloudflare backend setup-এর জন্য ব্যবহার করবেন। `worker.js` ফাইলে কোনো Secret নেই, তবু backend code আলাদা রাখাই ভালো।

## Live AI চালুর আগে বাধ্যতামূলক সীমাবদ্ধতা

এই Worker একটি **শিক্ষামূলক সীমিত Beta starter**, জনসাধারণের জন্য প্রস্তুত production service নয়। বর্তমান প্যাকেজে এখনো নিচের বিষয়গুলো নেই:

- শিক্ষার্থী-ভিত্তিক লগইন/অ্যাক্সেস নিয়ন্ত্রণ বা নির্ভরযোগ্য বয়স যাচাই নেই; GitHub Pages সাইটটি Public।
- অভিভাবক/শিক্ষকের কাছে নিরাপদ রিপোর্ট পাঠানো, মানব পর্যবেক্ষণ এবং উচ্চ-ঝুঁকির ঘটনার escalation workflow নেই।
- OpenAI API খরচের জন্য hard monthly spend cap নেই। Cloudflare-এর ৮ request/৬০ সেকেন্ড rate limit কেবল প্রাথমিক অপব্যবহার কমায়; এটি খরচের নিশ্চয়তাপূর্ণ সীমা নয়।

তাই অভিভাবক/পরিচালক এই তিনটি বিষয় সমাধান না করা পর্যন্ত Live AI-কে **সাধারণ/পাবলিক শিক্ষার্থীদের জন্য চালু করবেন না**। শুধু অভিভাবক-অনুমোদিত, নিয়ন্ত্রিত পরীক্ষা বিবেচনা করা যেতে পারে।

## নিরাপত্তা ও গোপনীয়তা

- API key শুধু Cloudflare Worker Secret-এ থাকবে।
- Frontend-এ কেবল Backend URL এবং Turnstile public Site Key থাকবে।
- Live chat-এ সর্বশেষ ৮টি message পর্যন্ত পাঠানো হয়; Local Storage-এ transcript রাখা হয় না।
- Backend input/output moderation চালায়। পরিচয়-সংক্রান্ত তথ্য যেমন email/phone/password pattern পেলে API-তে পাঠানোর আগেই request থামায়।
- কোনো chat-এ পূর্ণ নাম, ফোন, email, বাসার ঠিকানা, স্কুল, পাসওয়ার্ড বা সংবেদনশীল তথ্য লিখবে না।
- Public GitHub Pages মানে ওয়েবসাইট সবার জন্য দৃশ্যমান। Live backend চালু করার আগে অভিভাবক কে ব্যবহার করতে পারবে, খরচ ও safety পর্যবেক্ষণ করবেন।
- Cloudflare Turnstile client widget একা যথেষ্ট নয়; backend-এ Siteverify দিয়ে server-side token verification করা হয়।
- Rate limit shared IP-তে কয়েকজনের ব্যবহার একসঙ্গে গণনা করতে পারে; তাই কারও quota শেষ হলে অভিভাবক সেটিংস পর্যালোচনা করবেন।

## Troubleshooting

- `/health` এ `configured:false`: API Secret, Turnstile Secret, অথবা `CHAT_LIMITER` binding অনুপস্থিত।
- `Human verification failed`: Turnstile hostname `abdullahalnurtahsin.github.io`, action `ema_chat`, Site Key/Secret মিলেছে কি না পরীক্ষা করুন।
- CORS/Forbidden: Backend origin অবশ্যই `https://abdullahalnurtahsin.github.io` হবে।
- 429: Rate limit হয়েছে; ১ মিনিট পরে চেষ্টা করুন। OpenAI project budget/usage limit-ও পরীক্ষা করুন।
- 502: API provider বা network সমস্যা হতে পারে; Secret কখনো চ্যাটে পাঠাবেন না।

## Official references

- OpenAI Under-18 API Guidance: https://developers.openai.com/api/docs/guides/safety-checks/under-18-api-guidance
- OpenAI Moderation: https://developers.openai.com/api/docs/guides/moderation
- OpenAI Responses API: https://developers.openai.com/api/reference/resources/responses/methods/create
- OpenAI Pricing: https://developers.openai.com/api/docs/pricing
- Cloudflare Worker Secrets: https://developers.cloudflare.com/workers/configuration/secrets/
- Cloudflare Turnstile server-side validation: https://developers.cloudflare.com/turnstile/get-started/server-side-validation/
- Cloudflare Rate Limiting: https://developers.cloudflare.com/workers/runtime-apis/bindings/rate-limit/
