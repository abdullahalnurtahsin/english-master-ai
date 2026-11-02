# English Master AI — সংস্করণ 0.4

বাংলা সহায়তায় Beginner ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA।

## এই সংস্করণে যা আছে
- Lesson 01: নিজের পরিচয় দেওয়া — ১০টি বাক্য, বাংলা অর্থ ও বাংলা উচ্চারণ
- ব্রাউজারের Speech Synthesis দিয়ে ইংরেজি বাক্য শোনা
- ২০টি শব্দ, বাংলা অর্থ, উদাহরণ, সার্চ ও শেখা-চিহ্ন
- Grammar Master-এর ৪টি প্রাথমিক অধ্যায়: Pronouns ও be verb, A/An, Simple Present, Present Continuous
- **Tense Master-এর ১২টি Tense** — Present, Past ও Future-এর চারটি করে Tense
- প্রতিটি Tense-এ ব্যবহার, affirmative/negative/question structure, বাংলা ব্যাখ্যা, উদাহরণ, উচ্চারণ ও MCQ অনুশীলন
- Tense, Grammar, শব্দ শেখা ও কুইজের অগ্রগতি একই ব্রাউজারের Local Storage-এ সংরক্ষণ
- ৮ প্রশ্নের প্রাথমিক কুইজ ও একটি লিখিত অনুশীলন
- Service worker দিয়ে মৌলিক offline cache; নতুন সংস্করণে cache version v4 করা হয়েছে

## শেখার পরামর্শ
- ১২টি Tense একদিনে মুখস্থ করার চেষ্টা কোরো না। প্রতিদিন ১–২টি Tense পড়ো।
- প্রতিটি Tense-এর affirmative, negative ও question form দিয়ে নিজের ৩টি বাক্য তৈরি করো।
- V1, V2 ও V3 আলাদা করে অনুশীলন করো।

## গুরুত্বপূর্ণ সীমাবদ্ধতা
- এখনো কোনো AI model বা API যুক্ত নেই। “AI Tutor” এখনো কাজ করে না।
- OpenAI API key বা অন্য কোনো secret কখনো `index.html`-এ রাখবে না।
- অগ্রগতি একই browser/device-এর local storage-এ থাকে; browser data মুছে গেলে তা হারাতে পারে।
- GitHub Pages-এ প্রকাশ করলে public repository-র কোড যে কেউ দেখতে পারবে। ব্যক্তিগত তথ্য রেখো না।
- উচ্চারণ শোনার সুবিধা browser ও device-এর speech synthesis engine-এর ওপর নির্ভরশীল।

## GitHub-এ আপডেট
1. ZIP extract করো।
2. Repository `english-master-ai` খোলো।
3. `Add file` → `Upload files` নির্বাচন করো।
4. এই ফোল্ডারের ভেতরের **সব ৬টি ফাইল** root-এ upload করো: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`।
5. একই নামের পুরোনো ফাইলগুলো replace করে commit করো।
6. Pages settings আগের মতো `main` এবং `/(root)` থাকবে। Deploy শেষ হলে website refresh করো। Browser-এ পুরোনো cache থাকলে একবার hard refresh বা private tab দিয়ে পরীক্ষা করো।

## প্রকাশিত ঠিকানা
`https://abdullahalnurtahsin.github.io/english-master-ai/`
