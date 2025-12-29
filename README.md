<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Engineer</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            --db-red: #FF3621;
            --gen-ai: #9D28AC; /* Fiolet dla Generative AI */
            --spark: #E25A1C;  /* Pomarańcz dla Apache Spark */
            --azure: #0078D4;
            --bg-dark: #050505;
            --card-bg: rgba(20, 20, 20, 0.6);
            --text-main: #ffffff;
            --text-muted: #888888;
        }

        * { box-sizing: border-box; }

        body {
            margin: 0;
            background-color: var(--bg-dark);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
        }

        /* --- TŁO CZĄSTECZKOWE --- */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at center, #111 0%, #000 100%);
        }

        /* --- NAWIGACJA --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .logo { font-family: 'JetBrains Mono', monospace; font-weight: 700; font-size: 1.2rem; }
        .logo span { color: var(--db-red); }

        /* --- HERO SECTION --- */
        .hero {
            height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
        }

        /* Glitch Effect Title */
        .glitch-wrapper { position: relative; display: inline-block; }
        h1 {
            font-size: 5rem;
            font-weight: 800;
            line-height: 1;
            margin: 0;
            text-transform: uppercase;
            position: relative;
            z-index: 1;
        }
        
        .role-title {
            font-size: 5rem;
            background: linear-gradient(90deg, #fff, #aaa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-family: 'JetBrains Mono', monospace;
            color: var(--db-red);
            margin-top: 20px;
            font-size: 1.2rem;
            background: rgba(255, 54, 33, 0.1);
            padding: 5px 15px;
            border-radius: 4px;
            border: 1px solid rgba(255, 54, 33, 0.3);
        }

        .typing-container {
            margin-top: 20px;
            height: 30px;
            color: var(--text-muted);
            font-family: 'JetBrains Mono', monospace;
        }

        /* --- SEKCJA CERTYFIKATÓW (GRIDY) --- */
        section { padding: 80px 8%; }
        .section-title {
            font-size: 2.5rem;
            margin-bottom: 50px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        .section-title::after {
            content: ''; flex: 1; height: 1px; background: linear-gradient(90deg, #333, transparent);
        }

        /* KARTY TOP TIER */
        .elite-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }

        .card {
            background: var(--card-bg);
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 12px;
            padding: 30px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
        }

        /* Hover Effects */
        .card:hover { transform: translateY(-10px) scale(1.02); }
        
        /* Specyficzne kolory poświaty */
        .card.db-pro:hover { box-shadow: 0 0 30px rgba(255, 54, 33, 0.2); border-color: var(--db-red); }
        .card.gen-ai:hover { box-shadow: 0 0 30px rgba(157, 40, 172, 0.2); border-color: var(--gen-ai); }
        .card.spark:hover { box-shadow: 0 0 30px rgba(226, 90, 28, 0.2); border-color: var(--spark); }
        .card.azure:hover { box-shadow: 0 0 20px rgba(0, 120, 212, 0.2); border-color: var(--azure); }

        .card-icon { font-size: 2.5rem; margin-bottom: 20px; display: block; }
        .card h3 { margin: 0 0 10px 0; font-size: 1.4rem; }
        .card span { font-size: 0.8rem; text-transform: uppercase; letter-spacing: 1px; opacity: 0.7; display: block; margin-bottom: 15px; }
        .card p { font-size: 0.95rem; color: #aaa; line-height: 1.5; }

        /* LISTA DLA MNIEJSZYCH CERTYFIKATÓW */
        .compact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
        }
        .mini-card {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.05);
            padding: 15px 20px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: 0.3s;
        }
        .mini-card:hover { background: rgba(255,255,255,0.08); }
        .mini-card i { color: var(--text-muted); }
        .mini-card.gh i { color: #fff; }

        /* --- TIMELINE DOŚWIADCZENIA --- */
        .timeline {
            border-left: 2px solid rgba(255,255,255,0.1);
            padding-left: 40px;
        }
        .timeline-item {
            position: relative;
            margin-bottom: 50px;
        }
        .timeline-item::before {
            content: ''; position: absolute; left: -46px; top: 5px;
            width: 10px; height: 10px; background: var(--db-red); border-radius: 50%;
            box-shadow: 0 0 15px var(--db-red);
        }
        .timeline-date { font-family: 'JetBrains Mono'; font-size: 0.85rem; color: var(--text-muted); margin-bottom: 5px; display: block; }
        .timeline-role { font-size: 1.5rem; font-weight: 700; margin-bottom: 5px; color: #fff; }
        .timeline-company { font-size: 1.1rem; color: var(--db-red); margin-bottom: 15px; }

        /* --- FOOTER --- */
        footer {
            background: #020202;
            padding: 60px 0;
            text-align: center;
            border-top: 1px solid #111;
        }
        .social-btn {
            display: inline-block;
            font-size: 2rem;
            color: #fff;
            margin-top: 20px;
            transition: 0.3s;
        }
        .social-btn:hover { color: var(--azure); transform: scale(1.1); }

        @media (max-width: 768px) {
            h1 { font-size: 3rem; }
            .hero { height: auto; padding: 100px 20px; }
            section { padding: 50px 5%; }
        }
    </style>
</head>
<body>

    <div id="particles-js"></div>

    <nav>
        <div class="logo">DAMIAN<span>.DATA</span></div>
        <div style="font-size: 1.5rem; color: #fff;">
            <a href="https://linkedin.com" target="_blank" style="color:white;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </nav>

    <section class="hero">
        <div data-aos="fade-down" class="subtitle">CERTIFIED EXPERT</div>
        
        <h1 class="role-title" data-aos="zoom-in" data-aos-duration="1000">
            SENIOR <br> DATA ENGINEER
        </h1>
        
        <div class="typing-container">
            <span id="typewriter"></span>
        </div>

        <div style="margin-top: 40px; display: flex; gap: 20px;">
            <a href="#elite" class="button" style="color: #fff; border: 1px solid var(--db-red); padding: 12px 30px; border-radius: 50px; text-decoration: none; transition: 0.3s; background: rgba(255,54,33,0.1);">
                View Credentials
            </a>
        </div>
    </section>

    <section id="elite">
        <div class="section-title">
            <i class="fa-solid fa-crown" style="color: #FFD700;"></i> Elite Certifications
        </div>
        
        <div class="elite-grid">
            <div class="card db-pro" data-tilt>
                <i class="fa-solid fa-layer-group card-icon" style="color: var(--db-red);"></i>
                <h3>Databricks Professional</h3>
                <span style="color: var(--db-red);">Data Engineer Expert</span>
                <p>Zaawansowana optymalizacja Spark, architektura Delta Lake, CI/CD oraz wdrażanie produkcyjnych potoków ETL w dużej skali.</p>
            </div>

            <div class="card gen-ai" data-tilt>
                <i class="fa-solid fa-wand-magic-sparkles card-icon" style="color: var(--gen-ai);"></i>
                <h3>Generative AI Engineer</h3>
                <span style="color: var(--gen-ai);">Databricks Certified</span>
                <p>Tworzenie aplikacji LLM, RAG (Retrieval Augmented Generation), obsługa Vector Database i wdrażanie modeli w Databricks.</p>
            </div>

            <div class="card spark" data-tilt>
                <i class="fa-solid fa-fire card-icon" style="color: var(--spark);"></i>
                <h3>Apache Spark Developer</h3>
                <span style="color: var(--spark);">Certified Associate</span>
                <p>Głęboka znajomość Spark DataFrame API, optymalizacji Catalyst Optimizer i wewnętrznego działania silnika Spark.</p>
            </div>
        </div>
    </section>

    <section id="ecosystem">
        <div class="section-title">
            <i class="fa-brands fa-microsoft" style="color: var(--azure);"></i> Cloud & Specialist Ecosystem
        </div>

        <div class="elite-grid" style="grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));">
            
            <div class="card azure" data-tilt>
                <i class="fa-solid fa-project-diagram card-icon" style="color: var(--azure);"></i>
                <h3>Fabric Analytics Engineer</h3>
                <span>DP-600</span>
                <p>Kompleksowa analityka w Microsoft Fabric: Lakehouse, Warehouse i Power BI.</p>
            </div>

            <div class="card azure" data-tilt>
                <i class="fa-solid fa-robot card-icon" style="color: #e84393;"></i>
                <h3>Azure AI Engineer</h3>
                <span>AI-102</span>
                <p>Budowa rozwiązań AI, Cognitive Services i integracja modeli w chmurze Azure.</p>
            </div>

            <div class="card azure" data-tilt>
                <i class="fa-solid fa-database card-icon" style="color: #27ae60;"></i>
                <h3>Azure DB Admin</h3>
                <span>DP-300</span>
                <p>Administracja, optymalizacja i zarządzanie relacyjnymi bazami SQL w chmurze.</p>
            </div>

             <div class="card azure" data-tilt>
                <i class="fa-solid fa-leaf card-icon" style="color: #27ae60;"></i>
                <h3>Cosmos DB Developer</h3>
                <span>DP-420</span>
                <p>Modelowanie danych nierelacyjnych i skalowanie globalne.</p>
            </div>

        </div>

        <h4 style="margin-top: 50px; color: var(--text-muted); text-transform: uppercase;">Foundation & DevOps Stack</h4>
        <div class="compact-grid">
            <div class="mini-card db-pro"><i class="fa-solid fa-check"></i> DB Data Engineer Assoc.</div>
            <div class="mini-card db-pro"><i class="fa-solid fa-check"></i> DB Analyst Assoc.</div>
            <div class="mini-card db-pro"><i class="fa-solid fa-check"></i> DB ML Associate</div>
            <div class="mini-card"><i class="fa-brands fa-microsoft"></i> DP-900 Data Fund.</div>
            <div class="mini-card"><i class="fa-brands fa-microsoft"></i> AZ-900 Azure Fund.</div>
            <div class="mini-card"><i class="fa-brands fa-microsoft"></i> AI-900 AI Fund.</div>
            <div class="mini-card"><i class="fa-brands fa-microsoft"></i> DP-700 / DP-203</div>
            <div class="mini-card gh"><i class="fa-brands fa-github"></i> GH-300 Adv. Security</div>
            <div class="mini-card gh"><i class="fa-brands fa-github"></i> GH-900 Foundations</div>
        </div>
    </section>

    <section id="experience">
        <div class="section-title">Experience</div>
        <div class="timeline">
            
            <div class="timeline-item" data-aos="fade-left">
                <span class="timeline-date">10.2024 - PRESENT</span>
                <div class="timeline-role">Data Engineer</div>
                <div class="timeline-company">EY (Ernst & Young)</div>
                <p style="color: #ccc;">Projektowanie i wdrażanie architektury Lakehouse. Optymalizacja kosztów chmurowych. Praca z technologiami Gen AI.</p>
            </div>

            <div class="timeline-item" data-aos="fade-left" data-aos-delay="100">
                <span class="timeline-date">02.2024 - 10.2024</span>
                <div class="timeline-role">Data Engineer Intern</div>
                <div class="timeline-company">Sii Poland</div>
                <p style="color: #ccc;">Migracje danych, wsparcie procesów ETL i rozwój kompetencji w ekosystemie Azure Big Data.</p>
            </div>

             <div class="timeline-item" data-aos="fade-left" data-aos-delay="200">
                <span class="timeline-date">08.2022 - 06.2023</span>
                <div class="timeline-role">Junior BI Specialist</div>
                <div class="timeline-company">Micro Solutions</div>
                <p style="color: #ccc;">Business Intelligence, raportowanie i analiza danych.</p>
            </div>

        </div>
    </section>

    <footer>
        <h2 style="margin: 0;">Damian Kędzierski</h2>
        <p style="color: var(--text-muted);">+48 533 864 722 | Damian.kedzierski@op.pl</p>
        <a href="https://www.linkedin.com/in/damian-kędzierski-3763252ba" class="social-btn"><i class="fa-brands fa-linkedin"></i></a>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script src="https://unpkg.com/typewriter-effect@latest/dist/core.js"></script>

    <script>
        AOS.init();

        // Typewriter Effect
        const typeTarget = document.getElementById('typewriter');
        const typewriter = new Typewriter(typeTarget, {
            loop: true,
            delay: 75,
        });

        typewriter
            .typeString('Databricks Professional.')
            .pauseFor(1000)
            .deleteAll()
            .typeString('Generative AI Engineer.')
            .pauseFor(1000)
            .deleteAll()
            .typeString('Apache Spark Developer.')
            .pauseFor(1000)
            .start();

        // Particles
        particlesJS("particles-js", {
            "particles": {
                "number": { "value": 80 },
                "color": { "value": "#ffffff" },
                "shape": { "type": "circle" },
                "opacity": { "value": 0.3 },
                "size": { "value": 2 },
                "line_linked": { "enable": true, "distance": 150, "color": "#FF3621", "opacity": 0.2, "width": 1 },
                "move": { "speed": 1 }
            }
        });
    </script>
</body>
</html>
