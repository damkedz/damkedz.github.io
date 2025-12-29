<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Cinematic Portfolio</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=Inter:wght@400;600&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            --db-red: #FF3621;
            --ai-purple: #9D28AC;
            --copilot-orange: #f78c6c; /* Kolor Copilota */
            --azure-blue: #0078D4;
            --bg-black: #000000;
            --glass: rgba(255, 255, 255, 0.05);
            --border: rgba(255, 255, 255, 0.15);
            --text-main: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-black);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
        }

        /* --- WIDEO TŁO --- */
        .video-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            z-index: -2;
            overflow: hidden;
        }
        
        .video-container video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.4; /* Przyciemnienie wideo */
        }

        .overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at center, transparent 0%, #000 90%);
            z-index: -1;
        }

        /* --- NAV --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 5%;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            background: linear-gradient(180deg, rgba(0,0,0,0.8) 0%, transparent 100%);
        }
        .logo { font-family: 'Space Grotesk', sans-serif; font-weight: 700; font-size: 1.5rem; letter-spacing: -1px; }
        
        /* --- HERO --- */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        h1 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 6rem;
            line-height: 0.9;
            font-weight: 700;
            text-transform: uppercase;
            mix-blend-mode: overlay; /* Efekt przenikania z wideo */
            color: #fff;
            margin-bottom: 20px;
        }
        
        .role-badge {
            border: 1px solid var(--db-red);
            background: rgba(255, 54, 33, 0.1);
            color: #fff;
            padding: 10px 25px;
            border-radius: 50px;
            text-transform: uppercase;
            letter-spacing: 3px;
            font-weight: 600;
            font-size: 0.9rem;
            margin-bottom: 20px;
            box-shadow: 0 0 30px rgba(255, 54, 33, 0.3);
            backdrop-filter: blur(5px);
        }

        /* --- INFINITE MARQUEE (Ruchomy pasek) --- */
        .marquee-container {
            background: rgba(0,0,0,0.8);
            border-top: 1px solid var(--border);
            border-bottom: 1px solid var(--border);
            padding: 20px 0;
            overflow: hidden;
            white-space: nowrap;
            position: relative;
        }
        
        .marquee-content {
            display: inline-block;
            animation: marquee 20s linear infinite;
        }
        
        .tech-item {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin: 0 30px;
            color: #888;
            font-weight: 600;
            font-family: 'Space Grotesk';
            font-size: 1.2rem;
        }
        .tech-item i { color: var(--db-red); }

        @keyframes marquee { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

        /* --- SECTIONS --- */
        section { padding: 100px 8%; position: relative; background: rgba(0,0,0,0.7); /* Przyciemnienie sekcji treści */ backdrop-filter: blur(10px); }
        .section-title { font-family: 'Space Grotesk'; font-size: 3rem; margin-bottom: 50px; }
        .section-title span { color: var(--db-red); }

        /* --- GRIDY --- */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .card {
            background: var(--glass);
            border: 1px solid var(--border);
            padding: 40px;
            border-radius: 20px;
            transition: 0.4s;
            position: relative;
            overflow: hidden;
        }
        .card:hover { border-color: var(--db-red); transform: translateY(-10px); background: rgba(255,255,255,0.08); }
        
        /* Video Reveal Effect on Card Hover (Symulacja) */
        .card::before {
            content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 5px;
            background: var(--db-red); transform: scaleX(0); transform-origin: left; transition: 0.4s;
        }
        .card:hover::before { transform: scaleX(1); }

        .card h3 { font-size: 1.8rem; margin: 20px 0 10px 0; font-family: 'Space Grotesk'; }
        .card p { color: #aaa; line-height: 1.6; }
        .icon-box { font-size: 3rem; margin-bottom: 10px; }

        /* COPILOT & AI STYLE */
        .ai-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 30px;
            margin-bottom: 30px;
        }
        @media (max-width: 768px) { .ai-grid { grid-template-columns: 1fr; } h1 { font-size: 3.5rem; } }

        .card.copilot { border-color: var(--copilot-orange); }
        .card.copilot:hover::before { background: var(--copilot-orange); }
        .card.copilot .icon-box { color: var(--copilot-orange); }
        
        .card.genai { border-color: var(--ai-purple); }
        .card.genai:hover::before { background: var(--ai-purple); }
        .card.genai .icon-box { color: var(--ai-purple); }


        /* --- LISTA MICROSOFT --- */
        .ms-list {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
        }
        .ms-badge {
            background: rgba(0, 120, 212, 0.1);
            border: 1px solid rgba(0, 120, 212, 0.3);
            color: #fff;
            padding: 10px 20px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: 0.3s;
        }
        .ms-badge:hover { background: var(--azure-blue); transform: scale(1.05); }

        /* --- TIMELINE --- */
        .job {
            border-left: 1px solid #333;
            padding-left: 30px;
            margin-bottom: 40px;
            position: relative;
        }
        .job::after {
            content: ''; position: absolute; left: -5px; top: 0; width: 9px; height: 9px; background: var(--db-red); border-radius: 50%;
        }
        .job-title { font-size: 1.5rem; font-weight: 700; color: #fff; }
        .job-company { color: var(--db-red); font-weight: bold; margin-bottom: 10px; display: block; }

        /* --- FOOTER --- */
        footer { padding: 60px 0; text-align: center; background: #000; }
        .contact-link { color: #fff; font-size: 1.5rem; text-decoration: none; border-bottom: 1px solid var(--db-red); padding-bottom: 5px; }

    </style>
</head>
<body>

    <div class="video-container">
        <video autoplay muted loop playsinline poster="https://images.pexels.com/photos/17483873/pexels-photo-17483873.jpeg">
            <source src="https://videos.pexels.com/video-files/3129671/3129671-hd_1920_1080_30fps.mp4" type="video/mp4">
        </video>
    </div>
    <div class="overlay"></div>

    <nav>
        <div class="logo">DAMIAN <span>KĘDZIERSKI</span></div>
        <div style="font-size: 1.5rem;">
            <a href="https://linkedin.com" target="_blank" style="color:white;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </nav>

    <section class="hero" style="background: transparent; backdrop-filter: none;">
        <div class="role-badge" data-aos="fade-down">Senior Profile</div>
        <h1 data-aos="zoom-in" data-aos-duration="1500">
            DATA<br>ENGINEER
        </h1>
        <div id="typewriter" style="font-family: 'Space Grotesk'; font-size: 1.5rem; color: #ccc;"></div>
    </section>

    <div class="marquee-container">
        <div class="marquee-content">
            <span class="tech-item"><i class="fa-solid fa-fire"></i> Apache Spark</span>
            <span class="tech-item"><i class="fa-solid fa-layer-group"></i> Databricks</span>
            <span class="tech-item"><i class="fa-brands fa-python"></i> Python</span>
            <span class="tech-item"><i class="fa-brands fa-microsoft"></i> Azure Fabric</span>
            <span class="tech-item"><i class="fa-solid fa-database"></i> Delta Lake</span>
            <span class="tech-item"><i class="fa-solid fa-robot"></i> Generative AI</span>
            <span class="tech-item"><i class="fa-brands fa-github"></i> Copilot</span>
            <span class="tech-item"><i class="fa-solid fa-code"></i> SQL</span>
            <span class="tech-item"><i class="fa-solid fa-fire"></i> Apache Spark</span>
            <span class="tech-item"><i class="fa-solid fa-layer-group"></i> Databricks</span>
            <span class="tech-item"><i class="fa-brands fa-python"></i> Python</span>
            <span class="tech-item"><i class="fa-brands fa-microsoft"></i> Azure Fabric</span>
            <span class="tech-item"><i class="fa-solid fa-database"></i> Delta Lake</span>
            <span class="tech-item"><i class="fa-solid fa-robot"></i> Generative AI</span>
            <span class="tech-item"><i class="fa-brands fa-github"></i> Copilot</span>
            <span class="tech-item"><i class="fa-solid fa-code"></i> SQL</span>
        </div>
    </div>

    <section id="certifications">
        <h2 class="section-title" data-aos="fade-right">Elite <span>Certifications</span></h2>
        
        <div class="card" data-tilt data-aos="fade-up" style="margin-bottom: 30px; border-color: var(--db-red);">
            <div class="icon-box" style="color: var(--db-red);"><i class="fa-solid fa-medal"></i></div>
            <span style="text-transform: uppercase; letter-spacing: 2px; font-size: 0.8rem; color: #888;">The Gold Standard</span>
            <h3>Databricks Certified Professional</h3>
            <p>Ekspercka wiedza z zakresu inżynierii danych. Optymalizacja wydajności Spark, zaawansowane modelowanie Delta Lake i produkcyjne wdrożenia CI/CD.</p>
        </div>

        <div class="ai-grid">
            <div class="card genai" data-tilt data-aos="fade-up" data-aos-delay="100">
                <div class="icon-box"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                <h3>Gen AI Associate</h3>
                <p>Budowa aplikacji LLM, RAG i obsługa Vector Search w ekosystemie Databricks.</p>
            </div>

            <div class="card copilot" data-tilt data-aos="fade-up" data-aos-delay="200">
                <div class="icon-box"><i class="fa-brands fa-github"></i></div>
                <h3>GitHub Copilot</h3>
                <p><strong>Certyfikat GH-300</strong>. Zaawansowane wykorzystanie AI w procesie wytwarzania oprogramowania (AI-Pair Programming).</p>
            </div>
        </div>

        <div class="grid-3">
            <div class="card" data-tilt data-aos="fade-up">
                <div class="icon-box" style="color: #e65100;"><i class="fa-solid fa-fire"></i></div>
                <h3>Apache Spark Dev</h3>
                <p>Głębokie zrozumienie silnika Spark i optymalizacji zapytań.</p>
            </div>
            
            <div class="card" data-tilt data-aos="fade-up" data-aos-delay="100">
                <div class="icon-box" style="color: var(--azure-blue);"><i class="fa-brands fa-microsoft"></i></div>
                <h3>Fabric Analytics (DP-600)</h3>
                <p>Kompleksowa analityka w najnowszym rozwiązaniu Microsoftu.</p>
            </div>

            <div class="card" data-tilt data-aos="fade-up" data-aos-delay="200">
                <div class="icon-box" style="color: #E84393;"><i class="fa-solid fa-brain"></i></div>
                <h3>Azure AI (AI-102)</h3>
                <p>Inżynieria rozwiązań sztucznej inteligencji w chmurze.</p>
            </div>
        </div>
    </section>

    <section>
        <h2 class="section-title" data-aos="fade-right">Specialist <span>Stack</span></h2>
        <p style="color: #888; margin-bottom: 30px;">Dodatkowe certyfikaty potwierdzające szeroką wiedzę w ekosystemie Microsoft.</p>
        
        <div class="ms-list">
            <div class="ms-badge"><i class="fa-solid fa-database"></i> DP-300 Azure DB Admin</div>
            <div class="ms-badge"><i class="fa-solid fa-globe"></i> DP-420 Cosmos DB</div>
            <div class="ms-badge"><i class="fa-solid fa-chart-pie"></i> PL-300 Power BI</div>
            <div class="ms-badge"><i class="fa-solid fa-server"></i> DP-203 / DP-700</div>
            <div class="ms-badge" style="border-color: #666;"><i class="fa-brands fa-microsoft"></i> AZ-900 / DP-900 / AI-900</div>
            <div class="ms-badge" style="border-color: #f78c6c;"><i class="fa-brands fa-github"></i> GH-900 Foundations</div>
        </div>
    </section>

    <section>
        <h2 class="section-title" data-aos="fade-right">Time<span>line</span></h2>
        
        <div class="job" data-aos="fade-left">
            <div class="job-title">Data Engineer</div>
            <span class="job-company">EY (Ernst & Young) | 10.2024 - Obecnie</span>
            <p style="color: #aaa;">Rozwój architektury Lakehouse, Databricks Unity Catalog oraz mentoring w zakresie Gen AI.</p>
        </div>

        <div class="job" data-aos="fade-left" data-aos-delay="100">
            <div class="job-title">Data Engineer Intern</div>
            <span class="job-company">Sii Poland | 02.2024 - 10.2024</span>
            <p style="color: #aaa;">Migracje danych, budowa pipeline'ów w Azure Data Factory.</p>
        </div>

        <div class="job" data-aos="fade-left" data-aos-delay="200">
            <div class="job-title">Junior BI Specialist</div>
            <span class="job-company">Micro Solutions | 08.2022 - 06.2023</span>
            <p style="color: #aaa;">Raportowanie Power BI i analiza danych biznesowych.</p>
        </div>
    </section>

    <footer>
        <h2 style="font-family: 'Space Grotesk'; margin-bottom: 30px; color: #fff;">Let's Code the Future.</h2>
        <a href="mailto:Damian.kedzierski@op.pl" class="contact-link">Damian.kedzierski@op.pl</a>
        <p style="margin-top: 30px; color: #666;">+48 533 864 722</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://unpkg.com/typewriter-effect@latest/dist/core.js"></script>

    <script>
        AOS.init();

        new Typewriter('#typewriter', {
            strings: ['Databricks Professional', 'GitHub Copilot Expert', 'Azure Architect', 'Gen AI Enthusiast'],
            autoStart: true,
            loop: true,
        });
    </script>
</body>
</html>
