# حزمة تحديث Hussein Badr English

## الملفات وأين تضعها
ارفع كل الملفات التالية إلى **جذر المشروع** (بجانب index.html):
- `skills-test.html` اختبار الاستماع والتحدث (جديد)
- `privacy.html` و`terms.html` و`404.html`
- `sitemap.xml` و`robots.txt`
- `manifest.webmanifest` و`sw.js`

## الملفات التي تعدّلها بنفسك
1. `snippets/social-channels-section.html`: استبدل به قسم يوتيوب في index.html (id="youtube").
2. `snippets/head-seo.html`: انسخ ما فيه إلى <head> وقبل </body> في index.html. جرّب الموقع بعد إضافة سطر CSP.
3. في index.html وplacement-test.html:
   - أضف رابط "اختبار الاستماع والتحدث" في القائمة والقسم، يشير إلى `skills-test.html`.
   - غيّر العبارة "لا يقيس التحدث والاستماع" إلى: "للاستماع والتحدث جرّب اختبار المهارات".
   - أضف في الفوتر روابط الخصوصية والشروط.
4. أرسل `sitemap.xml` في Google Search Console بعد الرفع.

## ملاحظات
- الحزمة إضافية ولا تستبدل ملفاتك الأصلية، لأني لم أطّلع على كودها المصدري.
- أيقونة PWA تستخدم صورتك الحالية؛ لتثبيت كامل أضف أيقونتي PNG بحجم 192 و512.
- تقييم التحدث يعمل على Chrome/Edge، وغيرهما يستخدم تقييمًا ذاتيًا.
- مدة الصوت والنطق تعتمد على أصوات جهاز المستخدم (speechSynthesis).
