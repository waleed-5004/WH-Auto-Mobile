# WH Auto v0.7 — Findings

تم تحليل BYDMate-3.11.8.apk مباشرة.

أهم الاكتشافات داخل BYDMate:
- المسار:
  `/storage/emulated/0/energydata`
- الأسماء:
  `energydata.db`
  `EnergyConsumption.db`
  `EnergyDataReader`
  `EnergyConsumption`
- حقول/مفاهيم ظهرت داخل التطبيق:
  `soc`
  `soc_percent`
  `mileage`
  `mileage_km`
  `total_elec`
  `total_elec_kwh`
  `rangeKm`
  `estimatedRangeKm`
  `rangeKmAt100Soc`

هذا يدل أن BYDMate لديه مسار قراءة يعتمد على ملفات/قواعد بيانات energydata،
وليس فقط على BYD SPI.

لذلك v0.7 لا تعيد تجربة getService فقط.
هي تفحص هذا المسار قراءة فقط ثم تبقي تشخيص SPI v0.6 كمسار ثانٍ.

## ما ستظهره الشاشة

ابحث عن أسطر تبدأ بـ:
- `bydmate.energydata.root`
- `bydmate.energydata.files`
- `bydmate.db.`
- `bydmate.energydata.summary`
- `v0.7.source`

إذا ظهر:
`bydmate.energydata.root: FOUND`
فهذا تقدم مهم جدًا.

إذا ظهر أيضًا:
`usable=true`
ومعه SOC أو Range، فقد وصلنا لأول مصدر فعلي للبيانات بدون الاعتماد على BYD signature permissions.
