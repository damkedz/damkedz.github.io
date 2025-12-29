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
            --bg-core: #0b0c10;
            --text-primary: #ffffff;
            --brand-db: #FF3621;
            --brand-ms: #0078D4;
            --notebook-bg: #1e1e1e;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background: var(--bg-core); color: #fff; font-family: 'Outfit', sans-serif; overflow-x: hidden; }

        /* --- VIDEO BACKGROUND --- */
        .video-bg { position: fixed; top: 0; left: 0; width: 100%; height: 100vh; z-index: -2; opacity: 0.3; }
        .video-bg video { width: 100%; height: 100%; object-fit: cover; }
        .overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: radial-gradient(circle, transparent 0%, #0b0c10 90%); z-index: -1; }

        /* --- NAV --- */
        nav { padding: 20px 5%; display: flex; justify-content: space-between; align-items: center; position: fixed; width: 100%; top: 0; z-index: 1000; background: rgba(11,12,16,0.9); backdrop-filter: blur(10px); border-bottom: 1px solid rgba(255,255,255,0.1); }
        .logo { font-family: 'JetBrains Mono'; font-weight: 700; font-size: 1.2rem; }
        .logo span { color: var(--brand-db); }
        .nav-items a { color: #aaa; text-decoration: none; margin-left: 30px; font-weight: 600; font-size: 0.9rem; transition: 0.3s; }
        .nav-items a:hover { color: #fff; }

        /* --- HERO --- */
        .hero { height: 100vh; display: flex; flex-direction: column; justify-content: center; padding: 0 10%; }
        h1 { font-size: 5rem; line-height: 1; font-weight: 800; margin-bottom: 20px; }
        .hero-desc { max-width: 600px; font-size: 1.2rem; color: #ccc; border-left: 4px solid var(--brand-db); padding-left: 20px; }

        /* --- DATABRICKS NOTEBOOK UI (PURE CSS) --- */
        .notebook-section { padding: 80px 10%; }
        .notebook-container {
            background: #2D2D2D; border-radius: 8px; overflow: hidden;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5); border: 1px solid #444;
            max-width: 900px; margin: 0 auto;
        }
        .nb-header {
            background: #1f1f1f; padding: 10px 15px; display: flex; gap: 10px; align-items: center; border-bottom: 1px solid #333;
        }
        .nb-dot { width: 12px; height: 12px; border-radius: 50%; }
        .nb-title { font-family: 'JetBrains Mono'; font-size: 0.8rem; color: #aaa; margin-left: 10px; }
        
        .nb-cell { padding: 20px; font-family: 'JetBrains Mono', monospace; font-size: 0.9rem; color: #d4d4d4; }
        .nb-cell-header { display: flex; justify-content: space-between; margin-bottom: 10px; color: #888; font-size: 0.75rem; }
        .nb-code { line-height: 1.6; }
        
        .kw { color: #569cd6; } /* keyword */
        .fn { color: #dcdcaa; } /* function */
        .str { color: #ce9178; } /* string */
        .var { color: #9cdcfe; } /* variable */
        .com { color: #6a9955; } /* comment */

        /* --- MEDALLION ARCHITECTURE --- */
        .medallion-container { display: flex; justify-content: center; gap: 30px; margin-top: 50px; flex-wrap: wrap; }
        .layer {
            background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1);
            padding: 30px; border-radius: 15px; width: 250px; text-align: center; position: relative;
            transition: 0.3s;
        }
        .layer:hover { transform: translateY(-10px); border-color: var(--brand-db); }
        .layer h3 { margin: 15px 0 5px 0; }
        .layer i { font-size: 2.5rem; }
        
        /* --- GRID STACK --- */
        .stack-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; padding: 80px 10%; }
        .card { background: rgba(255,255,255,0.03); padding: 30px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.1); transition: 0.3s; }
        .card:hover { border-color: var(--brand-db); transform: translateY(-5px); }
        .card-db { border-top: 3px solid var(--brand-db); }
        .card-ms { border-top: 3px solid var(--brand-ms); }
        
        /* --- TIMELINE --- */
        .timeline-sec { padding: 80px 10%; }
        .job { border-left: 2px solid #333; padding-left: 30px; margin-bottom: 50px; position: relative; }
        .job::before { content:''; position: absolute; left: -6px; top: 5px; width: 10px; height: 10px; background: var(--brand-db); border-radius: 50%; }

        footer { padding: 60px 0; text-align: center; background: #000; border-top: 1px solid #222; }
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
            <a href="#notebook">Notebook</a>
            <a href="#stack">Certifications</a>
            <a href="#experience">Experience</a>
        </div>
    </nav>

    <section class="hero">
        <div style="color: var(--brand-db); font-weight: 700; margin-bottom: 20px;">// SENIOR DATA ENGINEER</div>
        <h1 data-aos="fade-up">Architecting the <br>Lakehouse.</h1>
        <div class="hero-desc" data-aos="fade-up" data-aos-delay="200">
            Specialized in Databricks optimization, Unity Catalog governance, and Azure Cloud infrastructure.
            I turn raw data into gold-standard assets.
        </div>
    </section>

    <section class="notebook-section" id="notebook">
        <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 40px;">My Daily Driver</h2>
        
        <div class="notebook-container" data-aos="zoom-in">
            <div class="nb-header">
                <div class="nb-dot" style="background:#ff5f56"></div>
                <div class="nb-dot" style="background:#ffbd2e"></div>
                <div class="nb-dot" style="background:#27c93f"></div>
                <span class="nb-title">medallion_architecture_etl.py (Python)</span>
            </div>
            <div class="nb-cell">
                <div class="nb-cell-header">
                    <span>Cmd 1</span>
                    <span style="color: var(--brand-db);"><i class="fa-solid fa-play"></i> Run</span>
                </div>
                <div class="nb-code">
                    <span class="com"># Define Medallion Architecture ingestion using Auto Loader</span><br>
                    <span class="kw">def</span> <span class="fn">ingest_bronze_layer</span>(source_path, table_name):<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;<span class="var">df</span> = spark.readStream.format(<span class="str">"cloudFiles"</span>) \<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.option(<span class="str">"cloudFiles.format"</span>, <span class="str">"json"</span>) \<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.load(source_path)<br>
                    <br>
                    &nbsp;&nbsp;&nbsp;&nbsp;<span class="var">df</span>.writeStream.format(<span class="str">"delta"</span>) \<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.option(<span class="str">"checkpointLocation"</span>, <span class="str">f"/mnt/checkpoints/{table_name}"</span>) \<br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.table(<span class="str">f"catalog.bronze.{table_name}"</span>)<br>
                    <br>
                    <span class="com"># Optimize using Liquid Clustering for performance</span><br>
                    <span class="kw">print</span>(<span class="str">"Deploying to Production Cluster..."</span>)
                </div>
            </div>
        </div>

        <div class="medallion-container">
            <div class="layer" style="border-top: 3px solid #CD7F32">
                <i class="fa-solid fa-database" style="color: #CD7F32"></i>
                <h3>Bronze</h3>
                <p style="font-size:0.8rem; color:#aaa">Raw Data Ingestion<br>Parquet / JSON</p>
            </div>
            <div style="align-self:center; font-size:1.5rem; color:#555"><i class="fa-solid fa-arrow-right"></i></div>
            <div class="layer" style="border-top: 3px solid #C0C0C0">
                <i class="fa-solid fa-filter" style="color: #C0C0C0"></i>
                <h3>Silver</h3>
                <p style="font-size:0.8rem; color:#aaa">Cleaned & Conformed<br>Delta Lake</p>
            </div>
            <div style="align-self:center; font-size:1.5rem; color:#555"><i class="fa-solid fa-arrow-right"></i></div>
            <div class="layer" style="border-top: 3px solid #FFD700">
                <i class="fa-solid fa-chart-pie" style="color: #FFD700"></i>
                <h3>Gold</h3>
                <p style="font-size:0.8rem; color:#aaa">Business Aggregates<br>Power BI Ready</p>
            </div>
        </div>
    </section>

    <section id="stack" class="stack-grid">
        <div class="card card-db" data-aos="fade-right">
            <h3 style="color: var(--brand-db); margin-bottom: 20px;"><i class="fa-solid fa-layer-group"></i> Databricks</h3>
            
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Certified Professional</h4>
                <p style="font-size:0.9rem; color:#888">Expert Level Data Engineering</p>
            </div>
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Gen AI Associate</h4>
                <p style="font-size:0.9rem; color:#888">LLM & RAG Systems Implementation</p>
            </div>
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Apache Spark Dev</h4>
                <p style="font-size:0.9rem; color:#888">Core Engine Optimization</p>
            </div>
        </div>

        <div class="card card-ms" data-aos="fade-left">
            <h3 style="color: var(--brand-ms); margin-bottom: 20px;"><i class="fa-brands fa-microsoft"></i> Azure Cloud</h3>
            
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Fabric Analytics (DP-600)</h4>
                <p style="font-size:0.9rem; color:#888">OneLake & Synapse Engineering</p>
            </div>
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Azure AI (AI-102)</h4>
                <p style="font-size:0.9rem; color:#888">Cognitive Services & OpenAI</p>
            </div>
            <div style="margin-bottom: 20px;">
                <h4 style="color:#fff">Database Admin (DP-300)</h4>
                <p style="font-size:0.9rem; color:#888">SQL Server Performance Tuning</p>
            </div>
        </div>

        <div class="card" style="border-top: 3px solid #9D28AC;" data-aos="fade-up">
            <h3 style="color: #9D28AC; margin-bottom: 20px;"><i class="fa-brands fa-github"></i> AI Tools</h3>
            <div>
                <h4 style="color:#fff">GitHub Copilot (GH-300)</h4>
                <p style="font-size:0.9rem; color:#888">AI Pair Programming Expert</p>
            </div>
            <div style="margin-top: 20px;">
                <h4 style="color:#fff">GitHub Foundations</h4>
                <p style="font-size:0.9rem; color:#888">CI/CD & Advanced Security</p>
            </div>
        </div>
    </section>

    <section class="timeline-sec" id="experience">
        <h2 style="font-size: 2.5rem; margin-bottom: 40px;">Professional Journey</h2>
        
        <div class="job" data-aos="fade-up">
            <div class="job-role">Data Engineer</div>
            <span class="job-company">EY (Ernst & Young) | 10.2024 - Present</span>
            <p style="color: #bbb; margin-top: 10px;">
                Driving the adoption of <strong>Lakehouse Architecture</strong>. Focusing on FinOps, Unity Catalog Governance, and mentoring juniors in Spark optimization techniques.
            </p>
        </div>

        <div class="job" data-aos="fade-up">
            <div class="job-role">Data Engineer Intern</div>
            <span class="job-company">Sii Poland | 02.2024 - 10.2024</span>
            <p style="color: #bbb; margin-top: 10px;">
                Built scalable ETL pipelines using Azure Data Factory and Databricks. Automated data ingestion and transformation processes.
            </p>
        </div>

        <div class="job" data-aos="fade-up">
            <div class="job-role">Junior BI Specialist</div>
            <span class="job-company">Micro Solutions | 08.2022 - 06.2023</span>
            <p style="color: #bbb; margin-top: 10px;">
                Delivered actionable insights using Power BI (PL-300 certified). Specialized in DAX modeling and SQL querying.
            </p>
        </div>
    </section>

    <footer>
        <h2 style="color: #fff; margin-bottom: 20px;">Damian Kędzierski</h2>
        <a href="mailto:Damian.kedzierski@op.pl" style="color: #fff; text-decoration: none; font-size: 1.1rem; border: 1px solid #333; padding: 10px 20px; border-radius: 50px;">Damian.kedzierski@op.pl</a>
        <div style="margin-top: 30px; font-size: 2rem;">
            <a href="https://linkedin.com" target="_blank" style="color: #fff;"><i class="fa-brands fa-linkedin"></i></a>
        </div>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>AOS.init();</script>
</body>
</html>
