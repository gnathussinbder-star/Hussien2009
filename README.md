# Hussein Badr English — Static website upgrade

**من الصفر إلى الطلاقة | From zero to fluency**

This is a vanilla HTML/CSS/ES-module JavaScript bundle intended for the GitHub Pages project site:

`https://gnathussinbder-star.github.io/Hussien2009/`

The source provided with the request contained placeholders for the current HTML/CSS/JS, rather than the actual source files. This ZIP is therefore a complete, self-contained upgrade bundle based on the requirements and the stated brand, not a line-by-line patch against the unavailable original source.

## Arabic — النشر والتعديل

### 1. ارفع الملفات إلى GitHub Pages

1. نزّل ملف ZIP وفك الضغط عنه مع الحفاظ على المجلدات كما هي.
2. افتح مستودع GitHub الذي ينشر `Hussien2009`، ثم ارفع **محتويات** مجلد الحزمة إلى جذر المستودع، بحيث يكون `index.html` في الجذر وليس داخل مجلد إضافي.
3. من **Settings → Pages** اختر فرع النشر الذي تستخدمه (مثل `main`) ومجلد الجذر `/`، ثم احفظ الإعداد.
4. انتظر اكتمال نشر GitHub Pages، ثم افتح `https://gnathussinbder-star.github.io/Hussien2009/` وتحقق من الصفحات والروابط.
5. حدّث `sitemap.xml` وبيانات canonical في الصفحات بعد تغيير أي عنوان أو اسم صفحة.

> **مهم:** يعتمد هذا الإصدار على المسار `/Hussien2009/`. إذا كان اسم مستودع النشر مختلفًا، عدّل `BASE_PATH` في `assets/js/i18n.js` و`assets/js/app.js` حيث يظهر، و`BASE_PATH` في `sw.js`، وروابط القوالب و`manifest.webmanifest` و`robots.txt` و`sitemap.xml` قبل النشر. عند تبديل اسم المستودع يفضّل البحث الشامل عن `/Hussien2009/` واستبداله بالمسار الصحيح.

### 2. اختبار محلي اختياري

يمكن تشغيل مجلد الموقع عبر خادم محلي بدل فتح الملفات بالنقر المباشر، لأن `fetch()` وES modules وService Worker تتطلب سياق HTTP/HTTPS:

```bash
python -m http.server 8000
```

افتح حينها `http://localhost:8000/` من المجلد الذي يحتوي `index.html`. المسارات المُعدة للنشر تبدأ بـ `/Hussien2009/`؛ لذلك قد تحتاج إلى استضافة المجلد محليًا بالمسار نفسه أو تعديل `BASE_PATH` أثناء الاختبار المحلي.

### 3. أماكن تحرير المحتوى

- الأسئلة الأربعون: `assets/data/questions.json`.
- الدروس ومفرداتها وأمثلتها واختباراتها: `assets/data/lessons.json`، إضافة إلى صفحات HTML الثابتة في `lessons/` التي ينبغي تحديثها مع البيانات حتى يبقى المحتوى واضحًا لمحركات البحث دون JavaScript.
- البطاقات: `assets/data/flashcards.json`.
- الأسئلة الشائعة: `assets/data/faq.json` ونسختها الثابتة في `index.html` وبيانات FAQ structured data.
- المسارات: `assets/data/paths.json` و`paths.html`.
- التصميم: `assets/css/main.css`، مع متغيرات الألوان في أول الملف.
- النصوص العامة للترجمة: `assets/js/i18n.js`. زر اللغة يبدّل التنقل والعناصر الموسومة والنصوص الشائعة؛ المحتوى التعليمي الطويل في هذه النسخة يظل عربيًا في بعض الصفحات، مع أمثلة إنجليزية داخل الدروس.
- العنوان الأساسي وخريطة الموقع: ابحث عن `https://gnathussinbder-star.github.io/Hussien2009/` لتحديثها إذا تغيّر النطاق.

### 4. الصوت والخصوصية

