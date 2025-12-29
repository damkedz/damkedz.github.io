<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Engineer</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        /* --- DATABRICKS & AZURE THEME (SENIOR LEVEL) --- */
        :root {
            --db-primary: #FF3621; /* Databricks Orange/Red */
            --db-glow: rgba(255, 54, 33, 0.4);
            --azure-blue: #0078D4; /* Microsoft Blue */
            --azure-glow: rgba(0, 120, 212, 0.4);
            --bg-dark: #0b0c0d;      
            --card-bg: rgba(27, 29, 31, 0.85); 
            --text-main: #FFFFFF;
            --text-sec: #9CA3AF;
            --gold: #FFD700; /* Dla statusu Senior/Pro */
        }

        * { box-sizing: border-box; }

        body {
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
            margin: 0;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* TŁO */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
            background: radial-gradient(circle at 50% 10%, #1a0f0f 0%, var(--bg-dark) 70%);
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        
        /* --- NAV --- */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(11, 12, 13, 0.9);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .brand { font-size: 1.5rem; font-weight: 800; letter-spacing: -0.5px; }
        .brand span { color: var(--db-primary); }

        .nav-links { display: flex; gap: 30px; font-size: 0.9rem; font-weight: 500; }
        .nav-links a:hover { color: var(--db-primary); }

        /* --- HERO (SENIOR) --- */
        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        .senior-badge {
            background: rgba(255, 215, 0, 0.1);
            color: var(--gold);
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            margin-bottom: 25px;
            border: 1px solid rgba(255, 215, 0, 0.3);
            text-transform: uppercase;
            letter-spacing: 2px;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.1);
        }

        h1 {
            font-size: 4rem;
            margin: 0 0 20px 0;
            line-height: 1.1;
            font-weight: 800;
            background: linear-gradient(180deg, #fff, #a1a1a1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-subtitle {
            font-size: 1.4rem;
            color: var(--text-sec);
            max-width: 800px;
            margin-bottom: 40px;
        }

        .typewriter {
            font-family: 'Courier New', monospace;
            color: var(--db-primary);
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 40px;
            min-height: 1.5em;
        }

        /* --- SEKCJE --- */
        section { padding: 100px 10%; position: relative; }
        
        .section-header { margin-bottom: 60px; text-align: center; }
        .section-header h2 { font-size: 2.5rem; margin-bottom: 10px; }
        .section-header p { color: var(--text-sec); }
        .divider { width: 60px; height: 4px; background: var(--db-primary); margin: 20px auto; border-radius: 2px; }
        .divider.blue { background: var(--azure-blue); }

        /* --- DATABRICKS GRID (Top Tier) --- */
        .db-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .cert-card {
            background: var(--card-bg);
            padding: 35px;
            border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: 0.3s;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
        
        /* Efekt Pro */
        .cert-card.pro {
            grid-column: 1 / -1; /* Na całą szerokość */
            background: linear-gradient(145deg, rgba(30,10,10,0.9), rgba(20,20,20,0.95));
            border: 1px solid rgba(255, 54, 33, 0.3);
            flex-direction: row;
            align-items: center;
        }
        
        .cert-card.pro .content { flex: 2; padding-right: 20px; }
        .cert-card.pro .icon-box { flex: 1; text-align: center; border-left: 1px solid rgba(255,255,255,0.1); padding-left: 20px;}
        
        @media (max-width: 768px) {
            .cert-card.pro { flex-direction: column; text-align: center; }
            .cert-card.pro .icon-box { border-left: none; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 20px; margin-top: 20px; padding-left: 0;}
        }

        .cert-icon { font-size: 2.5rem; color: var(--db-primary); margin-bottom: 20px; }
        .cert-title { font-size: 1.4rem; font-weight: 700; margin-bottom: 10px; color: #fff; }
        .cert-id { font-size: 0.8rem; color: #666; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 10px; display: block;}
        .cert-desc { font-size: 0.95rem; color: var(--text-sec); }

        /* --- MICROSOFT GRID (Specialist) --- */
        .ms-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 50px;
        }

        .ms-card {
            background: rgba(0, 120, 212, 0.05);
            border: 1px solid rgba(0, 120, 212, 0.2);
            padding: 25px;
            border-radius: 12px;
            transition: transform 0.3s;
        }
        .ms-card:hover { transform: translateY(-5px); border-color: var(--azure-blue); }
        .ms-icon { color: var(--azure-blue); font-size: 2rem; margin-bottom: 15px; }

        /* --- WALL OF KNOWLEDGE (Small Tags) --- */
        .badge-wall {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin-top: 40px;
        }
        
        .mini-badge {
            background: #151515;
            border: 1px solid #333;
            padding: 10px 20px;
            border-radius: 6px;
            font-size: 0.9rem;
            color: #ccc;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .mini-badge span { font-weight: bold; color: #fff; }
        .mini-badge i { color: #555; }
        .mini-badge.gh { border-color: #8e44ad; } 
        .mini-badge.gh i { color: #8e44ad; }

        /* --- EXPERIENCE (Senior Style) --- */
        .exp-item {
            border-left: 2px solid #333;
            padding-left: 40px;
            margin-bottom: 50px;
            position: relative;
        }
        .exp-item::before {
            content: ''; position: absolute; left: -6px; top: 5px;
            width: 10px; height: 10px; background: var(--db-primary); border-radius: 50%;
        }
        .exp-role { font-size: 1.5rem; font-weight: 700; color: white; }
        .exp-company { color: var(--db-primary); font-size: 1.1rem; font-weight: 600; margin: 5px 0; }
        .exp-details { margin-top: 15px; color: var(--text-sec); }
        .exp-details ul { padding-left: 20px; }
        .exp-details li { margin-bottom: 8px; }

        /* --- FOOTER --- */
        footer { padding: 60px 0; background: #000; text-align: center; border-top: 1px solid #222; }

    </style>
</head>
<body>

    <div id="particles-js"></div>

    <header>
        <div class="brand">Damian<span>Kędzierski</span></div>
        <nav class="nav-links">
            <a href="#databricks">Databricks</a>
            <a href="#microsoft">Microsoft & Azure</a>
            <a href="#experience">Doświadczenie</a>
            <a href="#contact">Kontakt</a>
        </nav>
    </header>

    <section class="hero">
        <div class="senior-badge" data-aos="fade-down">Senior Profile</div>
        
        <h1 data-aos="zoom-in" data-aos-duration="1200">
            Senior Databricks <br> Data Engineer
        </h1>
        
        <div class="typewriter">
            <span id="typing-text"></span><span style="animation: blink 1s infinite">|</span>
        </div>

        <p class="hero-subtitle" data-aos="fade-up" data-aos-delay="200">
            Architektura Lakehouse • Optymalizacja kosztów • Mentoring techniczny <br>
            Ponad 15 certyfikacji potwierdzających ekspertyzę w chmurze Azure i ekosystemie Databricks.
        </p>

        <a href="#contact" style="margin-top: 30px; background: var(--db-primary); color: #fff; padding: 15px 40px; border-radius: 50px; font-weight: bold;" data-aos="fade-up" data-aos-delay="400">
            Współpraca
        </a>
    </section>

    <section id="databricks">
        <div class="section-header">
            <h2>Databricks Authority</h2>
            <div class="divider"></div>
            <p>Pełna ścieżka certyfikacyjna: Od Associate do Professional</p>
        </div>

        <div class="db-grid">
            <div class="cert-card pro" data-tilt data-aos="fade-up">
                <div class="content">
                    <span class="cert-id" style="color: var(--db-primary);">Ekspert Poziom</span>
                    <div class="cert-title" style="font-size: 2rem;">Databricks Certified Data Engineer Professional</div>
                    <p class="cert-desc">
                        Potwierdzenie najwyższych kompetencji w projektowaniu zaawansowanych potoków ETL, zarządzaniu wydajnością Spark, 
                        modelowaniu Delta Lake oraz wdrażaniu standardów CI/CD na produkcji.
                    </p>
                </div>
                <div class="icon-box">
                    <i class="fa-solid fa-medal" style="font-size: 5rem; color: var(--db-primary); text-shadow: 0 0 30px var(--db-glow);"></i>
                </div>
            </div>

            <div class="cert-card" data-tilt data-aos="fade-up" data-aos-delay="100">
                <i class="fa-solid fa-brain cert-icon"></i>
                <div class="cert-title">Machine Learning Associate</div>
                <span class="cert-id">Databricks Certified</span>
                <p class="cert-desc">Zarządzanie cyklem życia modeli ML (MLflow), Feature Store oraz deployment modeli w środowisku rozproszonym.</p>
            </div>

            <div class="cert-card" data-tilt data-aos="fade-up" data-aos-delay="200">
                <i class="fa-solid fa-chart-line cert-icon"></i>
                <div class="cert-title">Data Analyst Associate</div>
                <span class="cert-id">Databricks Certified</span>
                <p class="cert-desc">Zaawansowany SQL w Databricks, wizualizacja danych oraz integracja z narzędziami BI.</p>
            </div>

            <div class="cert-card" data-tilt data-aos="fade-up" data-aos-delay="300">
                <i class="fa-solid fa-cube cert-icon"></i>
                <div class="cert-title">Data Engineer Associate</div>
                <span class="cert-id">Databricks Certified</span>
                <p class="cert-desc">Fundamenty architektury Lakehouse i przetwarzania danych z użyciem Apache Spark.</p>
            </div>
        </div>
    </section>

    <section id="microsoft" style="background: #0f1012;">
        <div class="section-header">
            <h2>Microsoft Azure & Specialist Ecosystem</h2>
            <div class="divider blue"></div>
            <p>Zaawansowana administracja bazami danych, inżynieria AI oraz Fabric Analytics</p>
        </div>

        <h3 style="color: var(--text-sec); text-transform: uppercase; font-size: 0.9rem; letter-spacing: 1px;">Expert & Associate Level</h3>
        <div class="ms-grid">
            
            <div class="ms-card" data-aos="zoom-in" data-aos-delay="0">
                <i class="fa-solid fa-database ms-icon"></i>
                <div class="cert-title" style="font-size: 1.1rem;">Azure DB Admin</div>
                <span class="cert-id">DP-300</span>
                <p class="cert-desc">Administracja relacyjnymi bazami danych w Azure.</p>
            </div>

            <div class="ms-card" data-aos="zoom-in" data-aos-delay="100">
                <i class="fa-solid fa-project-diagram ms-icon"></i>
                <div class="cert-title" style="font-size: 1.1rem;">Fabric Engineer</div>
                <span class="cert-id">DP-600</span>
                <p class="cert-desc">Nowoczesna analityka w Microsoft Fabric.</p>
            </div>

            <div class="ms-card" data-aos="zoom-in" data-aos-delay="200">
                <i class="fa-solid fa-leaf ms-icon" style="color: #27ae60;"></i>
                <div class="cert-title" style="font-size: 1.1rem;">Cosmos DB Developer</div>
                <span class="cert-id">DP-420</span>
                <p class="cert-desc">Modelowanie danych NoSQL w skali globalnej.</p>
            </div>

            <div class="ms-card" data-aos="zoom-in" data-aos-delay="300">
                <i class="fa-solid fa-robot ms-icon" style="color: #e84393;"></i>
                <div class="cert-title" style="font-size: 1.1rem;">Azure AI Engineer</div>
                <span class="cert-id">AI-102</span>
                <p class="cert-desc">Tworzenie i wdrażanie rozwiązań AI w chmurze.</p>
            </div>

            <div class="ms-card" data-aos="zoom-in" data-aos-delay="400">
                <i class="fa-solid fa-network-wired ms-icon"></i>
                <div class="cert-title" style="font-size: 1.1rem;">Data Engineering</div>
                <span class="cert-id">DP-700 / DP-203</span>
                <p class="cert-desc">Zaawansowane przetwarzanie danych w Azure.</p>
            </div>
        </div>

        <div style="margin-top: 60px;">
            <h3 style="color: var(--text-sec); text-transform: uppercase; font-size: 0.9rem; letter-spacing: 1px; text-align: center;">Foundation & DevOps Stack</h3>
            <div class="badge-wall" data-aos="fade-up">
                <div class="mini-badge"><span>DP-900</span> Azure Data Fundamentals</div>
                <div class="mini-badge"><span>AZ-900</span> Azure Fundamentals</div>
                <div class="mini-badge"><span>AI-900</span> Azure AI Fundamentals</div>
                <div class="mini-badge gh"><i class="fa-brands fa-github"></i> <span>GH-300</span> Advanced Security</div>
                <div class="mini-badge gh"><i class="fa-brands fa-github"></i> <span>GH-900</span> GitHub Foundations</div>
            </div>
        </div>
    </section>

    <section id="experience">
        <div class="section-header">
            <h2>Doświadczenie Zawodowe</h2>
            <div class="divider"></div>
        </div>

        <div class="exp-item" data-aos="fade-right">
            <div class="exp-role">Data Engineer <span style="font-size: 1rem; color: #666; font-weight: 400;">(10.2024 - Obecnie)</span></div>
            <div class="exp-company">EY (Ernst & Young)</div>
            <div class="exp-details">
                Realizacja strategicznych projektów chmurowych.
                <ul>
                    <li>Projektowanie i implementacja skalowalnych architektur Lakehouse w oparciu o Databricks i Azure.</li>
                    <li>Optymalizacja wydajności zapytań Spark (Performance Tuning) skutkująca redukcją kosztów.</li>
                    <li>Wdrażanie standardów Governance oraz ESG w przetwarzaniu danych.</li>
                </ul>
            </div>
        </div>

        <div class="exp-item" data-aos="fade-right" data-aos-delay="100">
            <div class="exp-role">Data Engineer Intern <span style="font-size: 1rem; color: #666; font-weight: 400;">(02.2024 - 10.2024)</span></div>
            <div class="exp-company">Sii Poland</div>
            <div class="exp-details">
                Aktywne wsparcie procesów inżynierii danych i migracje środowisk Big Data.
            </div>
        </div>

        <div class="exp-item" data-aos="fade-right" data-aos-delay="200">
            <div class="exp-role">Junior BI Specialist <span style="font-size: 1rem; color: #666; font-weight: 400;">(08.2022 - 06.2023)</span></div>
            <div class="exp-company">Micro Solutions</div>
            <div class="exp-details">
                Budowa raportów Business Intelligence i analiza wymagań biznesowych.
            </div>
        </div>
    </section>

    <footer id="contact">
        <h2 style="color: #fff; margin-bottom: 30px;">Let's Connect</h2>
        <div style="font-size: 1.2rem; color: var(--text-sec);">
            <p><i class="fa-solid fa-phone" style="color: var(--db-primary); margin-right: 10px;"></i> +48 533 864 722</p>
            <p><i class="fa-solid fa-envelope" style="color: var(--db-primary); margin-right: 10px;"></i> Damian.kedzierski@op.pl</p>
        </div>
        <div style="margin-top: 30px;">
            <a href="https://www.linkedin.com/in/damian-kędzierski-3763252ba" target="_blank" style="font-size: 2.5rem; color: white; transition: 0.3s;">
                <i class="fa-brands fa-linkedin"></i>
            </a>
        </div>
        <p style="margin-top: 50px; font-size: 0.8rem; opacity: 0.4;">&copy; 2025 Damian Kędzierski. All 15+ Certifications Verified.</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>

    <script>
        AOS.init({ once: true, offset: 50, duration: 800 });

        // Pisanie tekstu
        const textElement = document.getElementById('typing-text');
        const phrases = ["Lakehouse Architecture Specialist", "Azure Cloud Expert", "Performance Tuning & Optimization", "Databricks Pro Certified"];
        let phraseIndex = 0, charIndex = 0, isDeleting = false;

        function typeEffect() {
            const currentPhrase = phrases[phraseIndex];
            textElement.textContent = currentPhrase.substring(0, charIndex + (isDeleting ? -1 : 1));
            charIndex += isDeleting ? -1 : 1;

            let speed = isDeleting ? 30 : 80;
            if (!isDeleting && charIndex === currentPhrase.length) { speed = 2000; isDeleting = true; }
            else if (isDeleting && charIndex === 0) { isDeleting = false; phraseIndex = (phraseIndex + 1) % phrases.length; speed = 500; }
            setTimeout(typeEffect, speed);
        }
        typeEffect();

        // Tło
        particlesJS("particles-js", {
            "particles": {
                "number": { "value": 60 },
                "color": { "value": "#ffffff" },
                "opacity": { "value": 0.1 },
                "size": { "value": 2 },
                "line_linked": { "enable": true, "distance": 150, "color": "#FF3621", "opacity": 0.15, "width": 1 },
                "move": { "enable": true, "speed": 1 }
            }
        });
    </script>
</body>
</html>
