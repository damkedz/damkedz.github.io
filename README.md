<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski - Data Engineer</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #ffe600; /* EY Yellow accent */
            --secondary-color: #00a3e0; /* Microsoft Blue */
            --bg-color: #1a1a1a; /* Dark gray */
            --card-bg: #2d2d2d;
            --text-color: #ffffff;
            --text-muted: #b3b3b3;
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

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 10%;
            background-color: rgba(26, 26, 26, 0.95);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid #404040;
        }

        .logo { font-size: 1.5rem; font-weight: bold; color: var(--primary-color); }
        
        .nav-links a { margin-left: 20px; color: var(--text-muted); font-weight: 500; }
        .nav-links a:hover { color: var(--primary-color); }

        .hero {
            height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(circle at center, #2d2d2d 0%, #1a1a1a 100%);
        }

        .hero h1 { font-size: 3rem; margin-bottom: 10px; }
        .hero span { color: var(--primary-color); }
        .hero p { font-size: 1.2rem; color: var(--text-muted); max-width: 600px; margin-bottom: 30px; }

        .btn {
            background-color: var(--primary-color);
            color: #000;
            padding: 12px 30px;
            border-radius: 5px;
            font-weight: bold;
        }
        .btn:hover { background-color: #e6cf00; }

        section { padding: 60px 10%; }
        h2 { font-size: 2rem; margin-bottom: 40px; text-align: center; border-bottom: 2px solid var(--primary-color); display: inline-block; padding-bottom: 10px; }
        .section-header { text-align: center; width: 100%; margin-bottom: 40px; }

        /* KARTY (Doświadczenie, Edukacja, Certyfikaty) */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .card {
            background-color: var(--card-bg);
            padding: 25px;
            border-radius: 8px;
            border-left: 4px solid var(--primary-color);
            transition: transform 0.3s;
        }
        .card:hover { transform: translateY(-5px); }
        
        .card h3 { margin-top: 0; margin-bottom: 5px; }
        .card-subtitle { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 15px; display: block; font-style: italic; }
        .card-date { float: right; font-size: 0.8rem; color: var(--text-muted); }

        /* UMIEJĘTNOŚCI */
        .skills-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; }
        .skill-tag { background-color: #404040; padding: 8px 16px; border-radius: 20px; font-size: 0.95rem; border: 1px solid #555; }
        .skill-tag:hover { border-color: var(--primary-color); color: var(--primary-color); }

        /* FOOTER */
        footer { background-color: #000; text-align: center; padding: 40px 0; margin-top: 40px; }
        .contact-info p { margin: 5px 0; color: var(--text-muted); }
        .social-icons a { font-size: 1.5rem; margin: 0 15px; color: white; }
        .social-icons a:hover { color: var(--primary-color); }
    </style>
</head>
<body>

    <nav>
        <div class="logo">DK.data</div>
        <div class="nav-links">
            <a href="#doswiadczenie">Doświadczenie</a>
            <a href="#edukacja">Edukacja</a>
            <a href="#certyfikaty">Certyfikaty</a>
            <a href="#kontakt">Kontakt</a>
        </div>
    </nav>

    <section class="hero">
        <h1>Cześć, jestem <span>Damian Kędzierski</span></h1>
        <p>Data Engineer w EY | Specjalista Microsoft Fabric & BigQuery</p>
        <a href="#kontakt" class="btn">Skontaktuj się ze mną</a>
    </section>

    <section id="doswiadczenie">
        <div class="section-header"><h2>Doświadczenie Zawodowe</h2></div>
        <div class="cards-grid">
            <div class="card">
                <h3>Data Engineer</h3>
                <span class="card-subtitle">EY, Wrocław <span class="card-date">10.2024 - Obecnie</span></span>
                <p>Tworzenie wartości długoterminowej poprzez rozwiązania chmurowe i ESG. Praca w środowisku międzynarodowym.</p>
            </div>
            <div class="card">
                <h3>Data Engineer Intern</h3>
                <span class="card-subtitle">Sii Poland, Wrocław <span class="card-date">02.2024 - 10.2024</span></span>
                <p>Wsparcie procesów inżynierii danych i rozwój kompetencji w obszarze Big Data.</p>
            </div>
            <div class="card">
                <h3>Junior BI Specialist</h3>
                <span class="card-subtitle">Micro Solutions <span class="card-date">08.2022 - 06.2023</span></span>
                <p>Analiza danych biznesowych i tworzenie raportów Business Intelligence.</p>
            </div>
        </div>
    </section>

    <section id="edukacja">
        <div class="section-header"><h2>Edukacja</h2></div>
        <div class="cards-grid">
            <div class="card" style="border-left-color: var(--secondary-color);">
                <h3>Magister, Informatyka (AI & ML)</h3>
                <span class="card-subtitle">Uniwersytet WSB Merito Wrocław <span class="card-date">2025 - 2027</span></span>
                <p>Specjalizacja: Sztuczna Inteligencja i Uczenie Maszynowe.</p>
            </div>
            <div class="card" style="border-left-color: var(--secondary-color);">
                <h3>Inżynier, Inżynieria Biznesu</h3>
                <span class="card-subtitle">Politechnika Wrocławska <span class="card-date">2021 - 2025</span></span>
                <p>Zastosowanie IT w biznesie.</p>
            </div>
        </div>
    </section>

    <section id="certyfikaty" style="background-color: #222;">
        <div class="section-header"><h2>Umiejętności i Certyfikaty</h2></div>
        
        <div style="margin-bottom: 40px;">
            <h3 style="text-align: center; color: var(--text-muted); margin-bottom: 20px;">Stack Technologiczny</h3>
            <div class="skills-container">
                <span class="skill-tag">Google BigQuery</span>
                <span class="skill-tag">Kubernetes</span>
                <span class="skill-tag">DBT (Data Build Tool)</span>
                <span class="skill-tag">SQL</span>
                <span class="skill-tag">Microsoft Fabric</span>
                <span class="skill-tag">Cloud Engineering</span>
            </div>
        </div>

        <div class="cards-grid">
            <div class="card">
                <i class="fa-brands fa-microsoft fa-2x" style="color: var(--secondary-color); margin-bottom: 10px;"></i>
                <h3>Fabric Analytics Engineer Assoc.</h3>
                <span class="card-subtitle">Microsoft Certified</span>
            </div>
            <div class="card">
                <i class="fa-solid fa-database fa-2x" style="color: #fff; margin-bottom: 10px;"></i>
                <h3>SQL Associate</h3>
                <span class="card-subtitle">Certyfikat branżowy</span>
            </div>
            <div class="card">
                <i class="fa-solid fa-leaf fa-2x" style="color: #00ff88; margin-bottom: 10px;"></i>
                <h3>EY Sustainability (ESG)</h3>
                <span class="card-subtitle">Bronze Learning</span>
            </div>
        </div>
    </section>

    <footer id="kontakt">
        <h2>Kontakt</h2>
        <div class="contact-info">
            <p><i class="fa-solid fa-phone"></i> +48 533 864 722</p>
            <p><i class="fa-solid fa-envelope"></i> Damian.kedzierski@op.pl</p>
        </div>
        <div class="social-icons" style="margin-top: 20px;">
            <a href="https://www.linkedin.com/in/damian-kędzierski-3763252ba" target="_blank"><i class="fa-brands fa-linkedin"></i></a>
        </div>
        <p style="font-size: 0.8rem; margin-top: 30px; opacity: 0.5;">&copy; 2025 Damian Kędzierski</p>
    </footer>

</body>
</html>