- يعتمد النطق الافتراضي على Web Speech API؛ الأصوات المتاحة تختلف حسب المتصفح ونظام التشغيل.
- لا توجد ملفات MP3 مرفقة في الحزمة؛ قيمة `audio` في أسئلة الاستماع هي `null` حاليًا، فيُستخدم TTS كبديل. عند إعداد ملف صوتي، ضعه محليًا داخل المشروع، ثم حدّث حقل `audio` إلى المسار النسبي المناسب واختبره.
- لا يرفع الموقع تسجيلات. مع ذلك، قد تعالج خدمة المتصفح أو مورّد النظام الصوت عند استخدام `SpeechRecognition`؛ راجع سياسة الخصوصية في الموقع وسياسة مزود المتصفح.
- تقدم الدروس وإجابات الاختبار والبطاقات تحفظ محليًا في `localStorage`. يحفظ Service Worker ملفات التطبيق الثابتة في `Cache Storage` ليتيح بعض العمل دون اتصال.
- نموذج التواصل يفتح تطبيق البريد باستخدام `mailto:`؛ لا توجد خدمة إرسال أو اشتراك خلفية حقيقية. النموذج يطبق تحققًا ووقت انتظار محليًا فقط؛ لا يُعدّ ذلك بديلًا عن rate-limiting على خادم.

### 5. رموز PWA

تتضمن الحزمة أيقونتي PNG بحجم 192×192 و512×512 داخل `assets/icons/`. استبدلهما بصورة شعار أصلية عند توفرها، مع إبقاء المقاسات والأسماء أو تحديث `manifest.webmanifest` معها. اختبر «إضافة إلى الشاشة الرئيسية» على Chrome/Android. تحتاج Service Worker إلى HTTPS أو localhost.

### 6. إعدادات الأمان

- يرسل GitHub Pages صفحات ثابتة ولا يسمح لك بضبط ترويسات HTTP الأمنية عبر ملفات المشروع. يوجد CSP عبر `<meta>` كدفاع جزئي، لكنه لا يعوض الترويسات الحقيقية.
- للحصول على ترويسات مثل `Strict-Transport-Security`, `X-Content-Type-Options`, `Permissions-Policy`, `frame-ancestors` وCSP مخصص، ضع CDN/وكيلًا مثل Cloudflare أمام النطاق واضبطها هناك. لا تستخدم `frame-ancestors` داخل meta؛ المتصفحات لا تعتمدها من هذا الموضع.
- لا توجد مكتبات خارجية أو خطوط خارجية أو تحليلات خارجية في هذه الحزمة، لذلك لا توجد موارد CDN تحتاج إلى SRI.
- افحص `https://gnathussinbder-star.github.io/Hussien2009/.well-known/security.txt` بعد النشر. لأن الموقع يعمل على GitHub Pages ضمن مستودع مشروع، يكون المسار تحت `/Hussien2009/` وليس جذر النطاق.

### 7. ما يحتاج إلى إدخال صاحب الموقع

- أي تسجيلات صوتية أصلية باللغة المرغوبة إذا لم ترغب في الاعتماد على TTS.
- نصوص حقيقية لآراء الطلاب مع موافقة واضحة؛ النصوص الحالية معلّمة حرفيًا كمواضع يجب استبدالها.
- شعار أصلي/أيقونات العلامة إذا كانت متوفرة؛ الأيقونات الحالية أحرف HB مولدة محليًا.
- خدمة اشتراك بريد حقيقية إن لزم الأمر؛ لا توجد قائمة بريد حقيقية هنا، فقط mailto. إذا أضيفت خدمة طرف ثالث، وثّقها في الخصوصية والشروط واضبط CSP حسب الحاجة.
- معرف تحليلات فقط إذا قررت استخدام التحليلات وراجعت الموافقة والخصوصية؛ لا يوجد analytics ID في هذه النسخة.
- راجع وصف المدرّس والسيرة الذاتية وأضف مؤهلات موثقة فقط.

## English — deployment and maintenance

### Deploy

1. Unzip this bundle without flattening or losing folders.
2. Upload the **contents** of the bundle to the root of the GitHub repository serving `Hussien2009`; `index.html` must be at repository root.
3. In **Settings → Pages**, select the publishing branch and root folder `/`.
4. Wait for Pages to deploy, then test the homepage and every route under the project path.
5. Keep `sitemap.xml`, canonical URLs, `robots.txt`, the manifest and service-worker scope synchronized if routes or the repository name change.

### Architecture

