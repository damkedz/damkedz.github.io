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
            --db-red: #FF3621;
            --ai-purple: #9D28AC;
            --copilot-orange: #f78c6c;
            --azure-blue: #0078D4;
            --bg-black: #050505;
            --glass-strong: rgba(10, 10, 10, 0.85); /* Ciemniejsze tło kart dla czytelności tekstu */
            --border: rgba(255, 255, 255, 0.15);
            --text-main: #e0e0e0;
            --text-highlight: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-black);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            line-height: 1.7; /* Większy odstęp między liniami dla czytelności */
        }

        /* --- VIDEO BACKGROUND --- */
        .video-wrapper {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100vh;
            z-index: -2;
            overflow: hidden;
        }
        .video-wrapper video {
            width: 100%; height: 100%; object-fit: cover;
            opacity: 0.25; /* Mocniejsze przyciemnienie, żeby tekst był czytelny */
        }
        .overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at center, transparent 0%, #050505 100%);
            z-index: -1;
        }

        /* --- NAV --- */
        nav {
            display: flex; justify-content: space-between; align-items: center;
            padding: 20px 5%; position: fixed; width: 100%; top: 0; z-index: 1000;
            background: rgba(5, 5, 5, 0.9);
            border-bottom: 1px solid var(--border);
        }
        .logo { font-family: 'Space Grotesk'; font-weight: 700; font-size: 1.4rem; color: #fff; }
        .logo span { color: var(--db-red); }

        /* --- HERO --- */
        .hero {
            min-height: 95vh;
            display: flex; flex-direction: column; justify-content: center; align-items: flex-start; /* Do lewej dla więcej tekstu */
            padding: 0 10%;
        }

        h1 {
            font-family: 'Space Grotesk'; font-size: 4.5rem; line-height: 1.1; font-weight: 700;
            color: #fff; margin-bottom: 25px;
        }
        
        .hero-desc {
            font-size: 1.2rem; max-width: 700px; color: #ccc; margin-bottom: 40px;
            border-left: 4px solid var(--db-red); padding-left: 20px;
        }

        .btn-cta {
            padding: 15px 40px; background: var(--db-red); color: #fff; text-decoration: none;
            font-weight: 600; border-radius: 4px; transition: 0.3s;
            text-transform: uppercase; letter-spacing: 1px;
        }
        .btn-cta:hover { background: #d32f2f; }

        /* --- MARQUEE --- */
        .marquee-strip {
            background: #000; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border);
            padding: 15px 0; overflow: hidden; white-space: nowrap;
        }
        .marquee-content { display: inline-block; animation: scroll 25s linear infinite; }
        .tech-tag {
            display: inline-flex; align-items: center; gap: 8px; margin: 0 25px;
            color: #888; font-family: 'Space Grotesk'; font-weight: 600; font-size: 1rem;
        }
        @keyframes scroll { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

        /* --- ABOUT / PHILOSOPHY SECTION (NEW) --- */
        section { padding: 100px 10%; position: relative; }
        
        .philosophy-grid {
            display: grid; grid-template-columns: 1fr 1fr; gap: 50px;
            margin-bottom: 80px;
        }
        @media(max-width:900px) { .philosophy-grid { grid-template-columns: 1fr; } }

        .text-block h2 { font-family: 'Space Grotesk'; font-size: 2.5rem; margin-bottom: 20px; color: #fff; }
        .text-block p { margin-bottom: 20px; font-size: 1.05rem; }
        
        .stat-box {
            background: var(--glass-strong); border: 1px solid var(--border);
            padding: 30px; border-radius: 12px;
        }
        .stat-number { font-size: 3rem; font-weight: 700; color: var(--db-red); font-family: 'Space Grotesk'; }
        .stat-label { text-transform: uppercase; font-size: 0.9rem; letter-spacing: 2px; color: #888; }

        /* --- CERTIFICATION CARDS (TEXT HEAVY) --- */
        .grid-cards {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(380px, 1fr)); gap: 30px;
        }

        .card {
            background: var(--glass-strong);
            border: 1px solid var(--border);
            padding: 40px; border-radius: 16px;
            transition: 0.3s; position: relative;
        }
        .card:hover { transform: translateY(-5px); border-color: #555; }
        
        .card-header { display: flex; align-items: center; gap: 15px; margin-bottom: 20px; }
        .card-icon { font-size: 2.5rem; }
        .card h3 { font-size: 1.5rem; color: #fff; font-family: 'Space Grotesk'; margin: 0; }
        
        .card-body p { font-size: 0.95rem; color: #ccc; margin-bottom: 15px; }
        .tech-list { list-style: none; padding: 0; margin-top: 20px; }
        .tech-list li {
            position: relative; padding-left: 20px; margin-bottom: 8px; font-size: 0.9rem; color: #aaa;
        }
        .tech-list li::before {
            content: '▹'; position: absolute; left: 0; color: var(--db-red);
        }

        /* Specific Colors */
        .c-db { border-top: 3px solid var(--db-red); } .c-db .card-icon { color: var(--db-red); }
        .c-ai { border-top: 3px solid var(--ai-purple); } .c-ai .card-icon { color: var(--ai-purple); } .c-ai li::before { color: var(--ai-purple); }
        .c-gh { border-top: 3px solid var(--copilot-orange); } .c-gh .card-icon { color: var(--copilot-orange); } .c-gh li::before { color: var(--copilot-orange); }
        .c-ms { border-top: 3px solid var(--azure-blue); } .c-ms .card-icon { color: var(--azure-blue); } .c-ms li::before { color: var(--azure-blue); }

        /* --- EXPERIENCE (DETAILED) --- */
        .exp-item {
            border-left: 2px solid #333; padding-left: 40px; margin-bottom: 60px; position: relative;
        }
        .exp-item::after {
            content: ''; position: absolute; left: -9px; top: 0; width: 16px; height: 16px;
            background: #000; border: 3px solid var(--db-red); border-radius: 50%;
        }
        .exp-title { font-size: 1.8rem; color: #fff; font-weight: 700; font-family: 'Space Grotesk'; }
        .exp-meta { color: var(--db-red); font-weight: 600; margin: 5px 0 20px 0; display: block; letter-spacing: 1px; }
        .exp-desc { color: #ccc; max-width: 800px; }

        footer { background: #000; padding: 80px 10%; border-top: 1px solid #222; }
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
        <div style="color: #fff; font-size: 0.9rem; font-weight: 600;">
            SENIOR DATA ENGINEER
        </div>
    </nav>

    <section class="hero">
        <div style="color: var(--db-red); font-weight: 700; letter-spacing: 2px; margin-bottom: 20px;" data-aos="fade-down">
            // CERTIFIED ARCHITECT
        </div>
        <h1 data-aos="fade-up">
            Przekształcam surowe dane <br>
            w decyzje biznesowe.
        </h1>
        <div class="hero-desc" data-aos="fade-up" data-aos-delay="200">
            Specjalizuję się w budowaniu skalowalnych architektur <strong>Lakehouse</strong>, wdrażaniu <strong>Governance</strong> w Databricks oraz automatyzacji procesów przy użyciu <strong>Generative AI</strong>. Łączę perspektywę inżynierską z analityką biznesową.
        </div>
        <a href="#experience" class="btn-cta" data-aos="fade-up" data-aos-delay="400">Zobacz Realizacje</a>
    </section>

    <div class="marquee-strip">
        <div class="marquee-content">
            <span class="tech-tag"><i class="fa-solid fa-fire"></i> Apache Spark Tuning</span>
            <span class="tech-tag"><i class="fa-solid fa-layer-group"></i> Databricks Unity Catalog</span>
            <span class="tech-tag"><i class="fa-solid fa-code"></i> PySpark & SQL</span>
            <span class="tech-tag"><i class="fa-solid fa-robot"></i> RAG & LLM Ops</span>
            <span class="tech-tag"><i class="fa-brands fa-github"></i> Copilot AI Pair Programming</span>
            <span class="tech-tag"><i class="fa-brands fa-microsoft"></i> Azure Fabric & Synapse</span>
            <span class="tech-tag"><i class="fa-solid fa-server"></i> Medallion Architecture</span>
             <span class="tech-tag"><i class="fa-solid fa-fire"></i> Apache Spark Tuning</span>
             <span class="tech-tag"><i class="fa-solid fa-layer-group"></i> Databricks Unity Catalog</span>
             <span class="tech-tag"><i class="fa-solid fa-code"></i> PySpark & SQL</span>
             <span class="tech-tag"><i class="fa-solid fa-robot"></i> RAG & LLM Ops</span>
        </div>
    </div>

    <section id="about">
        <div class="philosophy-grid">
            <div class="text-block" data-aos="fade-right">
                <h2>Filozofia Inżynierii</h2>
                <p>
                    W Data Engineeringu nie chodzi tylko o przesuwanie danych z punktu A do B. Chodzi o <strong>Data Reliability</strong> i <strong>Cost Efficiency</strong>.
                </p>
                <p>
                    W moich projektach (EY, Sii) stawiam na architekturę <strong>Lakehouse</strong>, która eliminuje silosy danych. Jako Senior Engineer skupiam się na optymalizacji zapytań Spark (Catalyst Optimizer, Z-Ordering), co pozwala redukować koszty chmurowe o dziesiątki procent. Wdrażam pełne CI/CD dla danych, traktując pipeline'y ETL tak samo rygorystycznie jak kod aplikacji.
                </p>
            </div>
            <div data-aos="fade-left">
                <div class="stat-box">
                    <div class="stat-number">15+</div>
                    <div class="stat-label">Certyfikatów Microsoft & Databricks</div>
                </div>
                <div class="stat-box" style="margin-top: 20px;">
                    <div class="stat-number">Ekspert</div>
                    <div class="stat-label">Databricks Pro & Gen AI</div>
                </div>
            </div>
        </div>
    </section>

    <section id="certifications">
        <div style="margin-bottom: 60px;">
            <h2 style="font-family: 'Space Grotesk'; font-size: 3rem; margin-bottom: 10px;">Tech Expertise</h2>
            <p style="color: #888;">Kompetencje potwierdzone egzaminami na poziomie Professional.</p>
        </div>

        <div class="grid-cards">
            
            <div class="card c-db" data-aos="fade-up">
                <div class="card-header">
                    <i class="fa-solid fa-layer-group card-icon"></i>
                    <div>
                        <h3>Databricks Professional</h3>
                        <span style="font-size: 0.8rem; color: var(--db-red); font-weight: bold;">DATA ENGINEER EXPERT</span>
                    </div>
                </div>
                <div class="card-body">
                    <p>Certyfikat potwierdzający zdolność do zarządzania produkcyjnymi systemami Big Data. Nie są to tylko podstawy, ale głęboka optymalizacja.</p>
                    <ul class="tech-list">
                        <li>Zaawansowane modelowanie Delta Lake (SCD Type 2, CDC, Time Travel).</li>
                        <li>Optymalizacja wydajności: Partitioning, Liquid Clustering, zarządzanie "Skew Join".</li>
                        <li>Orkiestracja zadań z Delta Live Tables (DLT) i Databricks Workflows.</li>
                        <li>Implementacja Data Governance poprzez Unity Catalog.</li>
                    </ul>
                </div>
            </div>

            <div class="card c-db" data-aos="fade-up" data-aos-delay="100">
                <div class="card-header">
                    <i class="fa-solid fa-fire card-icon"></i>
                    <div>
                        <h3>Apache Spark Dev</h3>
                        <span style="font-size: 0.8rem; color: var(--db-red); font-weight: bold;">CORE ENGINE SPECIALIST</span>
                    </div>
                </div>
                <div class="card-body">
                    <p>Zrozumienie, co dzieje się "pod maską" klastra obliczeniowego, pozwala mi pisać kod PySpark, który jest wydajny i skalowalny.</p>
                    <ul class="tech-list">
                        <li>Analiza planów wykonania (Logical/Physical Plans) i Catalyst Optimizer.</li>
                        <li>Tuning pamięci i GC (Garbage Collection) dla executorów.</li>
                        <li>Wykorzystanie Adaptive Query Execution (AQE) w Spark 3.0+.</li>
                        <li>Obsługa złożonych transformacji na terabajtach danych.</li>
                    </ul>
                </div>
            </div>

            <div class="card c-ai" data-aos="fade-up" data-aos-delay="200">
                <div class="card-header">
                    <i class="fa-solid fa-wand-magic-sparkles card-icon"></i>
                    <div>
                        <h3>Gen AI & Copilot</h3>
                        <span style="font-size: 0.8rem; color: var(--ai-purple); font-weight: bold;">AI-DRIVEN ENGINEERING</span>
                    </div>
                </div>
                <div class="card-body">
                    <p>Łączę inżynierię danych z Generative AI. Posiadam certyfikat Gen AI Associate oraz GH-300 (GitHub Copilot).</p>
                    <ul class="tech-list">
                        <li>Budowa systemów RAG (Retrieval Augmented Generation) w Databricks.</li>
                        <li>Zarządzanie wektorowymi bazami danych (Vector Search).</li>
                        <li>Wykorzystanie GitHub Copilot do przyspieszania procesu deweloperskiego (AI Pair Programming).</li>
                        <li>MLflow do monitorowania i wersjonowania modeli LLM.</li>
                    </ul>
                </div>
            </div>

            <div class="card c-ms" data-aos="fade-up" data-aos-delay="300">
                <div class="card-header">
                    <i class="fa-brands fa-microsoft card-icon"></i>
                    <div>
                        <h3>Azure Cloud Architect</h3>
                        <span style="font-size: 0.8rem; color: var(--azure-blue); font-weight: bold;">FULL STACK DATA</span>
                    </div>
                </div>
                <div class="card-body">
                    <p>Kompleksowa znajomość ekosystemu Microsoft, od baz danych po analitykę Fabric.</p>
                    <ul class="tech-list">
                        <li><strong>DP-600:</strong> Fabric Analytics Engineer (Lakehouse/Warehouse).</li>
                        <li><strong>DP-300:</strong> Administracja i tuning baz Azure SQL.</li>
                        <li><strong>AI-102:</strong> Projektowanie rozwiązań AI w chmurze (Cognitive Services).</li>
                        <li><strong>DP-420:</strong> Cosmos DB (NoSQL data modeling).</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="experience">
        <h2 style="font-family: 'Space Grotesk'; font-size: 3rem; margin-bottom: 50px;">Ścieżka Kariery</h2>

        <div class="exp-item" data-aos="fade-left">
            <div class="exp-title">Data Engineer</div>
            <span class="exp-meta">EY (ERNST & YOUNG) | 10.2024 - OBECNIE</span>
            <div class="exp-desc">
                <p>Odpowiedzialny za projektowanie i wdrażanie rozwiązań chmurowych dla klientów Enterprise. Moja rola wykracza poza pisanie kodu:</p>
                <br>
                <ul>
                    <li>Projektowanie architektury <strong>Lakehouse</strong> z wykorzystaniem Delta Lake, zapewniając ACID transactions na data lake'u.</li>
                    <li>Wdrażanie strategii <strong>ESG Data</strong> – agregacja i przetwarzanie danych niefinansowych.</li>
                    <li>Optymalizacja kosztów chmurowych (FinOps) poprzez tuning klastrów Databricks i refaktoryzację kodu PySpark.</li>
                    <li>Mentoring techniczny dla młodszych programistów w zakresie CI/CD i dobrych praktyk Python.</li>
                </ul>
            </div>
        </div>

        <div class="exp-item" data-aos="fade-left" data-aos-delay="100">
            <div class="exp-title">Data Engineer Intern</div>
            <span class="exp-meta">SII POLAND | 02.2024 - 10.2024</span>
            <div class="exp-desc">
                <p>Intensywna praca nad migracją i przetwarzaniem danych w środowisku Azure.</p>
                <br>
                <ul>
                    <li>Tworzenie potoków ETL w <strong>Azure Data Factory</strong> oraz Databricks.</li>
                    <li>Automatyzacja procesów ingestii danych z różnych źródeł (API, SQL, Flat Files).</li>
                    <li>Praca w metodologii Agile/Scrum w międzynarodowym zespole.</li>
                </ul>
            </div>
        </div>

        <div class="exp-item" data-aos="fade-left" data-aos-delay="200">
            <div class="exp-title">Junior BI Specialist</div>
            <span class="exp-meta">MICRO SOLUTIONS | 08.2022 - 06.2023</span>
            <div class="exp-desc">
                <p>Fundamenty analityczne. Zrozumienie potrzeb biznesowych "końcówki" procesu danych.</p>
                <br>
                <ul>
                    <li>Tworzenie zaawansowanych raportów w <strong>Power BI</strong> (PL-300).</li>
                    <li>Modelowanie danych i pisanie zapytań DAX/SQL.</li>
                </ul>
            </div>
        </div>
    </section>

    <footer>
        <div style="text-align: center;">
            <h2 style="color: #fff; font-family: 'Space Grotesk'; margin-bottom: 20px;">Porozmawiajmy o Danych.</h2>
            <p style="color: #888; max-width: 500px; margin: 0 auto 40px auto;">
                Szukasz inżyniera, który nie tylko napisze kod, ale zrozumie architekturę i biznes?
            </p>
            <a href="mailto:Damian.kedzierski@op.pl" class="btn-cta" style="background: transparent; border: 1px solid #fff;">
                Damian.kedzierski@op.pl
            </a>
            <div style="margin-top: 50px;">
                <a href="https://linkedin.com" target="_blank" style="color: #fff; font-size: 2rem;"><i class="fa-brands fa-linkedin"></i></a>
            </div>
            <p style="margin-top: 30px; font-size: 0.8rem; color: #444;">&copy; 2025 Damian Kędzierski</p>
        </div>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script>
        AOS.init({ once: true, duration: 800 });
        VanillaTilt.init(document.querySelectorAll(".card"), {
            max: 5, speed: 400, glare: true, "max-glare": 0.2
        });
    </script>
</body>
</html>
