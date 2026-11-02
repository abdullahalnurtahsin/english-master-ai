# English Master AI — সংস্করণ 0.3

বাংলা সহায়তায় Beginner ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA।

## এই সংস্করণে যা আছে
- Lesson 01: নিজের পরিচয় দেওয়া — ১০টি বাক্য, বাংলা অর্থ ও বাংলা উচ্চারণ
- ব্রাউজারের Speech Synthesis দিয়ে ইংরেজি বাক্য শোনা
- ২০টি শব্দ, বাংলা অর্থ, উদাহরণ, সার্চ ও শেখা-চিহ্ন
- Grammar Master-এর ৪টি প্রাথমিক অধ্যায়: Pronouns ও be verb, A/An, Simple Present, Present Continuous
- প্রতিটি Grammar অধ্যায়ে বাংলা ব্যাখ্যা, উদাহরণ, উচ্চারণ শোনা ও নিজেকে যাচাই করার প্রশ্ন
- Grammar অধ্যায়ের সম্পন্ন অগ্রগতি, শব্দ শেখা ও কুইজের সেরা ফল একই ব্রাউজারের Local Storage-এ সংরক্ষণ
- ৮ প্রশ্নের কুইজ এবং একটি লিখিত অনুশীলন
- Service worker দিয়ে মৌলিক offline cache; নতুন সংস্করণে cache version v3 করা হয়েছে

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
4. এই ফোল্ডারের ভেতরের ফাইলগুলো root-এ upload করো: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`। চাইলে `README-BN.md`-ও upload করো।
5. পুরোনো ফাইলের একই নাম হলে GitHub replacement দেখাবে; আপডেট commit করো।
6. Pages settings আগের মতো `main` এবং `/(root)` থাকবে। Deploy শেষ হলে website refresh করো।

## প্রকাশিত ঠিকানা
`https://abdullahalnurtahsin.github.io/english-master-ai/`