- No framework, package manager or build step is needed.
- The website uses semantic static HTML, one stylesheet, native ES modules, JSON data files and no third-party runtime libraries.
- Each sample lesson and blog article has a unique URL and pre-rendered Arabic content.
- `assets/js/progress.js` handles validated local progress; `test-engine.js` handles the 40-question placement test; `listening.js`, `speaking.js`, and `srs.js` handle skill practice and card review.
- Export is JSON-only, and reset only clears this site's local progress keys on the current origin.

### Before public launch

Run the manual checklist below on real Android and desktop browsers. Test microphone permissions on HTTPS, use keyboard-only navigation, inspect the browser console and network tab, validate JSON/XML, verify metadata against the live URL, and test offline reloads after a first successful visit. Lighthouse/Core Web Vitals should be measured in a deployed environment; the targets are goals, not claimed test results.

## Deployment checklist

- [ ] ZIP extracted and all files retained.
- [ ] `index.html` uploaded to repository root.
- [ ] GitHub Pages source configured.
- [ ] Canonical URLs and `/Hussien2009/` base path verified.
- [ ] All links, lesson next/previous links, and social links opened and checked.
- [ ] `sitemap.xml`, `robots.txt`, and `.well-known/security.txt` resolve.
- [ ] PWA install and offline fallback tested on HTTPS.
- [ ] Site title, description, JSON-LD, and sharing cards checked with validators.
- [ ] Real student feedback only added with permission; placeholder text removed or retained as placeholders.
- [ ] Privacy/terms checked after any third-party integration.

## Manual test checklist

- [ ] 360px phone, 768px tablet, 1280px desktop: no horizontal page overflow.
- [ ] Language button toggles shared navigation and translated elements; theme persists after refresh.
- [ ] Keyboard: skip link, navigation, answers, quizzes, share buttons and dialogs are operable; focus is visible.
- [ ] Placement test: all 40 questions, back/next, keyboard arrows, reload resume, retake, review, weighted skill results and adaptive minimum-20 stop behavior.
- [ ] Listening: each item plays at most twice, A1/A2 speed control only, fallback when TTS is unavailable.
- [ ] Speaking: permission granted/denied, speech-recognition supported/unsupported, fallback recorder playback, rubric, and no network upload of recorded blobs.
- [ ] Lessons: audio play buttons, 5-question quiz, explanation, mark-complete button and next lesson route.
- [ ] Flashcards: reveal, known/missed scheduling, due queue, refresh persistence and empty-due message.
- [ ] Dashboard: streak, lesson count, chart, badges, export JSON parse, reset data confirmation.
- [ ] Share card PNG downloads; WhatsApp/Telegram/X and copy link work where supported.
- [ ] Contact: required fields, malformed email, honeypot, 60-second local rate limit, mailto fallback and query-prefilled question report.
- [ ] PWA: manifest icons, install prompt, service-worker activation, cache cleanup, and offline fallback.
- [ ] Privacy notice: no cookies or analytics; explain localStorage, Cache Storage and browser vendor speech processing.
- [ ] Browser matrix: current Chrome/Android, Edge/Windows, Firefox/desktop, Safari/iOS where available. Speech recognition is not expected to be available in every browser.

## Known limitations — stated plainly

- This environment could not retrieve the current live pages for source-level comparison; the bundle is based on the provided specifications and the listed current weaknesses.
- The EN toggle translates shared navigation, marked content, and common interface labels; some longer Arabic instructional paragraphs remain Arabic-first in this version.
- CEFR results use a compact weighted score and are an educational estimate, not a validated psychometric test.
- Speaking scores are approximations based on word overlap/length or self-assessment; they do not reliably assess pronunciation, intelligibility or spontaneous fluency.
- TTS voice availability depends on the browser/OS. No real MP3 recordings are included.
- Adaptive selection is a lightweight rule-based adjustment, not a professionally calibrated computerized adaptive test.
- GitHub Pages does not provide a backend, secure server-side contact throttling, account sync, central progress storage or real email subscription.
- CSP delivered via meta does not replace server response headers. Use a CDN such as Cloudflare in front of the domain if you need enforceable HTTP security headers.
- Core Web Vitals and cross-browser behavior must be measured on the deployed site. The target thresholds are not claimed as already benchmarked.
