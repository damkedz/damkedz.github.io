<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Engineer</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            --bg-core: #050505;
            --text-primary: #ffffff;
            --text-secondary: #94a3b8;
            
            /* BRAND COLORS */
            --brand-db: #FF3621;      /* Databricks Red */
            --brand-ms: #0078D4;      /* Azure Blue */
            --brand-spark: #E25A1C;   /* Spark Orange */
            --brand-ai: #9D28AC;      /* AI Purple */
            --brand-gh: #ffffff;      /* GitHub White */

            /* UI VARS */
            --glass: rgba(20, 20, 20, 0.6);
            --border: rgba(255, 255, 255, 0.1);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-core);
            color: var(--text-primary);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- VIDEO BACKGROUND --- */
        .video-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            z-index: -2;
        }
        .video-bg video {
            width: 100%; height: 100%; object-fit: cover; opacity: 0.3;
            filter: hue-rotate(340deg) contrast(1.1); /* Lekko czerwony odcień pod Databricks */
        }
        .overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circleAt center, transparent 0%, #050505 100%);
            z-index: -1;
        }

        /* --- NAVIGATION --- */
        nav {
            position: fixed; top: 0; width: 100%; z-index: 1000;
            padding: 20px 5%; display: flex; justify-content: space-between; align-items: center;
            background: rgba(5, 5, 5, 0.85); backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
        }
        .logo { font-family: 'JetBrains Mono', monospace; font-weight: 700; font-size: 1.2rem; }
        .logo span { color: var(--brand-db); }

        .nav-items a {
            color: var(--text-secondary); text-decoration: none; margin-left: 30px;
            font-size: 0.85rem; font-weight: 600; text-transform: uppercase; letter-spacing: 1px; transition: 0.3s;
        }
        .nav-items a:hover { color: #fff; }

        /* --- HERO --- */
        .hero {
            height: 95vh; display: flex; flex-direction: column; justify-content: center; padding: 0 10%;
        }
        
        .pill {
            display: inline-flex; align-items: center; gap: 10px;
            padding: 8px 16px; border-radius: 50px;
            background: rgba(255, 54, 33, 0.1); border: 1px solid rgba(255, 54, 33, 0.3);
            color: var(--brand-db); font-family: 'JetBrains Mono'; font-size: 0.8rem;
            margin-bottom: 30px; width: fit-content;
        }

        h1 {
            font-size: 5.5rem; line-height: 1; font-weight: 800; letter-spacing: -2px;
            margin-bottom: 25px;
            background: linear-gradient(180deg, #fff 0%, #aaa 100%);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }

        .hero-desc {
            max-width: 650px; font-size: 1.25rem; color: #ccc; font-weight: 300;
            border-left: 4px solid var(--brand-db); padding-left: 25px;
        }

        /* --- MEDALLION ARCHITECTURE VISUAL (CSS GRAPHIC) --- */
        .medallion-section {
            padding: 60px 10%;
            background: linear-gradient(180deg, rgba(0,0,0,0) 0%, rgba(255, 54, 33, 0.05) 50%, rgba(0,0,0,0) 100%);
            text-align: center;
        }
        .medallion-container {
            display: flex; justify-content: center; align-items: center; gap: 20px; flex-wrap: wrap; margin-top: 40px;
        }
        .layer-card {
            background: rgba(0,0,0,0.6); border: 1px solid var(--border);
            padding: 20px; width: 220px; border-radius: 12px; position: relative;
            transition: 0.3s;
        }
        .layer-card:hover { transform: translateY(-5px); border-color: var(--brand-db); }
        .layer-icon { font-size: 2rem; margin-bottom: 10px; display: block; }
        .layer-title { font-weight: 700; display: block; margin-bottom: 5px; color: #fff; }
        .layer-desc { font-size: 0.8rem; color: #888; }
        
        .arrow { font-size: 1.5rem; color: #555; }
        
        /* Specific Layer Colors */
        .bronze i { color: #CD7F32; } .bronze { border-top: 3px solid #CD7F32; }
        .silver i { color: #C0C0C0; } .silver { border-top: 3px solid #C0C0C0; }
        .gold i { color: #FFD700; }   .gold { border-top: 3px solid #FFD700; }


        /* --- MAIN GRID --- */
        section { padding: 100px 8%; }
        .section-title { font-size: 2.5rem; margin-bottom: 50px; font-weight: 700; display: flex; align-items: center; gap: 15px; }
        
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; }
        @media(max-width: 900px) { .grid-2 { grid-template-columns: 1fr; } }

        .zone {
            background: var(--glass); border: 1px solid var(--border); border-radius: 20px;
            padding: 40px; position: relative; overflow: hidden;
        }

        /* Databricks Zone */
        .db-zone { border-top: 5px solid var(--brand-db); }
        .db-logo-svg { width: 40px; fill: var(--brand-db); margin-bottom: 20px; }
        
        /* Microsoft Zone */
        .ms-zone { border-top: 5px solid var(--brand-ms); }
        
        .card-item {
            background: rgba(255,255,255,0.03); border: 1px solid var(--border);
            padding: 20px; border-radius: 10px; margin-bottom: 15px;
            transition: 0.3s; display: flex; justify-content: space-between; align-items: center;
        }
        .card-item:hover { background: rgba(255,255,255,0.08); transform: translateX(5px); }
        
        .card-content h4 { color: #fff; font-size: 1.1rem; margin-bottom: 5px; }
        .card-content span { font-size: 0.8rem; color: #888; font-family: 'JetBrains Mono'; }
        
        .badge { 
            font-size: 0.7rem; font-weight: 700; text-transform: uppercase; 
            padding: 5px 10px; border-radius: 4px; color: #fff; 
        }

        /* --- GITHUB / AI --- */
        .ai-section { margin-top: 40px; display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .ai-card {
            background: linear-gradient(135deg, rgba(157,40,172,0.1) 0%, rgba(0,0,0,0) 100%);
            border: 1px solid rgba(157,40,172,0.3); padding: 30px; border-radius: 16px;
        }

        /* --- EXPERIENCE --- */
        .timeline { border-left: 2px solid #333; margin-left: 20px; padding-left: 40px; }
        .job { position: relative; margin-bottom: 60px; }
        .job::before {
            content: ''; position: absolute; left: -47px; top: 5px; width: 12px; height: 12px;
            background: var(--brand-db); border-radius: 50%; box-shadow: 0 0 15px var(--brand-db);
        }
        .job-role { font-size: 1.6rem; font-weight: 700; color: #fff; }
        .job-company { color: var(--brand-db); font-family: 'JetBrains Mono'; margin: 5px 0 15px 0; display: block; }

        footer { padding: 80px 0; background: #020202; text-align: center; border-top: 1px solid #222; }

    </style>
</head>
<body>

    <div class="video-bg">
        <video autoplay muted loop playsinline poster="https://images.pexels.com/photos/17483873/pexels-photo-17483873.jpeg">
            <source src="https://videos.pexels.com/video-files/3129671/3129671-hd_1920_1080_30fps.mp4" type="video/mp4">
        </video>
    </div>
    <div class="overlay"></div>

    <nav>
        <div class="logo">DAMIAN <span>KĘDZIERSKI</span></div>
        <div class="nav-items">
            <a href="#lakehouse">Lakehouse</a>
            <a href="#ecosystem">Stack</a>
            <a href="#experience">Experience</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <section class="hero">
        <div class="pill" data-aos="fade-down">
            <i class="fa-solid fa-code"></i> SENIOR DATA ENGINEER
        </div>
        <h1 data-aos="fade-up">
            Building Scalable <br>
            <span style="color: var(--brand-db);">Data Platforms.</span>
        </h1>
        <div class="hero-desc" data-aos="fade-up" data-aos-delay="200">
            Specialized in <strong>Databricks Lakehouse</strong> architecture, Spark optimization, and Azure cloud infrastructure. 
            Transforming raw signals into high-quality data products.
        </div>
    </section>

    <div class="medallion-section" id="lakehouse">
        <p style="font-family: 'JetBrains Mono'; color: #888; text-transform: uppercase; letter-spacing: 2px;">My Engineering Philosophy</p>
        <h2 style="font-size: 2rem; color: #fff; margin-bottom: 20px;">The Medallion Architecture</h2>
        
        <div class="medallion-container" data-aos="zoom-in">
            <div class="layer-card bronze">
                <i class="fa-solid fa-database layer-icon"></i>
                <span class="layer-title">BRONZE</span>
                <span class="layer-desc">Raw Ingestion<br>(Parquet/Delta)</span>
            </div>
            
            <i class="fa-solid fa-arrow-right arrow"></i>
            
            <div class="layer-card silver">
                <i class="fa-solid fa-filter layer-icon"></i>
                <span class="layer-title">SILVER</span>
                <span class="layer-desc">Cleaned & Conformed<br>(Filtered, Augmented)</span>
            </div>

            <i class="fa-solid fa-arrow-right arrow"></i>

            <div class="layer-card gold">
                <i class="fa-solid fa-chart-pie layer-icon"></i>
                <span class="layer-title">GOLD</span>
                <span class="layer-desc">Business Aggregates<br>(Power BI Ready)</span>
            </div>
        </div>
    </div>

    <section id="ecosystem">
        <div class="section-title">Technical Stack</div>
        
        <div class="grid-2">
            
            <div class="zone db-zone" data-aos="fade-right">
                <svg class="db-logo-svg" viewBox="0 0 448 512"><path d="M0 216C0 149.7 53.7 96 120 96h8c17.7 0 32 14.3 32 32s-14.3 32-32 32h-8c-30.9 0-56 25.1-56 56v8h64c35.3 0 64 28.7 64 64v64c0 35.3-28.7 64-64 64H64c-35.3 0-64-28.7-64-64V216zm256 0c0-66.3 53.7-120 120-120h8c17.7 0 32 14.3 32 32s-14.3 32-32 32h-8c-30.9 0-56 25.1-56 56v8h64c35.3 0 64 28.7 64 64v64c0 35.3-28.7 64-64 64h-64c-35.3 0-64-28.7-64-64V216z"/></svg>
                <h3 style="color: var(--brand-db); margin-bottom: 30px;">Databricks Ecosystem</h3>

                <div class="card-item" style="border-left: 3px solid var(--brand-db);">
                    <div class="card-content">
                        <h4>Certified Professional</h4>
                        <span>Data Engineer Expert</span>
                    </div>
                    <span class="badge" style="background: var(--brand-db);">PRO</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Generative AI Associate</h4>
                        <span>LLM & RAG Systems</span>
                    </div>
                    <span class="badge" style="background: var(--brand-ai);">AI</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Apache Spark Developer</h4>
                        <span>Internal Tuning & Optimization</span>
                    </div>
                    <span class="badge" style="background: var(--brand-spark);">CORE</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Associate Stack</h4>
                        <span>DE / DA / ML Certificates</span>
                    </div>
                    <span class="badge" style="background: #333;">FOUNDATION</span>
                </div>
            </div>

            <div class="zone ms-zone" data-aos="fade-left">
                <i class="fa-brands fa-microsoft" style="font-size: 2.5rem; color: var(--brand-ms); margin-bottom: 20px;"></i>
                <h3 style="color: var(--brand-ms); margin-bottom: 30px;">Azure Ecosystem</h3>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Fabric Analytics Engineer</h4>
                        <span>DP-600 | OneLake & Synapse</span>
                    </div>
                    <span class="badge" style="background: var(--brand-ms);">NEW</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Azure AI Engineer</h4>
                        <span>AI-102 | Cognitive Services</span>
                    </div>
                    <span class="badge" style="background: var(--brand-ms);">AI</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Azure DB Administrator</h4>
                        <span>DP-300 | SQL Performance</span>
                    </div>
                    <span class="badge" style="background: var(--brand-ms);">DBA</span>
                </div>

                <div class="card-item">
                    <div class="card-content">
                        <h4>Azure Infrastructure</h4>
                        <span>DP-203 / DP-420 / PL-300</span>
                    </div>
                    <span class="badge" style="background: var(--brand-ms);">CORE</span>
                </div>
            </div>
        </div>

        <div class="ai-section" id="ai">
            <div class="ai-card" data-aos="fade-up">
                <i class="fa-brands fa-github" style="font-size: 2rem; color: #fff; margin-bottom: 15px;"></i>
                <h4>GitHub Copilot (GH-300)</h4>
                <p style="font-size: 0.9rem; color: #ccc;">Using AI Pair Programming to accelerate code delivery and refactoring.</p>
            </div>
            <div class="ai-card" data-aos="fade-up" data-aos-delay="100">
                <i class="fa-solid fa-shield-halved" style="font-size: 2rem; color: #fff; margin-bottom: 15px;"></i>
                <h4>GitHub Advanced Security</h4>
                <p style="font-size: 0.9rem; color: #ccc;">Ensuring code integrity and secret scanning in CI/CD pipelines.</p>
            </div>
        </div>
    </section>

    <section id="experience">
        <div class="section-title">Experience</div>
        
        <div class="timeline">
            <div class="job" data-aos="fade-up">
                <div class="job-role">Data Engineer</div>
                <span class="job-company">EY (Ernst & Young) | Oct 2024 - Present</span>
                <p style="color: #bbb; max-width: 800px;">
                    Designing enterprise-scale <strong>Lakehouse Architectures</strong>. 
                    Implementing Data Governance with <strong>Unity Catalog</strong> and reducing cloud costs via FinOps Spark tuning.
                </p>
            </div>

            <div class="job" data-aos="fade-up">
                <div class="job-role">Data Engineer Intern</div>
                <span class="job-company">Sii Poland | Feb 2024 - Oct 2024</span>
                <p style="color: #bbb; max-width: 800px;">
                    Developed ETL pipelines in <strong>Azure Data Factory</strong> and Databricks. 
                    Migrated on-premise data to Azure Data Lake Storage Gen2.
                </p>
            </div>

            <div class="job" data-aos="fade-up">
                <div class="job-role">Junior BI Specialist</div>
                <span class="job-company">Micro Solutions | Aug 2022 - Jun 2023</span>
                <p style="color: #bbb; max-width: 800px;">
                    Built BI solutions using <strong>Power BI</strong> (PL-300 certified). 
                    Designed data models and DAX measures for business reporting.
                </p>
            </div>
        </div>
    </section>

    <footer id="contact">
        <h2 style="color: #fff; margin-bottom: 20px;">Damian Kędzierski</h2>
        <a href="mailto:Damian.kedzierski@op.pl" style="color: #fff; text-decoration: none; font-size: 1.2rem;">Damian.kedzierski@op.pl</a>
        <div style="margin-top: 30px; font-size: 2rem;">
            <a href="https://linkedin.com" target="_blank" style="color: #fff;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
        <p style="margin-top: 30px; font-size: 0.8rem; opacity: 0.5;">&copy; 2025 Senior Data Engineer Portfolio</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({ once: true, offset: 50, duration: 800 });
    </script>
</body>
</html>
