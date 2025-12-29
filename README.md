<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Architect</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
    
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            /* COLOR PALETTE */
            --bg-core: #030304;
            --text-primary: #ffffff;
            --text-secondary: #94a3b8;
            
            /* BRAND ACCENTS */
            --brand-db: #FF3621;      /* Databricks Red */
            --brand-ms: #00A4EF;      /* Azure Blue */
            --brand-ai: #D256E1;      /* Gen AI Purple */
            --brand-gh: #F778BA;      /* Copilot Accent */

            /* UI ELEMENTS */
            --glass-surface: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
            --blur: blur(20px);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-core);
            color: var(--text-primary);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- CINEMATIC BACKGROUND --- */
        .cinematic-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            z-index: -2; overflow: hidden;
        }
        .cinematic-bg video {
            width: 100%; height: 100%; object-fit: cover; opacity: 0.25;
            filter: grayscale(100%) contrast(1.2);
        }
        .overlay-gradient {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at 50% 50%, transparent 0%, var(--bg-core) 90%);
            z-index: -1;
        }

        /* --- NAVIGATION --- */
        nav {
            position: fixed; top: 0; width: 100%; z-index: 1000;
            padding: 20px 5%;
            display: flex; justify-content: space-between; align-items: center;
            background: rgba(3, 3, 4, 0.8);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--glass-border);
        }
        .logo { font-family: 'JetBrains Mono', monospace; font-weight: 700; font-size: 1.2rem; letter-spacing: -1px; }
        .logo span { color: var(--brand-db); }

        .nav-items a {
            color: var(--text-secondary); text-decoration: none; margin-left: 30px;
            font-size: 0.9rem; font-weight: 500; transition: 0.3s; text-transform: uppercase; letter-spacing: 1px;
        }
        .nav-items a:hover { color: #fff; text-shadow: 0 0 10px rgba(255,255,255,0.5); }

        /* --- HERO SECTION --- */
        .hero {
            height: 100vh;
            display: flex; flex-direction: column; justify-content: center; align-items: flex-start;
            padding: 0 10%;
        }
        
        .status-pill {
            padding: 6px 16px; border-radius: 50px;
            background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1);
            font-size: 0.8rem; font-family: 'JetBrains Mono'; color: var(--brand-db);
            margin-bottom: 25px; display: inline-block;
        }

        h1 {
            font-size: 5rem; line-height: 1.05; font-weight: 800; letter-spacing: -2px;
            background: linear-gradient(180deg, #fff 0%, #a1a1aa 100%);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            margin-bottom: 30px;
        }

        .hero-desc {
            max-width: 600px; color: var(--text-secondary); font-size: 1.2rem; font-weight: 300;
            border-left: 3px solid var(--brand-db); padding-left: 20px;
        }

        /* --- SECTIONS LAYOUT --- */
        section { padding: 100px 8%; position: relative; }
        .section-header { margin-bottom: 60px; }
        .section-header h2 { font-size: 3rem; font-weight: 700; letter-spacing: -1px; margin-bottom: 10px; }
        .section-header p { color: var(--text-secondary); font-family: 'JetBrains Mono'; font-size: 0.9rem; }

        /* --- DUAL ECOSYSTEM GRID (The Core) --- */
        .ecosystem-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }
        @media (max-width: 900px) { .ecosystem-container { grid-template-columns: 1fr; } }

        .ecosystem-col {
            background: var(--glass-surface);
            border: 1px solid var(--glass-border);
            border-radius: 24px;
            padding: 40px;
            position: relative;
            overflow: hidden;
        }

        /* Column Specifics */
        .col-db { border-top: 4px solid var(--brand-db); }
        .col-ms { border-top: 4px solid var(--brand-ms); }

        .col-title {
            font-size: 1.8rem; font-weight: 700; margin-bottom: 30px; display: flex; align-items: center; gap: 15px;
        }
        .col-db .col-title { color: var(--brand-db); }
        .col-ms .col-title { color: var(--brand-ms); }

        /* --- TECH CARDS --- */
        .tech-card {
            background: rgba(0,0,0,0.2);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 20px;
            transition: 0.3s;
        }
        .tech-card:hover { background: rgba(255,255,255,0.05); transform: translateX(5px); }

        .card-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; }
        .card-head h4 { font-size: 1.1rem; color: #fff; font-weight: 600; }
        .card-badge { 
            font-size: 0.7rem; font-weight: 700; text-transform: uppercase; padding: 4px 10px; border-radius: 4px;
        }
        
        .badge-pro { background: rgba(255, 54, 33, 0.15); color: var(--brand-db); }
        .badge-ai { background: rgba(210, 86, 225, 0.15); color: var(--brand-ai); }
        .badge-ms { background: rgba(0, 164, 239, 0.15); color: var(--brand-ms); }

        .tech-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 15px; }
        .tag {
            font-size: 0.75rem; color: var(--text-secondary); background: rgba(255,255,255,0.05);
            padding: 4px 10px; border-radius: 4px; border: 1px solid transparent; font-family: 'JetBrains Mono';
        }
        .tech-card:hover .tag { border-color: rgba(255,255,255,0.1); color: #fff; }

        /* --- GITHUB COPILOT SECTION --- */
        .gh-section {
            background: linear-gradient(90deg, rgba(157,40,172,0.05) 0%, rgba(3,3,4,0) 100%);
            border: 1px solid rgba(157,40,172,0.2);
            border-radius: 24px; padding: 40px; margin-top: 40px;
            display: flex; align-items: center; justify-content: space-between;
        }
        @media(max-width: 768px) { .gh-section { flex-direction: column; text-align: center; gap: 20px; } }

        /* --- EXPERIENCE TIMELINE --- */
        .timeline { position: relative; border-left: 2px solid var(--glass-border); margin-left: 20px; }
        .timeline-item { position: relative; padding-left: 40px; margin-bottom: 50px; }
        .timeline-item::before {
            content: ''; position: absolute; left: -6px; top: 8px; width: 10px; height: 10px;
            background: var(--brand-db); border-radius: 50%; box-shadow: 0 0 10px var(--brand-db);
        }
        
        .role-title { font-size: 1.5rem; font-weight: 700; color: #fff; }
        .company-name { 
            font-family: 'JetBrains Mono'; font-size: 0.9rem; color: var(--text-secondary); 
            margin: 5px 0 15px 0; display: block; 
        }
        .job-desc { color: #bbb; max-width: 800px; font-weight: 300; }
        .job-desc strong { color: #fff; font-weight: 600; }

        /* --- FOOTER --- */
        footer { padding: 80px 0; background: #000; text-align: center; border-top: 1px solid var(--glass-border); }
        .social-link { font-size: 2rem; color: #fff; transition: 0.3s; display: inline-block; margin-top: 20px; }
        .social-link:hover { color: var(--brand-db); transform: scale(1.1); }

    </style>
</head>
<body>

    <div class="cinematic-bg">
        <video autoplay muted loop playsinline poster="https://images.pexels.com/photos/17483873/pexels-photo-17483873.jpeg">
            <source src="https://videos.pexels.com/video-files/3129671/3129671-hd_1920_1080_30fps.mp4" type="video/mp4">
        </video>
    </div>
    <div class="overlay-gradient"></div>

    <nav>
        <div class="logo">DAMIAN <span>KĘDZIERSKI</span></div>
        <div class="nav-items">
            <a href="#ecosystem">Tech Stack</a>
            <a href="#experience">Career</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <section class="hero">
        <div class="status-pill" data-aos="fade-down">Available for Senior Roles</div>
        <h1 data-aos="fade-up" data-aos-delay="100">
            Architecting the <br>
            Future of Data.
        </h1>
        <div class="hero-desc" data-aos="fade-up" data-aos-delay="200">
            Senior Data Engineer specializing in <strong>Lakehouse Architecture</strong> and <strong>Cost Optimization</strong>. 
            Bridging the gap between robust Engineering and Generative AI.
        </div>
    </section>

    <section id="ecosystem">
        <div class="section-header">
            <h2>Technical Expertise</h2>
            <p>// CERTIFIED PROFESSIONAL • MULTI-CLOUD ARCHITECT</p>
        </div>

        <div class="ecosystem-container">
            
            <div class="ecosystem-col col-db" data-aos="fade-right">
                <div class="col-title">
                    <i class="fa-solid fa-layer-group"></i> Databricks Ecosystem
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Certified Professional</h4>
                        <span class="card-badge badge-pro">Expert Level</span>
                    </div>
                    <p style="font-size: 0.9rem; color: #ccc;">Advanced Lakehouse implementations focusing on performance and governance.</p>
                    <div class="tech-tags">
                        <span class="tag">Liquid Clustering</span>
                        <span class="tag">Unity Catalog</span>
                        <span class="tag">Delta Live Tables</span>
                        <span class="tag">FinOps Tuning</span>
                    </div>
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Generative AI Associate</h4>
                        <span class="card-badge badge-ai">AI Specialist</span>
                    </div>
                    <p style="font-size: 0.9rem; color: #ccc;">Building LLM-powered applications using the Databricks Intelligence Platform.</p>
                    <div class="tech-tags">
                        <span class="tag">RAG Architecture</span>
                        <span class="tag">Vector Search</span>
                        <span class="tag">Model Serving</span>
                        <span class="tag">LangChain</span>
                    </div>
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Apache Spark Developer</h4>
                        <span class="card-badge badge-pro">Core Engine</span>
                    </div>
                    <div class="tech-tags">
                        <span class="tag">Catalyst Optimizer</span>
                        <span class="tag">Structured Streaming</span>
                        <span class="tag">Adaptive Query Execution</span>
                    </div>
                </div>

                 <div class="tech-card">
                    <div class="card-head">
                        <h4>Associate Certifications</h4>
                        <span class="card-badge" style="background: #333; color: #fff;">Foundation</span>
                    </div>
                    <div class="tech-tags">
                        <span class="tag">Data Engineer Assoc</span>
                        <span class="tag">Data Analyst Assoc</span>
                        <span class="tag">ML Associate</span>
                    </div>
                </div>

            </div>

            <div class="ecosystem-col col-ms" data-aos="fade-left">
                <div class="col-title">
                    <i class="fa-brands fa-microsoft"></i> Azure Ecosystem
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Fabric Analytics Engineer</h4>
                        <span class="card-badge badge-ms">DP-600</span>
                    </div>
                    <p style="font-size: 0.9rem; color: #ccc;">End-to-end analytics using Microsoft Fabric and OneLake.</p>
                    <div class="tech-tags">
                        <span class="tag">Synapse Engineering</span>
                        <span class="tag">Direct Lake</span>
                        <span class="tag">Power BI Integration</span>
                    </div>
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Azure AI Engineer</h4>
                        <span class="card-badge badge-ms">AI-102</span>
                    </div>
                    <div class="tech-tags">
                        <span class="tag">Cognitive Services</span>
                        <span class="tag">Azure OpenAI</span>
                        <span class="tag">Bot Framework</span>
                    </div>
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Database Specialist</h4>
                        <span class="card-badge badge-ms">DP-300 & DP-420</span>
                    </div>
                    <div class="tech-tags">
                        <span class="tag">SQL Server Tuning</span>
                        <span class="tag">Cosmos DB</span>
                        <span class="tag">NoSQL Modeling</span>
                    </div>
                </div>

                <div class="tech-card">
                    <div class="card-head">
                        <h4>Core Infrastructure</h4>
                        <span class="card-badge badge-ms">Full Stack</span>
                    </div>
                    <div class="tech-tags">
                        <span class="tag">PL-300 (Power BI)</span>
                        <span class="tag">DP-203 (Data Eng)</span>
                        <span class="tag">AZ-900 / DP-900 / AI-900</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="gh-section" data-aos="fade-up">
            <div>
                <h3 style="font-size: 1.5rem; font-weight: 700; color: #fff; margin-bottom: 5px;">
                    <i class="fa-brands fa-github" style="margin-right: 10px;"></i> AI-Augmented Engineering
                </h3>
                <p style="color: var(--text-secondary); max-width: 600px;">
                    Leveraging <strong>GitHub Copilot (GH-300)</strong> for accelerated development cycles and <strong>GitHub Advanced Security</strong> for code integrity.
                </p>
            </div>
            <div style="display: flex; gap: 10px;">
                <span class="tag" style="border-color: var(--brand-gh); color: #fff;">GH-300 Copilot Expert</span>
                <span class="tag" style="border-color: #fff; color: #fff;">GH-900 Foundations</span>
            </div>
        </div>
    </section>

    <section id="experience">
        <div class="section-header">
            <h2>Professional Journey</h2>
            <p>// SCALABLE ARCHITECTURES • ENTERPRISE SOLUTIONS</p>
        </div>

        <div class="timeline">
            <div class="timeline-item" data-aos="fade-up">
                <div class="role-title">Data Engineer</div>
                <span class="company-name">EY (Ernst & Young) | Oct 2024 - Present</span>
                <div class="job-desc">
                    Designing and implementing scalable <strong>Lakehouse Architectures</strong> for enterprise clients. 
                    Focusing on <strong>FinOps</strong> (cloud cost reduction) through Spark optimization and implementing Data Governance via <strong>Unity Catalog</strong>.
                </div>
            </div>

            <div class="timeline-item" data-aos="fade-up" data-aos-delay="100">
                <div class="role-title">Data Engineer Intern</div>
                <span class="company-name">Sii Poland | Feb 2024 - Oct 2024</span>
                <div class="job-desc">
                    Executed complex data migrations and built robust ETL pipelines using <strong>Azure Data Factory</strong> and Databricks. 
                    Automated data ingestion processes from various sources (API, SQL).
                </div>
            </div>

            <div class="timeline-item" data-aos="fade-up" data-aos-delay="200">
                <div class="role-title">Junior BI Specialist</div>
                <span class="company-name">Micro Solutions | Aug 2022 - Jun 2023</span>
                <div class="job-desc">
                    Delivered business intelligence solutions using <strong>Power BI</strong> (PL-300 certified). 
                    Performed data modeling and advanced DAX/SQL querying for actionable insights.
                </div>
            </div>
        </div>
    </section>

    <footer id="contact">
        <h2 style="font-size: 2.5rem; margin-bottom: 20px;">Let's Talk Data.</h2>
        <p style="color: var(--text-secondary); margin-bottom: 30px;">Damian Kędzierski | Senior Data Architect</p>
        
        <a href="mailto:Damian.kedzierski@op.pl" style="color: #fff; text-decoration: none; border: 1px solid rgba(255,255,255,0.2); padding: 15px 30px; border-radius: 50px; transition: 0.3s;">
            Damian.kedzierski@op.pl
        </a>
        
        <div style="margin-top: 40px;">
            <a href="https://linkedin.com" target="_blank" class="social-link"><i class="fa-brands fa-linkedin"></i></a>
        </div>
        <p style="margin-top: 40px; font-size: 0.8rem; color: #444;">&copy; 2025 Damian Kędzierski. Crafted with Code.</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({
            once: true,
            offset: 50,
            duration: 800,
            easing: 'ease-out-cubic'
        });
    </script>
</body>
</html>
