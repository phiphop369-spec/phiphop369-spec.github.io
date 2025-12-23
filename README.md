<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Red Core - Multi-Function</title>
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        /* กำหนดตัวแปรสำหรับโหมดสี */
        :root {
            --primary-red: #e63946;
            --bg-color: #ffffff;
            --text-color: #1a1a1a;
            --card-bg: #f4f4f4;
            --nav-bg: #1a1a1a;
            --nav-text: #ffffff;
        }

        /* สำหรับ Dark Mode */
        [data-theme="dark"] {
            --bg-color: #121212;
            --text-color: #ffffff;
            --card-bg: #1e1e1e;
            --nav-bg: #000000;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            transition: background-color 0.3s, color 0.3s;
        }

        body {
            font-family: 'Kanit', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
        }

        /* Navigation */
        nav {
            background-color: var(--nav-bg);
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo { color: var(--nav-text); font-weight: 700; font-size: 1.5rem; }
        .logo span { color: var(--primary-red); }

        .controls { display: flex; gap: 10px; align-items: center; }

        button {
            padding: 8px 15px;
            cursor: pointer;
            border-radius: 20px;
            border: 1px solid var(--primary-red);
            background: transparent;
            color: var(--primary-red);
            font-family: 'Kanit', sans-serif;
        }

        button:hover { background: var(--primary-red); color: white; }

        /* Hero Section */
        .hero {
            padding: 100px 20px;
            text-align: center;
            background: linear-gradient(45deg, var(--primary-red), #9b1c24);
            color: white;
        }

        /* Content Area */
        .container {
            padding: 50px 10%;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .card {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        footer {
            text-align: center;
            padding: 40px;
            background: var(--nav-bg);
            color: var(--nav-text);
        }
    </style>
</head>
<body data-theme="light">

    <nav>
        <div class="logo">RED<span>CORE</span></div>
        <div class="controls">
            <button onclick="changeLanguage('th')">TH</button>
            <button onclick="changeLanguage('en')">EN</button>
            <button id="theme-toggle" onclick="toggleTheme()">🌙 Dark Mode</button>
        </div>
    </nav>

    <header class="hero">
        <h1 id="hero-title">ยินดีต้อนรับสู่ Red Core</h1>
        <p id="hero-desc">เลือกโหมดสีและภาษาที่คุณต้องการได้ที่เมนูด้านบน</p>
    </header>

    <main class="container">
        <div class="card">
            <h2 id="card1-title">รวดเร็ว</h2>
            <p id="card1-desc">ประสิทธิภาพการทำงานที่เหนือระดับ</p>
        </div>
        <div class="card">
            <h2 id="card2-title">ปลอดภัย</h2>
            <p id="card2-desc">ปกป้องข้อมูลด้วยระบบล่าสุด</p>
        </div>
    </main>

    <footer>
        <p id="footer-text">&copy; 2025 Red Core Digital Agency. สงวนลิขสิทธิ์</p>
    </footer>

    <script>
        // ข้อมูลภาษา
        const translations = {
            th: {
                heroTitle: "ยินดีต้อนรับสู่ Red Core",
                heroDesc: "เลือกโหมดสีและภาษาที่คุณต้องการได้ที่เมนูด้านบน",
                card1Title: "รวดเร็ว",
                card1Desc: "ประสิทธิภาพการทำงานที่เหนือระดับ",
                card2Title: "ปลอดภัย",
                card2Desc: "ปกป้องข้อมูลด้วยระบบล่าสุด",
                footer: "© 2025 Red Core Digital Agency. สงวนลิขสิทธิ์",
                darkMode: "🌙 โหมดมืด",
                lightMode: "☀️ โหมดสว่าง"
            },
            en: {
                heroTitle: "Welcome to Red Core",
                heroDesc: "Select your preferred language and theme from the menu above",
                card1Title: "Fast",
                card1Desc: "Unmatched performance and speed",
                card2Title: "Secure",
                card2Desc: "Protect your data with the latest systems",
                footer: "© 2025 Red Core Digital Agency. All Rights Reserved.",
                darkMode: "🌙 Dark Mode",
                lightMode: "☀️ Light Mode"
            }
        };

        let currentLang = 'th';

        // ฟังก์ชันเปลี่ยนภาษา
        function changeLanguage(lang) {
            currentLang = lang;
            document.getElementById('hero-title').textContent = translations[lang].heroTitle;
            document.getElementById('hero-desc').textContent = translations[lang].heroDesc;
            document.getElementById('card1-title').textContent = translations[lang].card1Title;
            document.getElementById('card1-desc').textContent = translations[lang].card1Desc;
            document.getElementById('card2-title').textContent = translations[lang].card2Title;
            document.getElementById('card2-desc').textContent = translations[lang].card2Desc;
            document.getElementById('footer-text').textContent = translations[lang].footer;
            updateThemeButtonText();
        }

        // ฟังก์ชันเปลี่ยนโหมด
        function toggleTheme() {
            const body = document.body;
            const currentTheme = body.getAttribute('data-theme');
            const newTheme = currentTheme === 'light' ? 'dark' : 'light';
            body.setAttribute('data-theme', newTheme);
            updateThemeButtonText();
        }

        function updateThemeButtonText() {
            const theme = document.body.getAttribute('data-theme');
            const btn = document.getElementById('theme-toggle');
            btn.textContent = theme === 'light' ? translations[currentLang].darkMode : translations[currentLang].lightMode;
        }
    </script>
</body>
</html>
