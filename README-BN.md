# English Master AI — Version 1.1

বাংলা সহায়তায় ইংরেজি শেখার mobile-friendly PWA। Version 1.1-এ Tutor session goal, duration preference, practice prompt, privacy pre-check এবং supervised Live AI backend gate যোগ হয়েছে।

## Frontend
- পূর্বের Lesson, Vocabulary, Grammar, 12 Tenses, Smart Revision, Daily Quiz, Listening ও Guided Tutor Practice বজায় আছে।
- Tutor level, mode, daily learning goal এবং session-duration preference নির্বাচন করা যায়।
- Live reply format: English + Practice + বাংলা সহায়তা।
- Email, ফোন নম্বর, password/OTP এবং কিছু personal-detail pattern browser-এই block করা হয়; backend-এও পুনরায় পরীক্ষা হয়।
- Chat transcript Local Storage-এ রাখা হয় না; শুধু tutor counters ও learning progress থাকে।
- Original `ema_v1_progress` storage key unchanged.

## Live AI status
Live AI is **not automatically enabled** by uploading the frontend. It requires an adult-managed backend, parent/guardian consent, access restrictions for intended testers, human monitoring and escalation, cost controls, Turnstile, API moderation, and secure API key storage. The Worker now refuses Live AI unless four adult-admin attestation flags are true in the backend environment. Those flags are declarations, not proof that controls exist.

Do not use this beta as a public service for minors. Before wider release, complete a professional safety/privacy review, implement verified user access, parent/guardian consent workflows, moderation and human reporting/escalation, and reliable spend controls. Cloudflare's per-IP rate limiter is not a hard billing cap.

## Adult-admin-only backend requirements
Required Cloudflare secrets:
- `OPENAI_API_KEY`
- `TURNSTILE_SECRET`

Required Cloudflare Rate Limiting binding:
- `CHAT_LIMITER`

Required administrator-controlled environment variables (set only after each safeguard is actually in place):
- `GUARDIAN_APPROVAL_COMPLETE=true`
- `STUDENT_ACCESS_CONTROL_READY=true`
- `HUMAN_MONITORING_READY=true`
- `SPEND_LIMITS_READY=true`

If any is missing, `/health` reports `configured:false` and `/api/chat` remains disabled.

## Files
Public GitHub Pages frontend (six files): `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`, `README-BN.md`.

Adult-admin backend files: `worker.js`, `wrangler.jsonc`, `BACKEND-SETUP-BN.md`.

Never commit API keys, Turnstile Secret, `.env`, `.dev.vars`, or other secrets.
