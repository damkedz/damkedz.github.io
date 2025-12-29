<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jan Kowalski - Data Engineer</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* --- USTAWIENIA PODSTAWOWE --- */
        :root {
            --primary-color: #0078d4; /* Azure Blue */
            --secondary-color: #FF3621; /* Databricks Orange Accent */
            --bg-color: #0f172a; /* Ciemne tło (Slate) */
            --card-bg: #1e293b;
            --text-color: #f1f5f9;
            --text-muted: #94a3b8;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        ul { list-style: none; padding: 0; }

        /* --- NAWIGACJA --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 10%;
            background-color: rgba(15, 23, 42, 0.95);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid #334155;
        }

        .logo { font-size: 1.5rem; font-weight: bold; color: var(--primary-color); }
        
        .nav-links a {
            margin-left: 20px;
            color: var(--text-muted);
            font-weight: 500;
        }
        .nav-links a:hover { color: var(--primary-color); }

        /* --- HERO SECTION --- */
        .hero {
            height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(circle at center, #1e293b 0%, #0f172a 100%);
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 10px;
        }

        .hero span { color: var(--primary-color); }
        
        .hero p {
            font-size: 1.2rem;
            color: var(--text-muted);
            max-width: 600px;
            margin-bottom: 30px;
        }

        .btn {
            background-color: var(--primary-color);
            color: white;
            padding: 12px 30px;
            border-radius: 5px;
            font-weight: bold;
            border: 1px solid var(--primary-color);
        }

        .btn:hover { background-color: transparent; }

        /* --- SEKCJE OGÓLNE --- */
        section { padding: 80px 10%; }
        h2 { font-size: 2rem; margin-bottom: 40px; text-align: center; }
        
        /* --- CERTYFIKATY --- */
        .certs-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .cert-card {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 10px;
            border-left: 5px solid var(--primary-color);
            transition: transform 0.3s;
        }

        .cert-card:hover { transform: translateY(-5px); }
        .cert-card.db { border-left-color: var(--secondary-color); } /* Databricks color */

        .cert-card h3 { margin-top: 0; }
        .cert-issuer { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 15px; display: block; }

        /* --- STACK TECHNOLOGICZNY --- */
        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
        }

        .skill-tag {
            background-color: #334155;
            padding: 10px 20px;
            border-radius: 20px;
            font-size: 0.9rem;
        }

        /* --- KONTAKT / STOPKA --- */
        footer {
            background-color: #020617;
            text-align: center;
            padding: 40px 0;
        }

        .social-icons { margin-bottom: 20px; }
        .social-icons a { font-size: 1.5rem; margin: 0 15px; }
        .social-icons a:hover { color: var(--primary-color); }

        /* --- RESPKSYWNOŚĆ --- */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            nav { flex-direction: column; gap: 10px; }
            .nav-links a { margin: 0 10px; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">&lt;JanKowalski /&gt;</div>
        <div class="nav-links">
            <a href="#o-mnie">O mnie</a>
            <a href="#certyfikaty">Certyfikaty</a>
            <a href="#umiejetnosci">Umiejętności</a>
            <a href="#kontakt">Kontakt</a>
        </div>
    </nav>

    <section class="hero">
        <h1>Cześć, jestem <span id="name-placeholder">Jan</span>.</h1>
        <p>Data Engineer specjalizujący się w budowaniu skalowalnych potoków ETL, architekturze Lakehouse oraz chmurze Azure.</p>
        <a href="#kontakt" class="btn">Skontaktuj się ze mną</a>
    </section>

    <section id="o-mnie">
        <h2>O mnie</h2>
        <p style="text-align: center; max-width: 700px; margin: 0 auto; color: var(--text-muted);">
            Jestem inżynierem danych z pasją do przetwarzania Big Data. Na co dzień zajmuję się optymalizacją zapytań Spark, orkiestracją procesów w Azure Data Factory oraz wdrażaniem rozwiązań opartych o Databricks. Stawiam na czysty kod (Python/Scala) i automatyzację CI/CD.
        </p>
    </section>

    <section id="certyfikaty">
        <h2>Certyfikaty</h2>
        <div class="certs-container">
            
            <div class="cert-card db">
                <i class="fa-solid fa-server fa-2x" style="color: var(--secondary-color); margin-bottom: 15px;"></i>
                <h3>Databricks Certified Data Engineer Professional</h3>
                <span class="cert-issuer">Wydane przez: Databricks</span>
                <p>Potwierdzenie zaawansowanych umiejętności w zakresie optymalizacji Apache Spark, Delta Lake oraz zarządzania produkcyjnymi potokami danych.</p>
            </div>

            <div class="cert-card">
                <i class="fa-brands fa-microsoft fa-2x" style="color: var(--primary-color); margin-bottom: 15px;"></i>
                <h3>Azure Data Engineer Associate</h3>
                <span class="cert-issuer">Wydane przez: Microsoft</span>
                <p>Certyfikat (DP-203) obejmujący projektowanie i wdrażanie rozwiązań do przechowywania i przetwarzania danych w chmurze Azure.</p>
            </div>

            <div class="cert-card">
                <i class="fa-solid fa-cloud fa-2x" style="color: #00bcf2; margin-bottom: 15px;"></i>
                <h3>Azure Fundamentals (AZ-900)</h3>
                <span class="cert-issuer">Wydane przez: Microsoft</span>
                <p>Solidne podstawy usług chmurowych, bezpieczeństwa, prywatności i zgodności w ekosystemie Azure.</p>
            </div>

        </div>
    </section>

    <section id="umiejetnosci" style="background-color: #1e293b;">
        <h2>Mój Stack Technologiczny</h2>
        <div class="skills-grid">
            <span class="skill-tag">Python (PySpark)</span>
            <span class="skill-tag">SQL</span>
            <span class="skill-tag">Azure Data Factory</span>
            <span class="skill-tag">Azure Synapse</span>
            <span class="skill-tag">Databricks</span>
            <span class="skill-tag">Delta Lake</span>
            <span class="skill-tag">Git & CI/CD</span>
            <span class="skill-tag">Airflow</span>
            <span class="skill-tag">Docker</span>
        </div>
    </section>

    <footer id="kontakt">
        <h2>Kontakt</h2>
        <p style="color: var(--text-muted); margin-bottom: 30px;">
            Szukasz inżyniera danych do swojego projektu? Napisz do mnie.
        </p>
        <div class="social-icons">
            <a href="https://linkedin.com" target="_blank"><i class="fa-brands fa-linkedin"></i></a>
            <a href="https://github.com" target="_blank"><i class="fa-brands fa-github"></i></a>
            <a href="mailto:twojemail@example.com"><i class="fa-solid fa-envelope"></i></a>
        </div>
        <p style="font-size: 0.8rem; color: #475569;">&copy; 2024 Jan Kowalski. Wszelkie prawa zastrzeżone.</p>
    </footer>

</body>
</html>
