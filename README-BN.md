# English Master AI — প্রথম প্রোটোটাইপ

এটি একটি বিনামূল্যের, মোবাইল-ফ্রেন্ডলি ওয়েব অ্যাপ/PWA starter। এতে আছে:

- Beginner Lesson 1: নিজের পরিচয় দেওয়া
- ইংরেজি বাক্য শোনার জন্য browser speech feature
- ১২টি শব্দের তালিকা, সার্চ এবং শেখা/না-শেখা চিহ্নিত করা
- ৫ প্রশ্নের কুইজ এবং স্থানীয়ভাবে অগ্রগতি সংরক্ষণ
- Service worker দিয়ে basic offline cache

## গুরুত্বপূর্ণ সীমাবদ্ধতা

- এখনো কোনো AI model বা API যুক্ত নেই। নামের মধ্যে “AI” থাকলেও এই প্রোটোটাইপটি এখন AI উত্তর তৈরি করে না।
- OpenAI API key বা অন্য কোনো secret কখনো `index.html`-এ রাখবে না।
- অগ্রগতি শুধু এই browser/device-এর local storage-এ থাকে; browser data মুছে গেলে তা হারাতে পারে।
- GitHub Pages-এ প্রকাশ করলে repository/public code সবাই দেখতে পারবে। এখানে ব্যক্তিগত তথ্য রাখবে না।

## GitHub Pages-এ প্রকাশ

1. ZIP extract করে ফাইলগুলো বের করো।
2. GitHub-এ `english-master-ai` নামে একটি **Public** repository বানাও।
3. এই ফোল্ডারের ভেতরের ফাইলগুলো repository-র root-এ upload করো (ফোল্ডার নিজে নয়): `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`। `README-BN.md`-ও upload করতে পারো।
4. Repository → Settings → Pages → Build and deployment → Source: `Deploy from a branch` নির্বাচন করো।
5. Branch: `main`, Folder: `/(root)` নির্বাচন করে Save করো।
6. Pages settings-এ প্রকাশিত URL এলে Chrome-এ খোলো। Chrome menu → `Install app` বা `Add to Home screen` চাপো।

GitHub Pages free public repository-তে ব্যবহার করা যায়। প্রকাশিত সাইট public হবে।
