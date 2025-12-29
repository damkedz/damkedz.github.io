<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Architect</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            /* GLOBALNE */
            --bg-black: #050505;
            --text-main: #e0e0e0;
            --glass-panel: rgba(10, 10, 10, 0.9);
            
            /* DATABRICKS ZONE */
            --db-red: #FF3621;
            --db-bg: rgba(40, 10, 10, 0.3);
            
            /* MICROSOFT ZONE */
            --ms-blue: #0078D4;
            --ms-bg: rgba(10, 20, 40, 0.3);

            /* GITHUB / AI */
            --gh-purple: #9D28AC;
            --gh-orange: #f78c6c;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-black);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            line-height: 1.7;
        }

        /* --- VIDEO BACKGROUND --- */
        .video-wrapper {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            z-index: -2; overflow: hidden;
        }
        .video-wrapper video {
            width: 100%; height: 100%; object-fit: cover; opacity: 0.2;
        }
        .overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(180deg, rgba(5,5,5,0.8) 0%, rgba(5,5,5,0.95) 100%);
            z-index: -1;
        }

        /* --- NAV --- */
        nav {
            display: flex; justify-content: space-between; align-items: center;
            padding: 20px 5%; position: fixed; width: 100%; top: 0; z-index: 1000;
            background: rgba(5, 5, 5, 0.95); border-bottom: 1px solid rgba(255,255,255,0.1);
        }
        .logo { font-family: 'Space Grotesk'; font-weight: 700; font-size: 1.4rem; color: #fff; }
        .nav-links a { color: #aaa; text-decoration: none; margin-left: 20px; font-size: 0.9rem; transition: 0.3s; }
        .nav-links a:hover { color: #fff; }

        /* --- HERO --- */
        .hero {
            min-height: 90vh;
            display: flex; flex-direction: column; justify-content: center; align-items: flex-start;
            padding: 0 10%;
        }
        h1 {
            font-family: 'Space Grotesk'; font-size: 4.5rem; line-height: 1.1; font-weight: 700;
            color: #fff; margin-bottom: 25px;
        }
        .hero-tag {
            background: rgba(255,255,255,0.1); padding: 5px 15px; border-radius: 50px;
            font-size: 0.8rem; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 20px;
            border: 1px solid rgba(255,255,255,0.2);
        }

        /* --- STREFY (ZONES) --- */
        .zone-header {
            font-family: 'Space Grotesk'; font-size: 2.5rem; margin-bottom: 40px;
            display: flex; align-items: center; gap: 15px;
        }
        .zone-header::after { content: ''; flex: 1; height: 1px; background: rgba(255,255,255,0.1); }
        
        section { padding: 80px 10%; position: relative; }

        /* --- STREFA CZERWONA (DATABRICKS) --- */
        .db-zone { border-left: 5px solid var(--db-red); background: linear-gradient(90deg, var(--db-bg) 0%, transparent 100%); }
        .db-zone .zone-header { color: var(--db-red); }
        .db-zone .zone-header::after { background: var(--db-red); opacity: 0.3; }

        /* --- STREFA NIEBIESKA (MICROSOFT) --- */
        .ms-zone { border-left: 5px solid var(--ms-blue); background: linear-gradient(90deg, var(--ms-bg) 0%, transparent 100%); }
        .ms-zone .zone-header { color: var(--ms-blue); }
        .ms-zone .zone-header::after { background: var(--ms-blue); opacity: 0.3; }

        /* --- KARTY --- */
        .grid-cards {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 30px;
        }
        .card {
            background: var(--glass-panel); border: 1px solid rgba(255,255,255,0.1);
            padding: 35px; border-radius: 12px; position: relative; transition: 0.3s;
        }
        .card:hover { transform: translateY(-5px); }
        
        .card h3 { font-family: 'Space Grotesk'; font-size: 1.5rem; margin-bottom: 5px; color: #fff; }
        .card-sub { font-size: 0.8rem; text-transform: uppercase; letter-spacing: 1px; font-weight: bold; margin-bottom: 20px; display: block; }
        
        .tech-list { list-style: none; margin-top: 20px; }
        .tech-list li {
            position: relative; padding-left: 20px; margin-bottom: 8px; font-size: 0.9rem; color: #bbb;
        }
        
        /* Stylizacja kart zależna od strefy */
        .db-card { border-top: 3px solid var(--db-red); }
        .db-card .card-sub { color: var(--db-red); }
        .db-card li::before { content: '▹'; position: absolute; left: 0; color: var(--db-red); }
        
        .ms-card { border-top: 3px solid var(--ms-blue); }
        .ms-card .card-sub { color: var(--ms-blue); }
        .ms-card li::before { content: '▹'; position: absolute; left: 0; color: var(--ms-blue); }

        /* Specjalna karta PRO (Szeroka) */
        .card-wide { grid-column: 1 / -1; display: flex; align-items: center; gap: 40px; }
        @media(max-width:900px) { .card-wide { flex-direction: column; align-items: flex-start; } }
        .card-wide i { font-size: 5rem; }

        /* --- GITHUB & AI SECTION --- */
        .ai-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .gh-card { border-top: 3px solid var(--gh-orange); }
        .gh-card h3 i { color: var(--gh-orange); margin-right: 10px; }

        /* --- LISTA BADGE --- */
        .badge-wall { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 20px; }
        .badge {
            background: rgba(255,255,255,0.05); padding: 5px 12px; border-radius: 4px;
            font-size: 0.8rem; border: 1px solid rgba(255,255,255,0.1); color: #888;
        }

        /* --- FOOTER --- */
        footer { background: #000; padding: 60px 10%; border-top: 1px solid #222; text-align: center; }

    </style>
</head>
<body>

    <div class="video-wrapper">
        <video autoplay muted loop playsinline poster="https://images.pexels.com/photos/17483873/pexels-photo-17483873.jpeg">
            <source src="https://videos.pexels.com/video-files/3129671/3129671-hd_1920_1080_30fps.mp4" type="video/mp4">
        </video>
    </div>
    <div class="overlay"></div>

    <nav>
        <div class="logo">DAMIAN <span>KĘDZIERSKI</span></div>
        <div class="nav-links">
            <a href="#databricks" style="color: var(--db-red);">Databricks Ecosystem</a>
            <a href="#microsoft" style="color: var(--ms-blue);">Microsoft Azure</a>
            <a href="#ai">AI & GitHub</a>
        </div>
    </nav>

    <section class="hero">
        <div class="hero-tag" data-aos="fade-down">Senior Profile</div>
        <h1 data-aos="fade-up">
            Lakehouse Architect.<br>
            Azure Expert.<br>
            <span style="color: var(--db-red);">Databricks Pro.</span>
        </h1>
        <p style="max-width: 600px; color: #ccc; margin-top: 20px;" data-aos="fade-up" data-aos-delay="200">
            Specjalizuję się w inżynierii danych dużej skali. Łączę zaawansowaną optymalizację Sparka z bezpieczną architekturą chmury Azure.
        </p>
    </section>

    <section id="databricks" class="db-zone">
        <div class="zone-header" data-aos="fade-right">
            <i class="fa-solid fa-layer-group"></i> DATABRICKS ECOSYSTEM
        </div>

        <div class="grid-cards">
            <div class="card db-card card-wide" data-aos="fade-up">
                <i class="fa-solid fa-medal" style="color: var(--db-red);"></i>
                <div>
                    <h3>Databricks Certified Professional</h3>
                    <span class="card-sub">Data Engineer Expert Level</span>
                    <p>Potwierdzenie najwyższych kompetencji inżynierskich. Skupienie na wydajności produkcyjnej, bezpieczeństwie i skalowalności.</p>
                    <ul class="tech-list" style="columns: 2;">
                        <li>Advanced Delta Lake Modeling (SCD2, CDC)</li>
                        <li>Spark Performance Tuning & Optimization</li>
                        <li>Unity Catalog Governance Implementation</li>
                        <li>CI/CD for Data Pipelines (Databricks Asset Bundles)</li>
                    </ul>
                </div>
            </div>

            <div class="card db-card" data-aos="fade-up" data-aos-delay="100">
                <h3>Gen AI Associate</h3>
                <span class="card-sub">Generative AI Specialist</span>
                <p>Budowa nowoczesnych systemów AI w oparciu o modele LLM.</p>
                <ul class="tech-list">
                    <li>RAG Architecture (Retrieval Augmented Generation)</li>
                    <li>Vector Search & Embeddings</li>
                    <li>MLflow LLM Ops & Evaluation</li>
                </ul>
            </div>

            <div class="card db-card" data-aos="fade-up" data-aos-delay="200">
                <h3>Apache Spark Developer</h3>
                <span class="card-sub">Core Engine Expert</span>
                <p>Dogłębna znajomość silnika przetwarzania rozproszonego.</p>
                <ul class="tech-list">
                    <li>Catalyst Optimizer Internals</li>
                    <li>Memory Management & Garbage Collection</li>
                    <li>Adaptive Query Execution (AQE)</li>
                </ul>
            </div>

            <div class="card db-card" data-aos="fade-up" data-aos-delay="300">
                <h3>Associate Stack</h3>
                <span class="card-sub">Solid Foundations</span>
                <p>Pełne spektrum certyfikatów podstawowych.</p>
                <div class="badge-wall">
                    <span class="badge" style="border-color: var(--db-red); color: #fff;">Data Engineer Assoc.</span>
                    <span class="badge" style="border-color: var(--db-red); color: #fff;">Data Analyst Assoc.</span>
                    <span class="badge" style="border-color: var(--db-red); color: #fff;">Machine Learning Assoc.</span>
                </div>
            </div>
        </div>
    </section>

    <section id="microsoft" class="ms-zone">
        <div class="zone-header" data-aos="fade-right">
            <i class="fa-brands fa-microsoft"></i> AZURE ARCHITECTURE
        </div>

        <div class="grid-cards">
            <div class="card ms-card" data-aos="zoom-in">
                <h3>Fabric Analytics Engineer</h3>
                <span class="card-sub">DP-600 | Nowa Era Analityki</span>
                <p>Projektowanie rozwiązań end-to-end w Microsoft Fabric.</p>
                <ul class="tech-list">
                    <li>OneLake Data Architecture</li>
                    <li>Synapse Data Engineering</li>
                    <li>Direct Lake Mode w Power BI</li>
                </ul>
            </div>

            <div class="card ms-card" data-aos="zoom-in" data-aos-delay="100">
                <h3>Azure AI Engineer</h3>
                <span class="card-sub">AI-102 | Artificial Intelligence</span>
                <p>Wdrażanie rozwiązań kognitywnych w chmurze.</p>
                <ul class="tech-list">
                    <li>Azure OpenAI Service Integration</li>
                    <li>Cognitive Search & Indexing</li>
                    <li>AI Security & Responsible AI</li>
                </ul>
            </div>

            <div class="card ms-card" data-aos="zoom-in" data-aos-delay="200">
                <h3>Database Specialist</h3>
                <span class="card-sub">DP-300 & DP-420</span>
                <p>Zaawansowane zarządzanie danymi relacyjnymi i NoSQL.</p>
                <ul class="tech-list">
                    <li>SQL Server Performance Tuning (DP-300)</li>
                    <li>Cosmos DB Global Distribution (DP-420)</li>
                    <li>High Availability & DR Strategies</li>
                </ul>
            </div>

            <div class="card ms-card" data-aos="zoom-in" data-aos-delay="300">
                <h3>Analytics & Core</h3>
                <span class="card-sub">PL-300 & DP-203/700</span>
                <div class="badge-wall">
                    <span class="badge" style="border-color: var(--ms-blue); color: #fff;">PL-300 Power BI</span>
                    <span class="badge" style="border-color: var(--ms-blue); color: #fff;">DP-203 Data Eng.</span>
                    <span class="badge">AZ-900 Azure Fund.</span>
                    <span class="badge">DP-900 Data Fund.</span>
                    <span class="badge">AI-900 AI Fund.</span>
                </div>
            </div>
        </div>
    </section>

    <section id="ai" style="padding-top: 40px;">
        <div class="grid-cards ai-grid">
            <div class="card gh-card" data-aos="fade-up">
                <h3><i class="fa-brands fa-github"></i> GitHub Copilot</h3>
                <span class="card-sub" style="color: var(--gh-orange);">GH-300 Expert</span>
                <p>Wykorzystanie AI do przyspieszania developmentu. AI Pair Programming, refaktoryzacja kodu i automatyzacja testów.</p>
            </div>
            
            <div class="card gh-card" data-aos="fade-up" data-aos-delay="100" style="border-top-color: #9D28AC;">
                <h3><i class="fa-brands fa-github"></i> GitHub Foundations</h3>
                <span class="card-sub" style="color: #9D28AC;">GH-900 Security & Ops</span>
                <p>Zarządzanie repozytoriami, GitHub Actions (CI/CD) oraz bezpieczeństwo kodu (Advanced Security).</p>
            </div>
        </div>
    </section>

    <section id="experience" style="border-top: 1px solid #222;">
        <h2 style="font-family: 'Space Grotesk'; font-size: 2.5rem; margin-bottom: 40px; color: #fff;">Doświadczenie</h2>
        
        <div style="border-left: 2px solid #333; padding-left: 30px;">
            <div style="margin-bottom: 50px;" data-aos="fade-left">
                <h3 style="color: #fff; margin-bottom: 5px;">Data Engineer</h3>
                <span style="color: var(--db-red); font-weight: bold; font-family: 'Space Grotesk';">EY (Ernst & Young) | 10.2024 - Obecnie</span>
                <p style="color: #bbb; margin-top: 10px; max-width: 800px;">
                    Projektowanie architektury Lakehouse i optymalizacja kosztów (FinOps) dla klientów Enterprise. Praca z Databricks Unity Catalog i ESG Data.
                </p>
            </div>
            
            <div style="margin-bottom: 50px;" data-aos="fade-left">
                <h3 style="color: #fff; margin-bottom: 5px;">Data Engineer Intern</h3>
                <span style="color: var(--db-red); font-weight: bold; font-family: 'Space Grotesk';">Sii Poland | 02.2024 - 10.2024</span>
                <p style="color: #bbb; margin-top: 10px; max-width: 800px;">
                    Migracje danych, budowa pipeline'ów w Azure Data Factory, automatyzacja ETL.
                </p>
            </div>

            <div data-aos="fade-left">
                <h3 style="color: #fff; margin-bottom: 5px;">Junior BI Specialist</h3>
                <span style="color: var(--db-red); font-weight: bold; font-family: 'Space Grotesk';">Micro Solutions | 08.2022 - 06.2023</span>
                <p style="color: #bbb; margin-top: 10px; max-width: 800px;">
                    Analityka biznesowa i raportowanie w Power BI (PL-300).
                </p>
            </div>
        </div>
    </section>

    <footer>
        <h2 style="color: #fff; margin-bottom: 20px;">Damian Kędzierski</h2>
        <a href="mailto:Damian.kedzierski@op.pl" style="color: var(--text-main); font-size: 1.2rem;">Damian.kedzierski@op.pl</a>
        <div style="margin-top: 30px; font-size: 2rem;">
            <a href="https://linkedin.com" target="_blank" style="color: #fff;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init();
    </script>
</body>
</html>
