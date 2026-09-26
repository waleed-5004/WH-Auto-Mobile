WH Auto 2.3.0 — BYD ContentProvider read-only probe

هذه النسخة تضيف اختبار قراءة فقط للمسارات التي ظهرت داخل DiCarServer.apk:

content://com.byd.carStatusProvider/car_status
content://com.byd.carStatusProvider/dicare_record
content://com.gpack.service.provider.VehicleServiceProvider/sync_binder
content://carsettings/settings
content://carsettings/global
content://carsettings/config

لا توجد كتابة أو تحكم في السيارة.

طريقة الاختبار:
1. Build car-agent.
2. ثبته على السيارة.
3. افتح Final.
4. اضغط Refresh final test.
5. انزل إلى:
   2. BYD ContentProvider probe
6. أرسل صورة هذا القسم فقط.

النتائج:
READ_OK = وصلنا فعلاً إلى صف بيانات.
QUERY_OK_NO_ROWS = المزود قابل للاستعلام لكنه لم يرجع صفوفاً.
PERMISSION_DENIED = محمي بصلاحية لا يملكها التطبيق.
NOT_AVAILABLE = المسار غير متاح في هذه النسخة.
