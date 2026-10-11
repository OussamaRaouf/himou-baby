# Himou Baby — Projet complet PWA

Version de livraison : 5 — octobre 2026  
Interface : français / العربية  
Type : application web installable (PWA)

## Fichiers du projet

- `index.html` : application complète et interface bilingue.
- `manifest.webmanifest` : nom, icônes et paramètres d’installation.
- `sw.js` : mise en cache de l’interface et ouverture de secours hors connexion.
- `icons/icon-192.png`, `icons/icon-512.png` : icônes de l’application à partir du logo Himou Baby.
- `icons/logo.jpg` : fichier image du logo fourni.

## Fonctionnalités incluses

- Vente au comptoir, panier, remises et deux actions d’encaissement.
- Scan de code-barres avec la caméra du téléphone, avec saisie manuelle de secours.
- Gestion des produits, codes-barres, catégories et quantités.
- Suggestions de noms similaires pendant la saisie d’un produit.
- Import/export de produits Excel (`.xlsx`, `.xls`) et CSV.
- Fusion des quantités quand un produit correspondant existe déjà, en évitant les conflits de code-barres.
- Filtres dans Produits, Stock et Rapports, avec remise à zéro des filtres.
- Impression des articles affichés dans l’état du stock.
- Gestion des vendeurs et classement mensuel selon les ventes enregistrées.
- Sauvegarde et restauration d’une base locale au format JSON.
- Section professionnelle « À propos du développeur » dans Paramètres avec le logo, Raouf Betaimi, téléphone 0698833744 et adresse Laghouat, Algérie.
- Interface en français et en arabe.

## Publier gratuitement avec GitHub Pages

### A. Préparer le dépôt

1. Décompressez `HimouBabyPWA_Complete.zip` sur votre ordinateur.
2. Connectez-vous à GitHub et créez un dépôt public nommé `himou-baby` (ou un autre nom).
3. Ouvrez le dépôt, choisissez **Add file → Upload files** et téléversez les fichiers qui sont à l’intérieur du dossier `HimouBabyPWA_Complete` — pas le dossier parent en tant que sous-dossier : `index.html`, `manifest.webmanifest`, `sw.js` et le dossier `icons`.
4. Validez avec **Commit changes**.

### B. Activer GitHub Pages

1. Dans le dépôt, ouvrez **Settings → Pages**.
2. Sous **Build and deployment**, choisissez **Deploy from a branch**.
3. Choisissez la branche `main` et le dossier `/(root)`, puis cliquez sur **Save**.
4. Attendez la fin du déploiement affiché dans GitHub Pages.
5. L’adresse sera semblable à `https://VOTRE-NOM.github.io/himou-baby/`. Le nom de compte et de dépôt dans l’adresse dépend de votre configuration.

### C. Installer sur Android

1. Ouvrez l’adresse HTTPS publiée dans **Google Chrome** sur le téléphone.
2. Autorisez l’accès à la caméra lorsque vous lancez le scanner.
3. Ouvrez le menu `⋮` et choisissez **Installer l’application** ou **Ajouter à l’écran d’accueil**.
4. Lancez Himou Baby depuis la nouvelle icône.
5. Testez d’abord avec quelques produits et une vente de démonstration.

### D. Mettre à jour plus tard

1. Exportez d’abord une sauvegarde JSON depuis Himou Baby et conservez-la ailleurs.
2. Envoyez les nouveaux fichiers dans le même dépôt GitHub en remplaçant les fichiers existants.
3. Dans `sw.js`, changez `CACHE_NAME` (par exemple, `himou-baby-pwa-v6-AAAA-MM-JJ`) avant de publier une nouvelle version ; cela force le navigateur à créer un nouveau cache.
4. Après le déploiement, rouvrez le site. Si l’ancienne interface est encore affichée, fermez l’application puis relancez-la, ou actualisez le site dans Chrome.

## Scanner de codes-barres et dépendances Internet

- L’accès caméra nécessite une origine sécurisée HTTPS (ou localhost) et l’autorisation du navigateur.
- L’application utilise d’abord `BarcodeDetector` lorsqu’il est disponible et tente ZXing Browser en remplacement. La bibliothèque ZXing est chargée depuis un CDN ; dans un navigateur sans `BarcodeDetector`, une connexion Internet peut donc être nécessaire pour le scan.
- Les fonctions d’import/export Excel chargent également SheetJS depuis un CDN, donc l’import/export Excel nécessite une connexion Internet au moment où la bibliothèque n’est pas déjà chargée.
- Si le scan échoue : autorisez la caméra dans les paramètres Android → Applications → Chrome → Autorisations → Appareil photo ; réessayez avec un code bien éclairé ou saisissez le code manuellement.

## Données : points importants

- Les produits, vendeurs, ventes et réglages sont stockés dans le stockage local du navigateur (`localStorage`) de cet appareil et de cette adresse web.
- Le service worker met en cache les fichiers de l’interface ; il ne synchronise pas les ventes ni les produits avec un serveur.
- Les données ne sont pas partagées entre plusieurs téléphones ou vendeurs. Une version multi-utilisateurs nécessiterait un serveur et une base de données centralisée.
- Avant d’effacer les données du navigateur, changer de téléphone ou publier une mise à jour, exportez une sauvegarde JSON. Testez la restauration dans un premier temps avec une copie de sauvegarde.
- Le projet n’a pas été compilé ou testé sur votre téléphone physique dans le cadre de cette livraison. Vérifiez les ventes, le scan, l’impression et les imports avec des données de test avant une utilisation commerciale quotidienne.

