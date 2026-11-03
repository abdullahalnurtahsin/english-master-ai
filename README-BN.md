# English Master AI — সংস্করণ 0.8

বাংলা সহায়তায় ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA।

## এই সংস্করণে যা আছে
- Version 0.7-এর সব সুবিধা বজায়: Lesson 01, ২০০টি Vocabulary শব্দ, Grammar-এর ৪টি অধ্যায়, ১২টি Tense, Smart Revision, Daily Goal, Daily Quiz ও চারটি Listening অনুশীলন।
- **Tutor Practice Beta:** তিনটি নির্দিষ্ট Beginner topic — Introducing Yourself, Daily Routine, Hobbies & Interests; প্রতিটিতে ৫টি প্রশ্ন, বাংলা hint, নমুনা উত্তর, বাক্য-গঠন যাচাই ও Text-to-Speech।
- **Optional microphone input:** ব্রাউজার Speech Recognition সমর্থন করলে কণ্ঠ থেকে টেক্সট ইনপুট বসাতে পারে; না হলে কিবোর্ডে উত্তর দেওয়া যাবে।
- **Privacy:** Tutor-এর raw answer/chat transcript Local Storage-এ রাখা হয় না। শুধু sessions, aggregate score, topic completion ও last session date সংরক্ষিত হয়। চাইলে কাল্পনিক নাম/তথ্য ব্যবহার করা যায়।
- **Progress compatibility:** পুরোনো `ema_v1_progress` Local Storage key এবং আগের Vocabulary indexes অপরিবর্তিত। Tutor aggregate progress একই object-এর `tutor` field-এ থাকে।
- Service worker cache version `english-master-ai-v8`।

## গুরুত্বপূর্ণ: এটি Live AI নয়
Tutor Practice Beta হলো নির্দিষ্ট প্রশ্ন ও নিয়মভিত্তিক বাক্য-গঠন যাচাইয়ের guided demo। এটি মুক্তভাবে যেকোনো প্রশ্ন বুঝতে, সব ধরনের grammar error ধরতে বা নিজে নতুন উত্তর তৈরি করতে পারে না। কোনো OpenAI API বা অন্য AI model সংযুক্ত করা হয়নি।

প্রকৃত AI Tutor যোগ করতে হলে নিরাপদ server-side backend, access control, rate limit, usage monitoring এবং বয়স-উপযোগী safety/privacy ব্যবস্থা দরকার। API key কখনো `index.html`, browser code, Android app বা public GitHub repository-তে রাখা যাবে না; OpenAI-ও API key browser/app-এ প্রকাশ না করে backend-এ রাখার নির্দেশ দেয়। See: https://developers.openai.com/api/reference/overview and https://help.openai.com/en/articles/5112595-best-practices-for-api-key-safety

## Microphone ও audio
- Question/sample voice browser `SpeechSynthesis` দিয়ে তৈরি হয়; কণ্ঠ ডিভাইসভেদে আলাদা হতে পারে।
- Microphone input browser-এর `SpeechRecognition`/`webkitSpeechRecognition` API থাকলে কাজ করবে। সব browser বা device-এ সমর্থিত নয়।
- Speech recognition browser/device service ব্যবহার করতে পারে। ব্যক্তিগত বা সংবেদনশীল তথ্য মাইক্রোফোনে বলবে না।

## GitHub-এ আপডেট
1. ZIP Extract করো।
2. Repository `english-master-ai` খোলো।
3. `Add file` → `Upload files` নির্বাচন করো।
4. এই ফোল্ডারের ভেতরের **সব ৬টি ফাইল** root-এ upload করো: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`।
5. একই নামের পুরোনো ফাইল replace করে Commit changes করো; আগে delete করার প্রয়োজন নেই।
6. Pages branch `main` এবং folder `/(root)` আগের মতো থাকবে। Deploy শেষ হলে website reload করো। পুরোনো cached copy দেখালে কিছুক্ষণ অপেক্ষা করে close/reopen বা নতুন private tab-এ পরীক্ষা করো। **Site Data / Local Storage মুছবে না।**

## প্রকাশিত ঠিকানা
`https://abdullahalnurtahsin.github.io/english-master-ai/`
