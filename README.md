<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Databricks Expert</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* --- DATABRICKS THEME --- */
        :root {
            --db-primary: #FF3621; /* Databricks Orange/Red */
            --db-dark: #1B1D1F;    /* Databricks Dark Slate */
            --db-bg: #0E0E0E;      /* Almost Black */
            --text-main: #FFFFFF;
            --text-sec: #B0B0B0;
            --card-bg: #242628;
            --azure-blue: #0078D4; /* Akcent dla Azure/Microsoft */
        }

        * { box-sizing: border-box; }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            margin: 0;
            background-color: var(--db-bg);
            color: var(--text-main);
            line-height: 1.6;
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        
        /* --- HEADER / NAV --- */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(14, 14, 14, 0.9);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid #333;
        }

        .brand { font-size: 1.5rem; font-weight: 800; letter-spacing: -1px; }
        .brand span { color: var(--db-primary); }

        .nav-links { display: flex; gap: 30px; }
        .nav-links a:hover { color: var(--db-primary); }

        /* --- HERO SECTION --- */
        .hero {
            padding: 100px 5%;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            background: radial-gradient(circle at 50% 20%, #2a1515 0%, var(--db-bg) 60%);
        }

        .badge-container {
            background: rgba(255, 54, 33, 0.1);
            color: var(--db-primary);
            padding: 5px 15px;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 54, 33, 0.3);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        h1 {
            font-size: 4rem;
            margin: 0 0 20px 0;
            line-height: 1.1;
            font-weight: 800;
        }

        h1 .highlight {
            background: linear-gradient(90deg, #FF3621, #FF8D4B);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 1.5rem;
            color: var(--text-sec);
            max-width: 800px;
            margin-bottom: 40px;
        }

        .btn-main {
            background-color: var(--db-primary);
            color: white;
            padding: 15px 40px;
            border-radius: 5px;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 0 20px rgba(255, 54, 33, 0.3);
        }
        .btn-main:hover { transform: scale(1.05); box-shadow: 0 0 30px rgba(255, 54, 33, 0.5); }

        /* --- CERTYFIKATY (GRID) --- */
        .certs-section { padding: 80px 10%; background: #151515; }
        .section-title { text-align: center; font-size: 2.5rem; margin-bottom: 60px; font-weight: 700; }
        
        .certs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
        }

        .cert-card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid #333;
            position: relative;
            overflow: hidden;
            transition: 0.4s;
        }

        .cert-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 4px; height: 100%;
            background: var(--db-primary);
        }

        .cert-card:hover { transform: translateY(-10px); border-color: var(--db-primary); }

        .cert-icon { font-size: 2.5rem; color: var(--db-primary); margin-bottom: 20px; }
        .cert-title { font-size: 1.25rem; font-weight: 700; margin-bottom: 10px; }
        .cert-issuer { font-size: 0.9rem; color: var(--text-sec); display: block; margin-bottom: 15px; }
        
        /* Specjalny styl dla "Pro" */
        .cert-card.pro {
            background: linear-gradient(145deg, #242628 0%, #2f1210 100%);
            border: 1px solid #5a2a2a;
        }

        /* --- DOŚWIADCZENIE (timeline style) --- */
        .exp-section { padding: 80px 10%; }
        
        .timeline-item {
            display: flex;
            margin-bottom: 40px;
            border-left: 2px solid #333;
            padding-left: 30px;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -6px; top: 0;
            width: 10px; height: 10px;
            background: var(--db-primary);
            border-radius: 50%;
        }

        .job-title { font-size: 1.3rem; font-weight: 700; color: white; }
        .company { color: var(--db-primary); font-weight: 600; }
        .job-date { font-size: 0.9rem; color: var(--text-sec); margin-left: 10px; }
        .job-desc { color: #ccc; margin-top: 10px; }

        /* --- STACK --- */
        .stack-bar {
            background: #111;
            padding: 40px 0;
            border-top: 1px solid #333;
            border-bottom: 1px solid #333;
            text-align: center;
        }
        .tech-tags { display: flex; justify-content: center; flex-wrap: wrap; gap: 15px; margin-top: 20px; }
        .tag { 
            background: #2a2a2a; padding: 8px 18px; border-radius: 4px; font-weight: 500; 
            border: 1px solid transparent; transition: 0.3s;
        }
        .tag:hover { border-color: var(--db-primary); color: var(--db-primary); }

        /* --- FOOTER --- */
        footer { padding: 50px 10%; background: #000; text-align: center; border-top: 1px solid #222; }
        
        @media (max-width: 768px) {
            h1 { font-size: 2.5rem; }
            .nav-links { display: none; } /* Uproszczone dla mobile */
        }
    </style>
</head>
<body>

    <header>
        <div class="brand">Damian<span>Kędzierski</span></div>
        <nav class="nav-links">
            <a href="#certyfikaty">Certyfikaty</a>
            <a href="#doswiadczenie">Doświadczenie</a>
            <a href="#kontakt">Kontakt</a>
        </nav>
    </header>

    <section class="hero">
        <div class="badge-container"><i class="fa-solid fa-medal"></i> Certified Databricks Expert</div>
        <h1>Data Engineering <br>w architekturze <span class="highlight">Lakehouse</span></h1>
        <p class="subtitle">
            Specjalizuję się w budowaniu wydajnych platform danych na dużą skalę. 
            Łączę ekosystem Databricks z chmurą Azure, dostarczając wartość biznesową dla EY.
        </p>
        <a href="#kontakt" class="btn-main">Porozmawiajmy o danych</a>
    </section>

    <section id="certyfikaty" class="certs-section">
        <div class="section-title">Certyfikacja Master Class</div>
        <div class="certs-grid">
            
            <div class="cert-card pro">
                <i class="fa-solid fa-layer-group cert-icon"></i>
                <div class="cert-title">Databricks Certified Data Engineer Professional</div>
                <span class="cert-issuer">Databricks</span>
                <p>Potwierdzenie eksperckiej wiedzy w zakresie optymalizacji Spark, modelowania Delta Lake i wdrażania produkcyjnych potoków ETL.</p>
            </div>

            <div class="cert-card">
                <i class="fa-solid fa-cube cert-icon"></i>
                <div class="cert-title">Databricks Certified Data Engineer Associate</div>
                <span class="cert-issuer">Databricks</span>
                <p>Solidne fundamenty architektury Lakehouse i przetwarzania danych z użyciem Apache Spark.</p>
            </div>

            <div class="cert-card">
                <i class="fa-solid fa-brain cert-icon"></i>
                <div class="cert-title">Databricks Certified Machine Learning</div>
                <span class="cert-issuer">Databricks</span>
                <p>Wdrażanie modeli ML i zarządzanie cyklem życia (MLflow) w środowisku Databricks.</p>
            </div>

            <div class="cert-card" style="border-left-color: var(--azure-blue);">
                <i class="fa-brands fa-microsoft cert-icon" style="color: var(--azure-blue);"></i>
                <div class="cert-title">Fabric Analytics Engineer Associate</div>
                <span class="cert-issuer">Microsoft</span>
                <p>DP-600: Projektowanie i wdrażanie rozwiązań analitycznych w Microsoft Fabric.</p>
            </div>

            <div class="cert-card" style="border-left-color: #fff;">
                <i class="fa-solid fa-database cert-icon" style="color: #fff;"></i>
                <div class="cert-title">SQL Associate</div>
                <span class="cert-issuer">Branżowy</span>
                <p>Zaawansowana znajomość języka SQL do analizy i manipulacji danymi.</p>
            </div>

        </div>
    </section>

    <div class="stack-bar">
        <h3 style="color: var(--text-sec); margin: 0;">Mój Stack Technologiczny</h3>
        <div class="tech-tags">
            <span class="tag">Apache Spark</span>
            <span class="tag">Delta Lake</span>
            <span class="tag">Python (PySpark)</span>
            <span class="tag">Databricks SQL</span>
            <span class="tag">Unity Catalog</span>
            <span class="tag">Azure Data Factory</span>
            <span class="tag">Kubernetes</span>
            <span class="tag">DBT</span>
            <span class="tag">CI/CD</span>
        </div>
    </div>

    <section id="doswiadczenie" class="exp-section">
        <div class="section-title">Ścieżka Kariery</div>
        
        <div class="timeline-item">
            <div>
                <div class="job-title">Data Engineer <span class="job-date">10.2024 - Obecnie</span></div>
                <div class="company">EY (Ernst & Young)</div>
                <div class="job-desc">
                    Realizacja projektów z zakresu chmury i ESG. Praca w międzynarodowym zespole nad skalowalnymi rozwiązaniami Big Data.
                </div>
            </div>
        </div>

        <div class="timeline-item">
            <div>
                <div class="job-title">Data Engineer Intern <span class="job-date">02.2024 - 10.2024</span></div>
                <div class="company">Sii Poland</div>
                <div class="job-desc">
                    Wsparcie procesów inżynierii danych, migracje danych i rozwój kompetencji w ekosystemie chmurowym.
                </div>
            </div>
        </div>

        <div class="timeline-item">
            <div>
                <div class="job-title">Junior BI Specialist <span class="job-date">08.2022 - 06.2023</span></div>
                <div class="company">Micro Solutions</div>
                <div class="job-desc">
                    Analiza danych biznesowych, tworzenie raportów i dashboardów wspomagających decyzje biznesowe.
                </div>
            </div>
        </div>
    </section>

    <footer id="kontakt">
        <h2 style="margin-bottom: 20px;">Kontakt</h2>
        <p style="color: var(--text-sec);">Masz projekt wymagający eksperckiej wiedzy z zakresu Databricks?</p>
        <div style="font-size: 1.2rem; margin: 30px 0;">
            <p><i class="fa-solid fa-envelope" style="color: var(--db-primary);"></i> Damian.kedzierski@op.pl</p>
            <p><i class="fa-solid fa-phone" style="color: var(--db-primary);"></i> +48 533 864 722</p>
        </div>
        <div>
            <a href="https://www.linkedin.com/in/damian-kędzierski-3763252ba" target="_blank" style="font-size: 2rem; color: white;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </footer>

</body>
</html>
