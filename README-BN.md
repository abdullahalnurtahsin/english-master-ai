# English Master AI — Version 1.0

বাংলা সহায়তায় ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি PWA। Version 1.0-এ নতুন নিরাপদ Live AI Tutor connector এবং Cloudflare Worker backend starter যুক্ত হয়েছে।

## Frontend features
- Lesson 01, ২০০ Vocabulary words, Grammar, ১২ Tense, quizzes.
- Smart Revision, Daily Goal, learning streak, wrong-word review.
- Listening: Word, Sentence, Conversation ও Dictation.
- Guided Tutor Practice এবং Local Practice Preview.
- Optional Live AI mode: parent/guardian-managed backend URL + public Turnstile Site Key.
- Recent conversation stays in memory only; chat transcript is not stored in Local Storage.
- Old `ema_v1_progress` key and learning progress structure remain unchanged.

## Live AI status
Version 1.0 package includes a secure backend starter (`worker.js`) but Live AI is **not activated by the GitHub Pages upload alone**. An adult parent/guardian must manage the API account, consent, billing, backend deployment, API key Secret, Turnstile, and safety controls. OpenAI API usage is billed separately; this is not included in a ChatGPT subscription. Do not paste any API key into the website, GitHub, or chat.

## Files
- Frontend for GitHub Pages: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`.
- Backend setup materials for an adult administrator: `worker.js`, `wrangler.jsonc`, `BACKEND-SETUP-BN.md`.

## গুরুত্বপূর্ণ Beta সীমা
Backend starter-টি এখনো public production-এর জন্য প্রস্তুত নয়। এতে শিক্ষার্থী-লগইন/বয়স যাচাই, অভিভাবক/শিক্ষক রিপোর্ট ও মানব escalation workflow, এবং hard monthly API spend cap নেই। Cloudflare rate limit খরচের গ্যারান্টিযুক্ত সীমা নয়। অভিভাবক/পরিচালক এই বিষয়গুলো বাস্তবায়ন না করা পর্যন্ত Live AI সাধারণ শিক্ষার্থীদের জন্য চালু করবেন না।

## GitHub Pages deployment
Upload/replace only the six frontend files in the root of the existing repository. Keep old learning progress by not clearing Chrome Site Data / Local Storage. Do not upload API secrets.

## Compatibility note
The app preserves `ema_v1_progress`. It does not store AI chat transcripts. In Live mode, the last eight chat messages are sent to the configured backend. The Worker calls OpenAI with `store:false`, but that does not guarantee zero provider-side retention for all purposes. Read `BACKEND-SETUP-BN.md` before enabling Live AI.
