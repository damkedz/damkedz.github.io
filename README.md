<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Data & AI Engineer</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;500;800&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            /* PALETA KOLORÓW */
            --db-red: #FF3621;        /* Databricks Engineering */
            --ai-purple: #D900FF;     /* Generative AI Focus */
            --ms-blue: #00A3E0;       /* Microsoft Azure */
            --bg-dark: #030305;       /* Deepest Black */
            --glass-bg: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.1);
            --text-main: #ffffff;
            --text-muted: #94a3b8;
        }

        * { box-sizing: border-box; }

        body {
            margin: 0;
            background-color: var(--bg-dark);
            color: var(--text-main);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* TŁO NEURALNE */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at 50% 10%, #150020 0%, var(--bg-dark) 80%);
        }

        /* --- NAWIGACJA --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 5%;
            background: rgba(3, 3, 5, 0.8);
            backdrop-filter: blur(15px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid var(--border);
        }
        .logo { font-family: 'JetBrains Mono', monospace; font-weight: 700; font-size: 1.3rem; letter-spacing: -1px; }
        .logo span { color: var(--db-red); }
        .logo .ai { color: var(--ai-purple); }

        .nav-links a { margin-left: 25px; color: var(--text-muted); text-decoration: none; transition: 0.3s; font-weight: 500; font-size: 0.9rem; text-transform: uppercase; letter-spacing: 1px;}
        .nav-links a:hover { color: #fff; text-shadow: 0 0 10px rgba(255,255,255,0.5); }

        /* --- HERO SECTION --- */
        .hero {
            min-height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            position: relative;
        }

        .status-badge {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--ai-purple);
            color: var(--ai-purple);
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 30px;
            box-shadow: 0 0 20px rgba(217, 0, 255, 0.2);
            animation: pulse 2s infinite;
        }

        @keyframes pulse { 0% { box-shadow: 0 0 0 0 rgba(217, 0, 255, 0.4); } 70% { box-shadow: 0 0 0 10px rgba(217, 0, 255, 0); } 100% { box-shadow: 0 0 0 0 rgba(217, 0, 255, 0); } }

        h1 {
            font-size: 5rem;
            font-weight: 800;
            line-height: 1;
            margin: 0;
            letter-spacing: -2px;
            background: linear-gradient(to right, #fff, #b0b0b0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-family: 'JetBrains Mono', monospace;
            font-size: 1.5rem;
            color: var(--text-muted);
            margin-top: 20px;
            height: 30px; /* Miejsce na typewriter */
        }
        .subtitle span { color: var(--db-red); }

        /* --- GLITCH EFFECT --- */
        .glitch { position: relative; color: white; }
        .glitch::before, .glitch::after {
            content: attr(data-text); position: absolute; top: 0; left: 0; width: 100%; height: 100%;
        }
        .glitch::before { left: 2px; text-shadow: -1px 0 var(--db-red); clip: rect(24px, 550px, 90px, 0); animation: glitch-anim-2 3s infinite linear alternate-reverse; }
        .glitch::after { left: -2px; text-shadow: -1px 0 var(--ai-purple); clip: rect(85px, 550px, 140px, 0); animation: glitch-anim 2.5s infinite linear alternate-reverse; }

        @keyframes glitch-anim { 0% { clip: rect(11px, 9999px, 81px, 0); } 100% { clip: rect(68px, 9999px, 8px, 0); } }
        @keyframes glitch-anim-2 { 0% { clip: rect(65px, 9999px, 100px, 0); } 100% { clip: rect(3px, 9999px, 86px, 0); } }


        /* --- SECTIONS --- */
        section { padding: 100px 8%; }
        .section-header { margin-bottom: 60px; display: flex; align-items: flex-end; gap: 20px; border-bottom: 1px solid var(--border); padding-bottom: 20px; }
        .section-header h2 { font-size: 3rem; margin: 0; line-height: 1; letter-spacing: -1px; }
        .section-header span { color: var(--text-muted); font-family: 'JetBrains Mono'; font-size: 0.9rem; margin-bottom: 5px; }

        /* --- CARDS GRID --- */
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .card {
            background: var(--glass-bg);
            border: 1px solid var(--border);
            padding: 35px;
            border-radius: 16px;
            position: relative;
            overflow: hidden;
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            backdrop-filter: blur(10px);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card:hover { transform: translateY(-10px) scale(1.02); background: rgba(255,255,255,0.06); }

        /* COLORS FOR SECTIONS */
        .db-card { border-top: 4px solid var(--db-red); }
        .db-card:hover { box-shadow: 0 10px 40px rgba(255, 54, 33, 0.15); border-color: var(--db-red); }
        .db-card .icon { color: var(--db-red); }

        .ai-card { border-top: 4px solid var(--ai-purple); background: linear-gradient(180deg, rgba(217,0,255,0.05) 0%, rgba(0,0,0,0) 100%); }
        .ai-card:hover { box-shadow: 0 10px 40px rgba(217, 0, 255, 0.2); border-color: var(--ai-purple); }
        .ai-card .icon { color: var(--ai-purple); }

        .ms-card { border-top: 4px solid var(--ms-blue); }
        .ms-card:hover { box-shadow: 0 10px 40px rgba(0, 163, 224, 0.15); border-color: var(--ms-blue); }
        .ms-card .icon { color: var(--ms-blue); }

        .icon { font-size: 3rem; margin-bottom: 25px; display: block; }
        .card h3 { font-size: 1.5rem; margin: 0 0 10px 0; font-weight: 700; }
        .card .badge-small { font-family: 'JetBrains Mono'; font-size: 0.75rem; text-transform: uppercase; opacity: 0.7; letter-spacing: 1px; display: block; margin-bottom: 15px; }
        .card p { color: var(--text-muted); font-size: 0.95rem; margin: 0; }

        /* Highlighted PRO Card */
        .card.pro { grid-column: 1 / -1; display: flex; flex-direction: row; align-items: center; gap: 40px; }
        @media (max-width: 900px) { .card.pro { flex-direction: column; text-align: center; } }

        /* --- SMALL BADGES WALL --- */
        .wall-grid { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 40px; }
        .wall-tag {
            padding: 8px 16px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 0.85rem;
            color: #ccc;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: 0.3s;
        }
        .wall-tag:hover { background: rgba(255,255,255,0.1); border-color: #fff; color: #fff; }

        /* --- EXPERIENCE TIMELINE --- */
        .timeline { border-left: 2px solid rgba(255,255,255,0.1); padding-left: 50px; position: relative; }
        .timeline-block { position: relative; margin-bottom: 60px; }
        .timeline-block::before {
            content: ''; position: absolute; left: -59px; top: 5px;
            width: 16px; height: 16px; background: var(--bg-dark);
            border: 2px solid var(--db-red); border-radius: 50%;
            transition: 0.3s;
        }
        .timeline-block:hover::before { background: var(--db-red); box-shadow: 0 0 15px var(--db-red); }
        
        .role { font-size: 1.8rem; font-weight: 700; color: #fff; }
        .company { color: var(--db-red); font-family: 'JetBrains Mono'; font-size: 1.1rem; margin: 5px 0 15px 0; display: block; }

        /* --- FOOTER --- */
        footer { padding: 80px 0; text-align: center; background: #000; border-top: 1px solid var(--border); }
        .contact-btn {
            display: inline-block;
            margin-top: 20px;
            padding: 15px 40px;
            border: 1px solid var(--text-muted);
            color: #fff;
            border-radius: 50px;
            font-weight: 600;
            transition: 0.3s;
        }
        .contact-btn:hover { background: #fff; color: #000; }

    </style>
</head>
<body>

    <div id="particles-js"></div>

    <nav>
        <div class="logo">DAMIAN<span class="ai">.AI</span><span>.DATA</span></div>
        <div class="nav-links">
            <a href="#databricks">Databricks</a>
            <a href="#microsoft">Microsoft</a>
            <a href="#experience">Doświadczenie</a>
            <a href="#contact">Kontakt</a>
        </div>
    </nav>

    <section class="hero">
        <div class="status-badge">Open for Senior Roles</div>
        
        <h1 class="glitch" data-text="SENIOR DATA ENGINEER">
            SENIOR DATA ENGINEER
        </h1>
        
        <div class="subtitle">
            <span id="typewriter"></span>
        </div>

        <div style="margin-top: 50px; display: flex; gap: 20px; justify-content: center;">
            <div style="text-align: center;">
                <i class="fa-solid fa-certificate" style="color: var(--db-red); font-size: 1.5rem; margin-bottom: 5px;"></i>
                <div style="font-size: 0.8rem; color: #888;">DB Professional</div>
            </div>
            <div style="text-align: center;">
                <i class="fa-solid fa-wand-magic-sparkles" style="color: var(--ai-purple); font-size: 1.5rem; margin-bottom: 5px;"></i>
                <div style="font-size: 0.8rem; color: #888;">Gen AI Associate</div>
            </div>
            <div style="text-align: center;">
                <i class="fa-brands fa-microsoft" style="color: var(--ms-blue); font-size: 1.5rem; margin-bottom: 5px;"></i>
                <div style="font-size: 0.8rem; color: #888;">Azure Expert</div>
            </div>
        </div>
    </section>

    <section id="databricks">
        <div class="section-header" data-aos="fade-right">
            <h2>Databricks & AI</h2>
            <span>// The Core Engine & Future Tech</span>
        </div>

        <div class="grid-container">
            
            <div class="card db-card pro" data-tilt data-tilt-max="5" data-aos="fade-up">
                <i class="fa-solid fa-layer-group icon" style="font-size: 5rem; text-shadow: 0 0 30px rgba(255, 54, 33, 0.4);"></i>
                <div>
                    <span class="badge-small" style="color: var(--db-red);">Data Engineering Expert</span>
                    <h3>Databricks Certified Professional</h3>
                    <p>Zaawansowana architektura Lakehouse, optymalizacja kosztów i wydajności Spark, wdrażanie produkcyjnych potoków ETL w skali Enterprise.</p>
                </div>
            </div>

            <div class="card ai-card" data-tilt data-aos="fade-up" data-aos-delay="100">
                <i class="fa-solid fa-microchip icon"></i>
                <span class="badge-small" style="color: var(--ai-purple);">Generative AI Focus</span>
                <h3>Gen AI Associate</h3>
                <p>Tworzenie aplikacji opartych na LLM, RAG (Retrieval Augmented Generation), Vector Databases i Unity Catalog.</p>
            </div>

            <div class="card db-card" data-tilt data-aos="fade-up" data-aos-delay="200">
                <i class="fa-solid fa-fire icon"></i>
                <span class="badge-small" style="color: var(--db-red);">Core Developer</span>
                <h3>Apache Spark Dev</h3>
                <p>Deep dive w Catalyst Optimizer, Spark Internals i przetwarzanie rozproszone.</p>
            </div>

            <div class="card db-card" data-tilt data-aos="fade-up" data-aos-delay="300">
                <i class="fa-solid fa-server icon"></i>
                <span class="badge-small" style="color: var(--db-red);">Foundation</span>
                <h3>Associate Stack</h3>
                <ul style="padding-left: 20px; color: var(--text-muted); font-size: 0.9rem;">
                    <li>Data Engineer Associate</li>
                    <li>Data Analyst Associate</li>
                    <li>Machine Learning Associate</li>
                </ul>
            </div>

        </div>
    </section>

    <section id="microsoft">
        <div class="section-header" data-aos="fade-right">
            <h2>Microsoft Azure</h2>
            <span>// Cloud Architecture & Specialist Tools</span>
        </div>

        <div class="grid-container">
            
            <div class="card ms-card" data-tilt data-aos="zoom-in">
                <i class="fa-solid fa-network-wired icon"></i>
                <span class="badge-small" style="color: var(--ms-blue);">DP-600</span>
                <h3>Fabric Analytics Eng.</h3>
                <p>Nowoczesna analityka w Microsoft Fabric, OneLake i integracja Power BI.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="50">
                <i class="fa-solid fa-chart-pie icon"></i>
                <span class="badge-small" style="color: var(--ms-blue);">PL-300</span>
                <h3>Power BI Analyst</h3>
                <p>Zaawansowana wizualizacja danych, modelowanie DAX i raportowanie biznesowe.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="100">
                <i class="fa-solid fa-robot icon"></i>
                <span class="badge-small" style="color: var(--ms-blue);">AI-102</span>
                <h3>Azure AI Engineer</h3>
                <p>Implementacja Cognitive Services, botów i modeli AI w chmurze.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="150">
                <i class="fa-solid fa-database icon"></i>
                <span class="badge-small" style="color: var(--ms-blue);">DP-300</span>
                <h3>Azure DB Admin</h3>
                <p>Administracja SQL Server i Azure SQL Database.</p>
            </div>

             <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="200">
                <i class="fa-solid fa-globe icon"></i>
                <span class="badge-small" style="color: var(--ms-blue);">DP-420</span>
                <h3>Cosmos DB Dev</h3>
                <p>Nierelacyjne bazy danych i skalowanie globalne.</p>
            </div>
        </div>

        <div style="margin-top: 50px;">
            <p style="color: #666; font-family: 'JetBrains Mono'; text-transform: uppercase;">Fundamentals & GitHub Security</p>
            <div class="wall-grid">
                <div class="wall-tag"><i class="fa-brands fa-microsoft"></i> DP-203 Data Engineering</div>
                <div class="wall-tag"><i class="fa-brands fa-microsoft"></i> DP-700</div>
                <div class="wall-tag"><i class="fa-brands fa-microsoft"></i> AZ-900 Azure Fund.</div>
                <div class="wall-tag"><i class="fa-brands fa-microsoft"></i> DP-900 Data Fund.</div>
                <div class="wall-tag"><i class="fa-brands fa-microsoft"></i> AI-900 AI Fund.</div>
                <div class="wall-tag" style="border-color: #777;"><i class="fa-brands fa-github"></i> GH-300 Adv. Security</div>
                <div class="wall-tag" style="border-color: #777;"><i class="fa-brands fa-github"></i> GH-900 Foundations</div>
            </div>
        </div>
    </section>

    <section id="experience">
        <div class="section-header">
            <h2>Experience</h2>
        </div>

        <div class="timeline">
            
            <div class="timeline-block" data-aos="fade-left">
                <div class="role">Data Engineer</div>
                <span class="company">EY (Ernst & Young) | 10.2024 - Present</span>
                <p style="color: #bbb;">Tworzenie skalowalnych platform danych. Wdrażanie standardów Governance i architektury Lakehouse na Databricks.</p>
            </div>

            <div class="timeline-block" data-aos="fade-left" data-aos-delay="100">
                <div class="role">Data Engineer Intern</div>
                <span class="company">Sii Poland | 02.2024 - 10.2024</span>
                <p style="color: #bbb;">Budowa potoków ETL, migracje danych i wsparcie zespołów projektowych w środowisku Azure.</p>
            </div>

             <div class="timeline-block" data-aos="fade-left" data-aos-delay="200">
                <div class="role">Junior BI Specialist</div>
                <span class="company">Micro Solutions | 08.2022 - 06.2023</span>
                <p style="color: #bbb;">Analiza danych, tworzenie raportów w Power BI, optymalizacja zapytań SQL.</p>
            </div>

        </div>
    </section>

    <footer id="contact">
        <h2 style="font-size: 2.5rem; color: #fff;">Let's build the future of data.</h2>
        <p style="color: #666; font-size: 1.2rem;">Damian Kędzierski | Senior Data Engineer</p>
        
        <div style="margin-top: 40px; display: flex; gap: 20px; justify-content: center;">
            <a href="mailto:Damian.kedzierski@op.pl" class="contact-btn">Damian.kedzierski@op.pl</a>
            <a href="https://linkedin.com" class="contact-btn" style="background: #0077b5; border: none;"><i class="fa-brands fa-linkedin"></i> LinkedIn</a>
        </div>
        <p style="margin-top: 50px; opacity: 0.3; font-size: 0.8rem;">+48 533 864 722</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script src="https://unpkg.com/typewriter-effect@latest/dist/core.js"></script>

    <script>
        // Init Scroll Animations
        AOS.init({ once: true, offset: 50, duration: 800 });

        // Init Typewriter
        new Typewriter('#typewriter', {
            strings: [
                'Specializing in <span style="color: #FF3621;">Databricks Lakehouse</span>', 
                'Expert in <span style="color: #D900FF;">Generative AI</span>', 
                'Certified <span style="color: #00A3E0;">Azure Architect</span>'
            ],
            autoStart: true,
            loop: true,
            delay: 40,
            deleteSpeed: 20,
        });

        // Init Particles (Neural Network config)
        particlesJS("particles-js", {
            "particles": {
                "number": { "value": 70 },
                "color": { "value": "#ffffff" },
                "opacity": { "value": 0.3, "random": true },
                "size": { "value": 3, "random": true },
                "line_linked": { "enable": true, "distance": 150, "color": "#ffffff", "opacity": 0.1, "width": 1 },
                "move": { "enable": true, "speed": 1.5, "direction": "none", "random": false, "out_mode": "out" }
            },
            "interactivity": {
                "detect_on": "canvas",
                "events": {
                    "onhover": { "enable": true, "mode": "grab" }, /* Mouse connects dots */
                    "onclick": { "enable": true, "mode": "push" }
                },
                "modes": { "grab": { "distance": 140, "line_linked": { "opacity": 0.5 } } }
            }
        });
    </script>
</body>
</html>
