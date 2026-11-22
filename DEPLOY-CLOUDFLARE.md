# نشر الموقع على Cloudflare Workers

سبب ظهور 404 ليس نقص صفحات الموقع: روابط مثل `pages/projects.html` موجودة، والملف `pages/projects.html` موجود داخل المشروع. النشر الحالي على `workers.dev` لا يقدّم ملفات الموقع الثابتة من مجلد المشروع.

أُضيف ملف `wrangler.jsonc` لتهيئة Cloudflare Workers Static Assets بحيث تُرفع ملفات الموقع كاملة.

## خطوات النشر

1. فك ضغط الأرشيف المعدّل.
2. افتح Terminal داخل المجلد الرئيسي للموقع، حيث يوجد `wrangler.jsonc`.
3. سجّل الدخول إلى Cloudflare إذا لم تكن مسجّلًا: `npx wrangler login`.
4. انشر الموقع: `npx wrangler deploy`.
5. بعد اكتمال النشر، اختبر الصفحة الرئيسية ثم مباشرةً:
   - `/pages/projects.html`
   - `/pages/about.html`
   - `/pages/projects/engilina.html`

يجب أن يحتوي النشر على المجلدات `pages/` و`assets/` و`css/` و`js/` كاملة، وليس ملف `index.html` وحده. إذا كنت تنشر من لوحة Cloudflare بدل Wrangler، اختر إعداد Static Assets وحدد جذر المشروع كمجلد الملفات.

لا تحذف `pages/` ولا تغيّر الروابط؛ كلاهما موجودان بالفعل في الأرشيف. بعد إعادة نشر كل الملفات، جرّب تحديث الصفحة أو فتحها في نافذة خاصة لتجاوز أي نتيجة 404 قديمة مخزنة.
