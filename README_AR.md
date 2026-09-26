# WH Auto 2.0 — Independent Park Monitor

هذه النسخة تعيد بناء المشروع كتطبيق مستقل قدر الإمكان، ولا تحتاج BYDMate أو AutoTark لكي تعمل الواجهة أو ترفع البيانات إلى السحابة.

## car-agent داخل السيارة
- واجهة Premium عربية/إنجليزية منظمة.
- صفحات مستقلة للبطارية، الإطارات، الشحن، الاتصال وقاعدة الرحلات.
- خريطة OpenStreetMap.
- طقس Open‑Meteo.
- تحديد موقع السيارة اختياري بإذن المستخدم.
- Local API على المنفذ 8765.
- Cloud uploader مستقل إلى Cloudflare عبر Vodafone أو Wi‑Fi.
- تحديث تقريباً كل 60 ثانية أثناء الوقوف، و15 ثانية أثناء الشحن/الحركة.
- إعداد Cloud URL و TELEMETRY_SECRET من داخل التطبيق.

## مصادر بيانات السيارة المستقلة
- BYD framework getters التي يسمح بها النظام.
- DiCarServer / SPI بوضع read-only.
- EnergyData SQLite بوضع read-only.

لا يعتمد المصدر الأساسي على BYDMate أو AutoTark. بعض بيانات BYD في هذا firmware محمية بصلاحيات signature، لذلك قد تبقى بعض القيم فارغة إلى أن يتوفر API رسمي/T‑Box مناسب. التطبيق لا يحاول تجاوز حماية Android.

## mobile-app
تطبيق هاتف لمراقبة السيارة من المنزل عبر:
`https://wh-auto-cloud.waleed5004.workers.dev/api/latest`

يعرض حالة الاتصال، SOC، الشحن، Last Seen، العداد، الحرارة، القدرة والخريطة عند توفر الإحداثيات.

## إعداد السحابة داخل car-agent
- Enable cloud: ON
- URL:
  `https://wh-auto-cloud.waleed5004.workers.dev/api/bydmate/telemetry`
- TELEMETRY_SECRET:
  ضع نفس السر الذي أنشأته في Cloudflare.

اسم route يحتوي bydmate فقط لأنه endpoint المنشور بالفعل على Worker؛ WH Auto 2.0 يرسل JSON الخاص به مباشرة ولا يحتاج BYDMate.

## Deep Sleep
WH Auto يرسل طالما Android/DiLink والمودم يعملان. في Deep Sleep الحقيقي يتوقف Android نفسه، لذلك يعرض السيرفر آخر قراءة وLast Seen حتى الاستيقاظ. الوصول إلى بيانات جديدة أثناء Deep Sleep يحتاج قناة T‑Box/خدمة رسمية.

## البناء
افتح مجلد `WH_Auto_v2.0` في Android Studio، ثم:
`Build → Build APK(s)`

APK السيارة:
`car-agent/build/outputs/apk/debug/car-agent-debug.apk`

APK الهاتف:
`mobile-app/build/outputs/apk/debug/mobile-app-debug.apk`

## الإصدار
- versionName: 2.0.0
- versionCode: 30
