# English Master AI — সংস্করণ 0.9

বাংলা সহায়তায় ইংরেজি শেখার মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA।

## আগের সংস্করণের সুবিধা
- Lesson 01 এবং নিজের পরিচয় তৈরি।
- ২০০টি Vocabulary শব্দ, অর্থ, উচ্চারণ-সহায়তা, উদাহরণ ও কুইজ।
- Grammar-এর ৪টি অধ্যায় এবং ১২টি Tense।
- Smart Revision, Daily Goal, ভুল শব্দের তালিকা ও Daily Quiz।
- Listening-এর চারটি অনুশীলন: Word, Sentence, Conversation ও Dictation।
- Version 0.8 Guided Tutor Practice এবং microphone input।

## Version 0.9 — Smart Tutor Preview
- নতুন Chat-style Tutor interface।
- Beginner, Elementary ও Intermediate স্তর নির্বাচন।
- Daily Conversation, Sentence Correction, Grammar Help, Vocabulary Help ও Writing Practice mode।
- কয়েকটি প্রচলিত Grammar ভুলের সংশোধন ও বাংলা ব্যাখ্যা।
- Built-in Vocabulary তালিকা থেকে শব্দের অর্থ ও উদাহরণ খোঁজা।
- স্তর ও mode অনুযায়ী অনুশীলনের prompt তৈরি।
- Tutor উত্তর Text-to-Speech দিয়ে শোনা এবং সমর্থিত browser-এ optional voice input।
- Aggregate chat sessions, message count ও correction-help count সংরক্ষণ।
- Chat transcript বা user-এর লেখা উত্তর Local Storage-এ সংরক্ষণ করা হয় না।

## গুরুত্বপূর্ণ সীমাবদ্ধতা
Version 0.9-এর Smart Tutor Preview **প্রকৃত Live AI chatbot নয়**। এটি browser-এর ভেতরে curated rule ও built-in content দিয়ে কাজ করে। কিছু পরিচিত ভুল ধরতে পারে, কিন্তু সব grammar error বা যেকোনো প্রশ্ন বুঝতে পারে না। “ভুল খুঁজে পায়নি” মানেই বাক্যটি শতভাগ সঠিক—এমন নয়।

প্রকৃত AI Tutor-এর জন্য HTTPS frontend-এর সঙ্গে নিরাপদ server-side backend, authentication/access control, rate limit, abuse protection, usage monitoring এবং privacy/safety checks দরকার। API key কখনো `index.html`, JavaScript, Android app বা public GitHub repository-তে রাখা যাবে না। Version 0.9-এ কোনো API key বা external AI endpoint যোগ করা হয়নি।

## Progress compatibility ও গোপনীয়তা
- আগের `ema_v1_progress` Local Storage key অপরিবর্তিত।
- `learned` Vocabulary indexes এবং পুরোনো `tutor` progress field অপরিবর্তিত।
- নতুন chat progress শুধু `saved.tutor.chatSessions`, `chatMessages`, `chatCorrections` aggregate counter হিসেবে যোগ হয়।
- Chat message, নাম, শহর বা ব্যক্তিগত উত্তরের transcript সংরক্ষণ হয় না। পেজ বন্ধ করলে বর্তমান chat log মুছে যায়।
- Chrome-এর Site Data / Local Storage মুছবে না; তাতে আগের progress হারাতে পারে।

## Microphone ও audio
- Text-to-Speech ডিভাইস/ব্রাউজারের কণ্ঠ ব্যবহার করে।
- Voice input `SpeechRecognition`/`webkitSpeechRecognition` থাকলে কাজ করবে; সব Android browser-এ সমর্থিত নয় এবং browser/device speech service বা network প্রয়োজন হতে পারে। Voice input ঐচ্ছিক; keyboard ব্যবহার করা যাবে।
- ব্যক্তিগত বা সংবেদনশীল তথ্য মাইক্রোফোনে বলবে না।

## GitHub-এ আপডেট
1. ZIP Extract করো।
2. Repository `english-master-ai` খোলো।
3. `Add file` → `Upload files` নির্বাচন করো।
4. ভেতরের সব ৬টি ফাইল root-এ upload করো: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`।
5. একই নামের পুরোনো ফাইল replace করে Commit changes করো; আগে delete করতে হবে না।
6. Pages branch `main` এবং folder `/(root)` আগের মতো থাকবে। Deploy শেষে reload করো। Cached copy থাকলে কিছুক্ষণ অপেক্ষা করে reopen বা private tab-এ পরীক্ষা করো। Site Data/Local Storage মুছবে না।

## প্রকাশিত ঠিকানা
`https://abdullahalnurtahsin.github.io/english-master-ai/`
