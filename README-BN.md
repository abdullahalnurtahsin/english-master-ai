# English Master AI — সংস্করণ 0.7

বাংলা সহায়তায় ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA।

## এই সংস্করণে যা আছে
- Version 0.6-এর সব সুবিধা বজায়: Lesson 01, Vocabulary Master-এর ২০০টি শব্দ, Grammar-এর ৪টি অধ্যায়, ১২টি Tense, Smart Revision, Daily Goal, Daily Quiz ও ভুল শব্দের তালিকা।
- **Listening Master:** চারটি অনুশীলন — শব্দ শুনে অর্থ চেনা, বাক্য শুনে অর্থ বোঝা, ছোট কথোপকথন শুনে প্রশ্নের উত্তর দেওয়া, এবং শুনে ইংরেজি বাক্য টাইপ করা।
- **Audio speed:** ধীরে, একটু ধীরে ও স্বাভাবিক গতির বিকল্প।
- **Listening progress:** শব্দ, বাক্য, কথোপকথন ও dictation-এর অগ্রগতি, মোট session, প্রতিটি মডিউলের সেরা ফল এবং ভুল আইটেম সংরক্ষণ। কথোপকথন সম্পন্ন হিসেবে গণনা হবে তখনই, যখন ওই কথোপকথনের সব প্রশ্ন একই অনুশীলনে সঠিক হবে।
- **Progress compatibility:** পুরোনো `ema_v1_progress` Local Storage key এবং আগের Vocabulary word indexes অপরিবর্তিত। নতুন Listening data একই progress object-এর `listening` field-এ যোগ হয়।
- Service worker cache version `english-master-ai-v7`।

## Listening কীভাবে কাজ করে
- অডিও ব্রাউজার/ফোনের Web Speech `SpeechSynthesis` Text-to-Speech দিয়ে তৈরি হয়; কোনো prerecorded audio file ব্যবহার করা হয়নি।
- en-US voice পাওয়া গেলে সেটি ব্যবহারের চেষ্টা করে; না পেলে ডিভাইসের default English voice ব্যবহার হয়।
- TTS voice ও উচ্চারণ Android/Chrome ও ইনস্টল করা voice engine অনুযায়ী আলাদা হতে পারে।
- Audio না চললে ফোনের Settings → Text-to-Speech output-এ English voice/engine চালু করে Chrome আবার খোলো। ব্রাউজার TTS সমর্থন না করলে Listening audio পাওয়া যাবে না।
- Dictation-এ case ও সাধারণ punctuation উপেক্ষা করে শব্দের মিল যাচাই করা হয়; এটি speech recognition নয়—শিক্ষার্থী কীবোর্ডে উত্তর টাইপ করে।

## গুরুত্বপূর্ণ সীমাবদ্ধতা
- এখনো কোনো AI model বা API যুক্ত নেই। AI Tutor এখনো যুক্ত হয়নি।
- Listening voice হলো device-generated TTS; মানুষের রেকর্ড করা native-speaker audio নয়।
- Progress একই browser/device-এর Local Storage-এ থাকে; একাধিক ডিভাইসে sync হয় না। Browser-এর Site Data মুছলে অগ্রগতি হারাতে পারে।
- OpenAI API key বা অন্য কোনো secret কখনো `index.html`-এ রাখবে না।
- GitHub Pages-এ প্রকাশ করলে public repository-র কোড সবাই দেখতে পারবে। ব্যক্তিগত তথ্য রেখো না।

## GitHub-এ আপডেট
1. ZIP Extract করো।
2. Repository `english-master-ai` খোলো।
3. `Add file` → `Upload files` নির্বাচন করো।
4. এই ফোল্ডারের ভেতরের **সব ৬টি ফাইল** root-এ upload করো: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`।
5. একই নামের পুরোনো ফাইলগুলো replace করে commit করো। আলাদা করে delete করার প্রয়োজন নেই।
6. Pages settings আগের মতো `main` এবং `/(root)` থাকবে। Deploy শেষ হলে website reload করো। PWA পুরোনো কপি দেখালে কিছুক্ষণ অপেক্ষা করে পেজ বন্ধ/আবার খোলো বা Chrome-এর নতুন private tab-এ পরীক্ষা করো. **Site Data / Local Storage মুছবে না.**

## প্রকাশিত ঠিকানা
`https://abdullahalnurtahsin.github.io/english-master-ai/`
