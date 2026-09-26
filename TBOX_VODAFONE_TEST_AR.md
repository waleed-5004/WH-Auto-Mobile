# WH Auto 2.1 — T‑Box / Vodafone Monitor

هذه النسخة تضيف تشخيصاً آمناً لمسار الإنترنت الذي يستطيع Android داخل السيارة رؤيته.

المعلومات:
- CELLULAR / WIFI / ETHERNET / VPN.
- Validated Internet.
- اسم مشغل الشبكة/الشريحة إذا أتاحه Android.
- Metered / Roaming.
- Local IP.
- agentAlive = true في كل إرسال للسحابة.
- agentVersion = 2.1.0.

## اختبار النوم
1. ثبت car-agent 2.1 على السيارة.
2. افتح صفحة T-Box.
3. اضغط Refresh network.
4. فعّل Cloud بنفس TELEMETRY_SECRET.
5. تأكد من HTTP 200.
6. اقفل السيارة.
7. افتح /api/latest من المنزل وراقب ageSeconds.

إذا توقف received_at عن التغير وبدأ ageSeconds يرتفع، فهذا يعني أن Android لم يعد ينفذ التطبيق.
إذا استمرت الحزم، فالنظام ما زال مستيقظاً.

## مهم
هذه النسخة لا تمنع Deep Sleep، ولا توقظ السيارة بالقوة، ولا تتجاوز صلاحيات BYD.
هي لتحديد ما إذا كان مسار Vodafone/T‑Box ظاهرًا لنظام Android وكيف يتصرف أثناء الوقوف.