---

# هيمو بيبي — مشروع PWA الكامل

الإصدار: 5 — أكتوبر 2026  
الواجهة: الفرنسية والعربية  
النوع: تطبيق ويب قابل للتثبيت (PWA)

## ملفات المشروع

- `index.html`: التطبيق والواجهة باللغتين.
- `manifest.webmanifest`: اسم التطبيق وأيقوناته وإعدادات التثبيت.
- `sw.js`: تخزين ملفات الواجهة مؤقتًا للمساعدة على فتحها دون اتصال.
- `icons/icon-192.png` و`icons/icon-512.png`: أيقونات التطبيق باستخدام شعار هيمو بيبي.
- `icons/logo.jpg`: ملف الشعار.

## الوظائف المتوفرة

- البيع عند الصندوق والسلة والتخفيضات وخيارا الدفع.
- قراءة الباركود بكاميرا الهاتف مع إمكانية إدخال الرمز يدويًا.
- إدارة المنتجات والرموز والفئات والكميات.
- اقتراح أسماء المنتجات المشابهة أثناء الكتابة.
- استيراد وتصدير المنتجات إلى Excel وCSV.
- جمع الكميات عند إضافة منتج مطابق مع تجنب تعارض الرموز الشريطية.
- فلاتر في المنتجات والمخزون والتقارير مع إمكانية مسح الفلاتر.
- طباعة المنتجات المعروضة في حالة المخزون.
- إدارة البائعين وترتيب بائع الشهر حسب المبيعات المسجلة.
- تصدير واستيراد نسخة احتياطية JSON.
- قسم «حول المطور» في الإعدادات مع الشعار واسم Raouf Betaimi ورقم الهاتف 0698833744 والعنوان الأغواط، الجزائر.
- واجهة بالفرنسية والعربية.

## النشر المجاني عبر GitHub Pages

1. فك ضغط `HimouBabyPWA_Complete.zip` على الكمبيوتر.
2. أنشئ مستودعًا عامًا في GitHub باسم `himou-baby` مثلًا.
3. ارفع محتويات المجلد إلى جذر المستودع: `index.html` و`manifest.webmanifest` و`sw.js` ومجلد `icons`، ثم احفظ التغييرات عبر **Commit changes**.
4. افتح **Settings → Pages**.
5. اختر **Deploy from a branch**، ثم الفرع `main` والمجلد `/(root)`، ثم **Save**.
6. انتظر اكتمال النشر وافتح الرابط الذي يظهر، ويكون شبيهًا بـ `https://اسمك.github.io/himou-baby/`.
7. افتح الرابط في Chrome على الهاتف، واسمح باستخدام الكاميرا.
8. من القائمة `⋮` اختر **تثبيت التطبيق** أو **إضافة إلى الشاشة الرئيسية**.

## تحديث التطبيق

1. صدّر نسخة احتياطية JSON واحفظها في مكان آمن.
2. استبدل الملفات القديمة بالملفات الجديدة داخل مستودع GitHub نفسه.
3. غيّر قيمة `CACHE_NAME` في `sw.js` إلى إصدار جديد قبل النشر.
4. بعد اكتمال النشر أعد فتح التطبيق. إذا ظهرت النسخة القديمة، أغلق التطبيق وافتحه أو حدّث الصفحة في Chrome.

## الكاميرا والإنترنت

- يجب فتح التطبيق عبر HTTPS مع السماح للمتصفح باستخدام الكاميرا.
- يستخدم التطبيق `BarcodeDetector` عند توفره، ويحاول استخدام مكتبة ZXing بديلًا. يتم تحميل ZXing من الإنترنت؛ وقد يحتاج المسح إلى اتصال إنترنت في المتصفحات التي لا تدعم `BarcodeDetector`.
- استيراد وتصدير Excel يستخدم مكتبة SheetJS من CDN وقد يحتاج إلى اتصال إنترنت.
- عند فشل الكاميرا: افتح إعدادات الهاتف ← التطبيقات ← Chrome ← الأذونات ← الكاميرا، ثم أعد المحاولة أو أدخل الرمز يدويًا.

## حفظ البيانات

- تُحفظ المنتجات والمبيعات والبائعون والإعدادات محليًا في المتصفح وعلى هذا الجهاز فقط.
- تخزين ملفات الواجهة مؤقتًا لا يعني مزامنة البيانات مع الخادم.
- لا توجد مزامنة بين عدة هواتف. يلزم خادم وقاعدة بيانات مركزية لإضافة هذه الخاصية.
- صدّر نسخة JSON قبل حذف بيانات المتصفح أو تغيير الهاتف أو تحديث التطبيق. اختبر الاستعادة باستخدام نسخة احتياطية أولًا.
- لم يتم اختبار هذا المشروع على هاتفك الفعلي ضمن هذه التسليم؛ اختبر الكاميرا والطباعة والمبيعات والاستيراد ببيانات تجريبية قبل الاعتماد اليومي عليه.
