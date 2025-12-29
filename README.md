<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Engineer</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            /* KOLORYSTYKA */
            --db-red: #FF3621;       /* Databricks Red */
            --ms-blue: #0078D4;      /* Microsoft Blue */
            --bg-dark: #0f1012;      /* Bardzo ciemne tło */
            --card-bg: rgba(25, 25, 25, 0.9);
            --text-main: #ffffff;
            --text-muted: #a0a0a0;
        }

        * { box-sizing: border-box; }

        body {
            margin: 0;
            background-color: var(--bg-dark);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- TŁO CZĄSTECZKOWE (SIECIOWE) --- */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at center, #1a1a1a 0%, #000 100%);
        }

        /* --- NAV --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(15, 16, 18, 0.9);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .logo { font-weight: 800; font-size: 1.4rem; letter-spacing: -1px; }
        .logo span { color: var(--db-red); }
        
        .nav-links a { margin-left: 20px; color: var(--text-muted); text-decoration: none; transition: 0.3s; font-weight: 600;}
        .nav-links a:hover { color: #fff; }

        /* --- HERO --- */
        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        .badge {
            padding: 8px 16px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 25px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--text-muted);
        }

        h1 {
            font-size: 4.5rem;
            margin: 0 0 10px 0;
            font-weight: 800;
            line-height: 1.1;
        }

        .typewriter {
            font-family: monospace;
            font-size: 1.5rem;
            color: var(--db-red);
            height: 30px;
            margin-bottom: 40px;
        }

        /* --- GRIDY I KARTY --- */
        section { padding: 80px 10%; position: relative; }
        
        .section-header { margin-bottom: 50px; border-left: 5px solid; padding-left: 20px; }
        .section-header h2 { font-size: 2.5rem; margin: 0; }
        .section-header p { color: var(--text-muted); margin-top: 10px; }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
        }

        .card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: transform 0.1s; /* Dla efektu Tilt */
            transform-style: preserve-3d;
            transform: perspective(1000px);
        }
        
        /* Specyficzne style dla Databricks (Czerwony) */
        .db-section .section-header { border-color: var(--db-red); }
        .db-card { border-top: 3px solid var(--db-red); }
        .db-card .icon { color: var(--db-red); font-size: 2.5rem; margin-bottom: 20px; text-shadow: 0 0 20px rgba(255, 54, 33, 0.3); }
        
        /* Specyficzne style dla Microsoft (Niebieski) */
        .ms-section .section-header { border-color: var(--ms-blue); }
        .ms-card { border-top: 3px solid var(--ms-blue); }
        .ms-card .icon { color: var(--ms-blue); font-size: 2.5rem; margin-bottom: 20px; text-shadow: 0 0 20px rgba(0, 120, 212, 0.3); }

        .card h3 { margin: 0 0 10px 0; font-size: 1.3rem; color: #fff; }
        .card .code { font-size: 0.8rem; font-weight: bold; opacity: 0.7; display: block; margin-bottom: 10px; text-transform: uppercase;}
        .card p { color: var(--text-muted); font-size: 0.95rem; line-height: 1.5; }

        /* Wyróżnienie PRO */
        .card.pro {
            grid-column: 1 / -1;
            background: linear-gradient(145deg, #1a0f0f, #141414);
            border: 1px solid var(--db-red);
            display: flex;
            align-items: center;
            gap: 30px;
        }
        @media (max-width: 768px) { .card.pro { flex-direction: column; text-align: center; } }

        /* Small Tags Grid */
        .tags-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 30px;
        }
        .tag {
            background: #1a1a1a;
            border: 1px solid #333;
            padding: 8px 15px;
            border-radius: 5px;
            font-size: 0.85rem;
            color: #ccc;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* --- EXPERIENCE --- */
        .timeline-item {
            border-left: 2px solid #333;
            padding-left: 30px;
            margin-bottom: 40px;
            position: relative;
        }
        .timeline-item::before {
            content: ''; position: absolute; left: -6px; top: 8px;
            width: 10px; height: 10px; background: #fff; border-radius: 50%;
        }
        .timeline-item h3 { margin: 0; font-size: 1.4rem; }
        .timeline-item .company { color: var(--db-red); font-weight: bold; margin-bottom: 10px; display: block; }

        footer { padding: 50px; text-align: center; background: #050505; color: #666; }

    </style>
</head>
<body>

    <div id="particles-js"></div>

    <nav>
        <div class="logo">DAMIAN <span>KĘDZIERSKI</span></div>
        <div class="nav-links">
            <a href="#databricks">Databricks</a>
            <a href="#microsoft">Microsoft</a>
            <a href="#doswiadczenie">Doświadczenie</a>
            <a href="#kontakt">Kontakt</a>
        </div>
    </nav>

    <section class="hero">
        <div class="badge">Senior Profile</div>
        <h1 data-aos="zoom-in">DATA ENGINEER</h1>
        <div class="typewriter" id="typewriter"></div>
        
        <p style="color: var(--text-muted); max-width: 600px;">
            Specjalista architektury Lakehouse i chmury Azure. <br>
            Posiadacz elitarnego zestawu certyfikatów Databricks & Microsoft.
        </p>
    </section>

    <section id="databricks" class="db-section">
        <div class="section-header" data-aos="fade-right">
            <h2>Databricks Ecosystem</h2>
            <p>Architektura, Generative AI i Apache Spark</p>
        </div>

        <div class="cards-grid">
            
            <div class="card db-card pro" data-tilt data-aos="fade-up">
                <i class="fa-solid fa-layer-group icon" style="font-size: 4rem; margin: 0;"></i>
                <div>
                    <h3>Databricks Certified Professional</h3>
                    <span class="code" style="color: var(--db-red);">Data Engineer Expert Level</span>
                    <p>Potwierdzona ekspertyza w optymalizacji wydajności Spark, zaawansowanym modelowaniu Delta Lake i wdrażaniu produkcyjnych potoków danych w dużej skali.</p>
                </div>
            </div>

            <div class="card db-card" data-tilt data-aos="fade-up" data-aos-delay="100">
                <i class="fa-solid fa-wand-magic-sparkles icon"></i>
                <h3>Generative AI Engineer</h3>
                <span class="code">Specialist Certification</span>
                <p>Tworzenie rozwiązań LLM, systemy RAG (Retrieval Augmented Generation) i zarządzanie modelami w Unity Catalog.</p>
            </div>

            <div class="card db-card" data-tilt data-aos="fade-up" data-aos-delay="200">
                <i class="fa-solid fa-fire icon"></i>
                <h3>Apache Spark Developer</h3>
                <span class="code">Core Engine Specialist</span>
                <p>Głębokie zrozumienie architektury Spark, optymalizatora Catalyst i API DataFrame.</p>
            </div>

            <div class="card db-card" data-tilt data-aos="fade-up" data-aos-delay="300">
                <i class="fa-solid fa-cubes icon"></i>
                <h3>Associate Certificates</h3>
                <span class="code">Solid Foundation</span>
                <ul style="padding-left: 20px; margin: 0; color: var(--text-muted); font-size: 0.9rem;">
                    <li>Data Engineer Associate</li>
                    <li>Data Analyst Associate</li>
                    <li>Machine Learning Associate</li>
                </ul>
            </div>
        </div>
    </section>

    <section id="microsoft" class="ms-section">
        <div class="section-header" data-aos="fade-right">
            <h2>Microsoft Azure Ecosystem</h2>
            <p>Inżynieria Danych, AI, Power BI & Governance</p>
        </div>

        <div class="cards-grid">
            
            <div class="card ms-card" data-tilt data-aos="zoom-in">
                <i class="fa-solid fa-chart-network icon"></i>
                <h3>Fabric Analytics Engineer</h3>
                <span class="code">DP-600</span>
                <p>Kompleksowa analityka w Microsoft Fabric: Lakehouse i Warehouse.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="50">
                <i class="fa-solid fa-brain icon"></i>
                <h3>Azure AI Engineer</h3>
                <span class="code">AI-102</span>
                <p>Wdrażanie rozwiązań Cognitive Services i AI w chmurze.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="100">
                <i class="fa-solid fa-database icon"></i>
                <h3>Azure DB Admin</h3>
                <span class="code">DP-300</span>
                <p>Administracja i optymalizacja relacyjnych baz danych SQL.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="150">
                <i class="fa-solid fa-chart-simple icon"></i>
                <h3>Power BI Data Analyst</h3>
                <span class="code">PL-300</span>
                <p>Modelowanie danych, DAX i zaawansowana wizualizacja w Power BI.</p>
            </div>

            <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="200">
                <i class="fa-solid fa-globe icon"></i>
                <h3>Cosmos DB Developer</h3>
                <span class="code">DP-420</span>
                <p>Nierelacyjne bazy danych i dystrybucja globalna.</p>
            </div>

             <div class="card ms-card" data-tilt data-aos="zoom-in" data-aos-delay="250">
                <i class="fa-solid fa-server icon"></i>
                <h3>Data Engineering</h3>
                <span class="code">DP-203 / DP-700</span>
                <p>Przetwarzanie danych i orkiestracja w Azure Data Factory/Synapse.</p>
            </div>

        </div>

        <h4 style="margin-top: 40px; color: var(--text-muted);">FUNDAMENTALS & GITHUB SECURITY</h4>
        <div class="tags-grid">
            <div class="tag" style="border-color: #0078D4;"><i class="fa-brands fa-microsoft"></i> AZ-900 Azure Fund.</div>
            <div class="tag" style="border-color: #0078D4;"><i class="fa-brands fa-microsoft"></i> DP-900 Data Fund.</div>
            <div class="tag" style="border-color: #0078D4;"><i class="fa-brands fa-microsoft"></i> AI-900 AI Fund.</div>
            <div class="tag" style="border-color: #6e5494;"><i class="fa-brands fa-github"></i> GH-300 Adv. Security</div>
            <div class="tag" style="border-color: #6e5494;"><i class="fa-brands fa-github"></i> GH-900 Foundations</div>
        </div>
    </section>

    <section id="doswiadczenie">
        <div class="section-header">
            <h2>Ścieżka Kariery</h2>
        </div>
        
        <div class="timeline-item" data-aos="fade-up">
            <h3>Data Engineer</h3>
            <span class="company">EY (Ernst & Young) | 10.2024 - Obecnie</span>
            <p>Projektowanie architektury Lakehouse, Databricks Unity Catalog, optymalizacja kosztów chmurowych.</p>
        </div>

        <div class="timeline-item" data-aos="fade-up">
            <h3>Data Engineer Intern</h3>
            <span class="company">Sii Poland | 02.2024 - 10.2024</span>
            <p>Wsparcie migracji danych, tworzenie potoków ETL w Azure, praca w zespole zwinnym.</p>
        </div>

        <div class="timeline-item" data-aos="fade-up">
            <h3>Junior BI Specialist</h3>
            <span class="company">Micro Solutions | 08.2022 - 06.2023</span>
            <p>Raportowanie biznesowe, SQL, wizualizacja danych.</p>
        </div>
    </section>

    <footer id="kontakt">
        <h2 style="color: #fff;">Damian Kędzierski</h2>
        <p>+48 533 864 722 | Damian.kedzierski@op.pl</p>
        <div style="font-size: 2rem; margin-top: 20px;">
            <a href="https://linkedin.com" target="_blank" style="color: #fff;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script src="https://unpkg.com/typewriter-effect@latest/dist/core.js"></script>

    <script>
        AOS.init();

        // Typewriter
        new Typewriter('#typewriter', {
            strings: ['Databricks Professional', 'Generative AI Engineer', 'Apache Spark Developer', 'Microsoft Azure Expert'],
            autoStart: true,
            loop: true,
            delay: 50,
        });

        // Particles (Network Effect)
        particlesJS("particles-js", {
            "particles": {
                "number": { "value": 60 },
                "color": { "value": "#ffffff" },
                "opacity": { "value": 0.2 },
                "size": { "value": 2 },
                "line_linked": { "enable": true, "distance": 150, "color": "#FF3621", "opacity": 0.15, "width": 1 },
                "move": { "enable": true, "speed": 1 }
            }
        });
    </script>
</body>
</html>
