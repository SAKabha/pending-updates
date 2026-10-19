# PENDING — خدمة التحقق من التحديث

هذا المستودع يحتوي فقط على ملف سياسة التحديث للعبة «قيد الانتظار» (PENDING).
لا يحتوي على اللعبة ولا ملفاتها ولا ملفات الحفظ.

اللعبة تقرأ `manifest.json` من هنا عبر HTTPS عند كل تشغيل، وتمنع اللعب إذا فشل
الاتصال أو كان رقم نسخة اللاعب أقل من `minimum_build`.

## الحقول

| الحقل | المعنى |
|---|---|
| `minimum_build` | أقدم رقم نسخة مسموح له باللعب. أي نسخة أقدم تُمنع. |
| `latest_build` | رقم أحدث نسخة وزّعتها (لازم يكون ≥ `minimum_build`). |
| `latest_version` | اسم النسخة للعرض فقط، مثل `0.9.20261019.1`. |
| `download_url` | فارغ: الملف يُرسل للاعبين مباشرة. |
| `schema`, `product`, `channel` | لا تغيّرها. |

## عند جاهزية نسخة جديدة

1. ابنِ النسخة الجديدة برقم build أعلى (مثلًا 2) وجرّبها، واحتفظ بالنسخة السابقة احتياطًا.
2. أرسل النسخة الجديدة لأصحابك أولًا.
3. افتح `manifest.json` هنا واضغط ✏️ (Edit)، وغيّر:
   - `"minimum_build": 2` ← هذا هو الذي يجبر النسخ القديمة على التحديث
   - `"latest_build": 2`
   - `"latest_version": "0.9.YYYYMMDD.2"`
4. اضغط **Commit changes**. خلال دقيقة إلى عدة دقائق يصبح الملف الجديد فعّالًا.
5. تأكد: افتح رابط `manifest.json` في المتصفح وشاهد الأرقام الجديدة.

ملاحظات:
- رفع `latest_build` وحده لا يمنع النسخ القديمة؛ رفع `minimum_build` هو الذي يمنعها.
- للتراجع عن خطأ: أعد الأرقام السابقة في `manifest.json`.
- لا تحذف هذا المستودع ولا توقف GitHub Pages: إذا تعطّل الرابط، لن تعمل اللعبة عند أحد.

---

**English:** update policy for PENDING. To require a new build N: set `minimum_build` and
`latest_build` to N, update `latest_version`, commit. Raising only `latest_build` does
not block older builds. Keep this repository and its Pages site online — the game
refuses to start when the check fails.
