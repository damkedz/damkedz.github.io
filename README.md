<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Databricks Expert</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        /* --- DATABRICKS THEME --- */
        :root {
            --db-primary: #FF3621; /* Databricks Orange/Red */
            --db-glow: rgba(255, 54, 33, 0.6);
            --db-dark: #1B1D1F;    
            --db-bg: #0b0c0d;      /* Jeszcze ciemniejszy dla kontrastu */
            --text-main: #FFFFFF;
            --text-sec: #B0B0B0;
            --card-bg: rgba(36, 38, 40, 0.8); /* Półprzezroczyste karty */
            --azure-blue: #0078D4;
        }

        * { box-sizing: border-box; }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            margin: 0;
            background-color: var(--db-bg);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden; /* Ukryj poziomy pasek przewijania */
        }

        /* TŁO CZĄSTECZKOWE */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1; /* Za treścią */
            background-color: var(--db-bg);
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        
        /* --- HEADER / NAV --- */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(11, 12, 13, 0.8);
            backdrop-filter: blur(15px); /* Efekt szkła */
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .brand { font-size: 1.5rem; font-weight: 800; letter-spacing: -1px; }
        .brand span { color: var(--db-primary); text-shadow: 0 0 15px var(--db-glow); }

        .nav-links { display: flex; gap: 30px; }
        .nav-links a { position: relative; }
        .nav-links a:hover { color: var(--db-primary); }
        .nav-links a::after {
            content: ''; position: absolute; width: 0; height: 2px; bottom: -5px; left: 0;
            background-color: var(--db-primary); transition: 0.3s;
        }
        .nav-links a:hover::after { width: 100%; }

        /* --- HERO SECTION --- */
        .hero {
            min-height: 90vh; /* Prawie cały ekran */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            position: relative;
        }

        .badge-container {
            background: rgba(255, 54, 33, 0.15);
            color: var(--db-primary);
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 30px;
            border: 1px solid rgba(255, 54, 33, 0.4);
            text-transform: uppercase;
            letter-spacing: 2px;
            box-shadow: 0 0 20px rgba(255, 54, 33, 0.2);
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }

        h1 {
            font-size: 4.5rem;
            margin: 0 0 20px 0;
            line-height: 1.1;
            font-weight: 800;
        }

        h1 .highlight {
            background: linear-gradient(90deg, #FF3621, #FF8D4B);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* EFEKT PISANIA */
        .typewriter {
            font-family: 'Courier New', Courier, monospace;
            color: var(--text-sec);
            font-size: 1.5rem;
            height: 30px; /* Rezerwacja miejsca */
            margin-bottom: 40px;
        }
        .cursor {
            display: inline-block;
            width: 3px;
            background-color: var(--db-primary);
            animation: blink 1s infinite;
        }

        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

        .btn-main {
            background: linear-gradient(45deg, var(--db-primary), #d92e1c);
            color: white;
            padding: 16px 45px;
            border-radius: 50px;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 0 30px rgba(255, 54, 33, 0.4);
            transition: 0.3s;
            position: relative;
            overflow: hidden;
            border: none;
            cursor: pointer;
        }
        
        .btn-main:hover { 
            transform: translateY(-3px) scale(1.02); 
            box-shadow: 0 0 50px rgba(255, 54, 33, 0.6); 
        }

        /* --- CERTYFIKATY (GRID) --- */
        .certs-section { padding: 80px 10%; }
        .section-title { text-align: center; font-size: 2.5rem; margin-bottom: 60px; font-weight: 700; position: relative; display: inline-block; left: 50%; transform: translateX(-50%); }
        .section-title::after {
            content: ''; display: block; width: 60px; height: 4px; background: var(--db-primary); margin: 10px auto 0; border-radius: 2px;
        }
        
        .certs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        /* KARTY 3D */
        .cert-card {
            background: var(--card-bg);
            padding: 35px;
            border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.05);
            backdrop-filter: blur(5px);
            transform-style: preserve-3d;
            transform: perspective(1000px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .cert-icon { 
            font-size: 3rem; 
            color: var(--db-primary); 
            margin-bottom: 20px; 
            filter: drop-shadow(0 0 10px rgba(255,54,33,0.5));
        }

        .cert-title { font-size: 1.3rem; font-weight: 700; margin-bottom: 10px; line-height: 1.3; }
        .cert-issuer { font-size: 0.9rem; color: var(--text-sec); display: block; margin-bottom: 15px; text-transform: uppercase; letter-spacing: 1px; }
        
        .cert-card.pro {
            border: 1px solid rgba(255, 54, 33, 0.5);
            background: linear-gradient(160deg, rgba(40,15,15,0.9) 0%, rgba(36,38,40,0.9) 100%);
        }

        /* --- STACK --- */
        .stack-bar {
            background: rgba(255,255,255,0.03);
            padding: 50px 0;
            text-align: center;
            border-top: 1px solid rgba(255,255,255,0.05);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            position: relative;
            z-index: 10;
        }
        .tech-tags { display: flex; justify-content: center; flex-wrap: wrap; gap: 15px; margin-top: 30px; max-width: 1000px; margin-left: auto; margin-right: auto; }
        .tag { 
            background: rgba(255,255,255,0.05); padding: 10px 25px; border-radius: 30px; font-weight: 500; 
            border: 1px solid rgba(255,255,255,0.1); transition: 0.3s; cursor: default;
        }
        .tag:hover { 
            background: var(--db-primary); 
            color: white; 
            box-shadow: 0 0 20px var(--db-glow); 
            border-color: var(--db-primary);
            transform: translateY(-3px);
        }

        /* --- TIMELINE --- */
        .exp-section { padding: 100px 10%; }
        
        .timeline-item {
            display: flex;
            margin-bottom: 50px;
            border-left: 2px solid rgba(255,255,255,0.1);
            padding-left: 40px;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -6px; top: 5px;
            width: 10px; height: 10px;
            background: var(--db-primary);
            border-radius: 50%;
            box-shadow: 0 0 15px var(--db-primary);
        }

        .job-title { font-size: 1.4rem; font-weight: 700; color: white; margin-bottom: 5px; }
        .company { color: var(--db-primary); font-weight: 600; font-size: 1.1rem; }
        .job-date { font-size: 0.9rem; color: #666; margin-left: 10px; font-weight: 400; }
        .job-desc { color: #ccc; margin-top: 15px; font-size: 1.05rem; }

        /* --- FOOTER --- */
        footer { padding: 60px 10%; background: #000; text-align: center; border-top: 1px solid #222; position: relative; z-index: 10;}
        
        @media (max-width: 768px) {
            h1 { font-size: 2.8rem; }
            .nav-links { display: none; }
            .hero { padding-top: 50px; }
        }
    </style>
</head>
<body>

    <div id="particles-js"></div>

    <header>
        <div class="brand">Damian<span>Kędzierski</span></div>
        <nav class="nav-links">
            <a href="#certyfikaty">Certyfikaty</a>
            <a href="#stack">Technologie</a>
            <a href="#doswiadczenie">Doświadczenie</a>
            <a href="#kontakt">Kontakt</a>
        </nav>
    </header>

    <section class="hero">
        <div class="badge-container" data-aos="fade-down" data-aos-delay="100">
            <i class="fa-solid fa-bolt"></i> Certified Databricks Expert
        </div>
        
        <h1 data-aos="zoom-in" data-aos-duration="1000">
            Architektura <br><span class="highlight">Lakehouse</span>
        </h1>
        
        <div class="typewriter">
            <span id="typing-text"></span><span class="cursor">&nbsp;</span>
        </div>

        <a href="#kontakt" class="btn-main" data-aos="fade-up" data-aos-delay="800">
            Skontaktuj się ze mną <i class="fa-solid fa-arrow-right" style="margin-left: 10px;"></i>
        </a>
    </section>

    <section id="certyfikaty" class="certs-section">
        <h2 class="section-title" data-aos="fade-up">Certyfikacja & Kompetencje</h2>
        <div class="certs-grid">
            
            <div class="cert-card pro" data-tilt data-tilt-max="10" data-tilt-speed="400" data-aos="fade-up" data-aos-delay="0">
                <i class="fa-solid fa-layer-group cert-icon"></i>
                <div class="cert-title">Databricks Certified Data Engineer Professional</div>
                <span class="cert-issuer">Databricks</span>
                <p>Ekspercka wiedza w zakresie optymalizacji Spark, Delta Lake i wdrażania produkcyjnych potoków ETL.</p>
            </div>

            <div class="cert-card" data-tilt data-tilt-max="10" data-tilt-speed="400" data-aos="fade-up" data-aos-delay="100">
                <i class="fa-solid fa-cube cert-icon"></i>
                <div class="cert-title">Databricks Certified Data Engineer Associate</div>
                <span class="cert-issuer">Databricks</span>
                <p>Fundamenty architektury Lakehouse i przetwarzania danych z użyciem Apache Spark.</p>
            </div>

            <div class="cert-card" data-tilt data-tilt-max="10" data-tilt-speed="400" data-aos="fade-up" data-aos-delay="200">
                <i class="fa-solid fa-brain cert-icon"></i>
                <div class="cert-title">Databricks Certified Machine Learning</div>
                <span class="cert-issuer">Databricks</span>
                <p>Wdrażanie modeli ML i zarządzanie cyklem życia (MLflow) w środowisku Databricks.</p>
            </div>

            <div class="cert-card" style="border-left: 1px solid var(--azure-blue);" data-tilt data-tilt-max="10" data-aos="fade-up" data-aos-delay="300">
                <i class="fa-brands fa-microsoft cert-icon" style="color: var(--azure-blue);"></i>
                <div class="cert-title">Fabric Analytics Engineer Associate</div>
                <span class="cert-issuer">Microsoft (DP-600)</span>
                <p>Projektowanie i wdrażanie rozwiązań analitycznych w Microsoft Fabric.</p>
            </div>

            <div class="cert-card" style="border-left: 1px solid #fff;" data-tilt data-tilt-max="10" data-aos="fade-up" data-aos-delay="400">
                <i class="fa-solid fa-database cert-icon" style="color: #fff;"></i>
                <div class="cert-title">SQL Associate</div>
                <span class="cert-issuer">Branżowy</span>
                <p>Zaawansowana analityka danych i optymalizacja zapytań SQL.</p>
            </div>

        </div>
    </section>

    <div id="stack" class="stack-bar">
        <h3 style="color: var(--text-sec); margin: 0; text-transform: uppercase; letter-spacing: 2px;" data-aos="fade-in">Tech Stack</h3>
        <div class="tech-tags">
            <span class="tag" data-aos="zoom-in" data-aos-delay="0">Apache Spark</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="50">Delta Lake</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="100">Python (PySpark)</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="150">Databricks SQL</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="200">Unity Catalog</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="250">Azure Data Factory</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="300">Kubernetes</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="350">DBT</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="400">CI/CD (DevOps)</span>
            <span class="tag" data-aos="zoom-in" data-aos-delay="450">Google BigQuery</span>
        </div>
    </div>

    <section id="doswiadczenie" class="exp-section">
        <h2 class="section-title" data-aos="fade-up">Ścieżka Kariery</h2>
        
        <div class="timeline-item" data-aos="fade-right">
            <div>
                <div class="job-title">Data Engineer <span class="job-date">10.2024 - Obecnie</span></div>
                <div class="company">EY (Ernst & Young)</div>
                <div class="job-desc">
                    Realizacja projektów z zakresu chmury i ESG. Budowa skalowalnych potoków danych oraz wdrażanie architektury Lakehouse.
                </div>
            </div>
        </div>

        <div class="timeline-item" data-aos="fade-right" data-aos-delay="100">
            <div>
                <div class="job-title">Data Engineer Intern <span class="job-date">02.2024 - 10.2024</span></div>
                <div class="company">Sii Poland</div>
                <div class="job-desc">
                    Wsparcie procesów inżynierii danych, migracje danych i rozwój kompetencji w ekosystemie chmurowym.
                </div>
            </div>
        </div>

        <div class="timeline-item" data-aos="fade-right" data-aos-delay="200">
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
        <p style="color: var(--text-sec); margin-bottom: 40px;">Porozmawiajmy o danych, chmurze i przyszłości Twoich projektów.</p>
        
        <div style="font-size: 1.2rem; margin-bottom: 30px; display: flex; flex-direction: column; gap: 15px;">
            <a href="mailto:Damian.kedzierski@op.pl" class="tag" style="background: transparent; border-color: var(--db-primary); width: fit-content; margin: 0 auto;">
                <i class="fa-solid fa-envelope" style="margin-right: 10px;"></i> Damian.kedzierski@op.pl
            </a>
            <span style="color: var(--text-sec);">+48 533 864 722</span>
        </div>

        <div>
            <a href="https://www.linkedin.com/in/damian-kędzierski-3763252ba" target="_blank" style="font-size: 2.5rem; color: white; transition: 0.3s;">
                <i class="fa-brands fa-linkedin"></i>
            </a>
        </div>
        <p style="font-size: 0.8rem; margin-top: 50px; opacity: 0.3;">&copy; 2025 Damian Kędzierski. Powered by Databricks Enthusiasm.</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.7.0/vanilla-tilt.min.js"></script>
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>

    <script>
        // 1. Inicjalizacja Animacji Scrollowania (AOS)
        AOS.init({
            once: true, // Animacja tylko raz
            offset: 100, // Start animacji trochę wcześniej
            duration: 800, // Czas trwania
        });

        // 2. Efekt Pisania (Typewriter)
        const textElement = document.getElementById('typing-text');
        const phrases = ["Building Scalable Data Pipelines", "Expert in Databricks & Azure", "Transforming Data into Value"];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeEffect() {
            const currentPhrase = phrases[phraseIndex];
            
            if (isDeleting) {
                textElement.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
            } else {
                textElement.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
            }

            let typeSpeed = isDeleting ? 50 : 100;

            if (!isDeleting && charIndex === currentPhrase.length) {
                typeSpeed = 2000; // Czekaj po napisaniu całego tekstu
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
                typeSpeed = 500;
            }

            setTimeout(typeEffect, typeSpeed);
        }
        // Start pisania
        typeEffect();

        // 3. Tło Cząsteczkowe (Particles.js) - Wygląd "Data Network"
        particlesJS("particles-js", {
            "particles": {
                "number": { "value": 80, "density": { "enable": true, "value_area": 800 } },
                "color": { "value": "#ffffff" },
                "shape": { "type": "circle" },
                "opacity": { "value": 0.1, "random": false },
                "size": { "value": 3, "random": true },
                "line_linked": {
                    "enable": true,
                    "distance": 150,
                    "color": "#FF3621", /* Kolor linii (Databricks Red) */
                    "opacity": 0.2,
                    "width": 1
                },
                "move": { "enable": true, "speed": 2, "direction": "none", "random": false, "out_mode": "out" }
            },
            "interactivity": {
                "detect_on": "canvas",
                "events": {
                    "onhover": { "enable": true, "mode": "grab" }, /* Łapanie myszką */
                    "onclick": { "enable": true, "mode": "push" }
                },
                "modes": { "grab": { "distance": 140, "line_linked": { "opacity": 0.6 } } }
            },
            "retina_detect": true
        });
    </script>
</body>
</html>
