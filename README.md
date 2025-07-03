<!-- ==============================================
  جو باص سودان | Go Bus Sudan — نسخة طبق الأصل من GoBus
  ----------------------------------------------
  الهيكل الكامل للمشروع (Front-end + Back-end)
  الملفات التالية مرتبة بالتسلسل، انسخ كل ملف في مساره الصحيح.
================================================ --><!-- =================================================
1) index.html — الصفحة الرئيسية
================================================ --><!DOCTYPE html><html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>جو باص سودان | Go Bus Sudan</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>
  <header>
    <div class="logo"><h1 id="logo-text">جو باص سودان</h1></div>
    <nav>
      <ul>
        <li><a href="index.html" id="nav-home">الرئيسية</a></li>
        <li><a href="dashboard.html" id="nav-dashboard">لوحة المستخدم</a></li>
        <li><a href="login.html" id="nav-login">تسجيل الدخول</a></li>
        <li><a href="#" onclick="switchLang(); return false;">EN</a></li>
      </ul>
    </nav>
  </header>  <main class="container search-form">
    <h2 id="search-title">ابحث عن رحلتك</h2>
    <form id="searchForm">
      <label for="from" id="from-label">من</label>
      <input list="cities" id="from" name="from" required>
      <label for="to" id="to-label">إلى</label>
      <input list="cities" id="to" name="to" required>
      <datalist id="cities">
        <option value="الخرطوم">
        <option value="مدني">
        <option value="بورتسودان">
      </datalist>
      <label for="date" id="date-label">تاريخ الرحلة</label>
      <input type="date" id="date" name="date" required>
      <button type="submit" id="search-button">ابحث</button>
    </form>
  </main>  <footer>&copy; 2025 جو باص سودان</footer>
  <script src="js/lang.js"></script>
  <script src="js/main.js"></script>
</body>
</html><!-- =================================================
2) search.html — صفحة نتائج الرحلات
================================================ --><!DOCTYPE html><html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>نتائج الرحلات | جو باص سودان</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>
  <header><h1 id="results-title">نتائج البحث</h1></header>
  <main class="container" id="results"></main>
  <footer>&copy; 2025 جو باص سودان</footer>
  <script src="js/lang.js"></script>
  <script src="js/main.js"></script>
  <script>
    // تحميل النتائج من السيرفر
    window.onload = async () => {
      const url = new URL(window.location.href);
      const params = url.searchParams;
      const resp = await fetch(`/api/trips?from=${params.get('from')}&to=${params.get('to')}&date=${params.get('date')}`);
      const trips = await resp.json();
      renderTrips(trips);
    };
  </script>
</body>
</html><!-- =================================================
3) seat-selection.html — اختيار الكرسي
================================================ --><!DOCTYPE html><html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>اختيار الكرسي |
