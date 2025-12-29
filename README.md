<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Portfolio</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;600;800&family=Roboto+Mono:wght@400;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            /* PROFESSIONAL PALETTE - DEEP NAVY & SLATE */
            --bg-body: #0f172a;       /* Slate 900 */
            --bg-card: #1e293b;       /* Slate 800 */
            --bg-sidebar: #020617;    /* Slate 950 */
            --accent: #38bdf8;        /* Sky Blue */
            --accent-sec: #818cf8;    /* Indigo */
            --text-main: #f8fafc;     /* Slate 50 */
            --text-muted: #94a3b8;    /* Slate 400 */
            --border: #334155;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            background-color: var(--bg-body);
            color: var(--text-main);
            font-family: 'Manrope', sans-serif;
            line-height: 1.6;
            display: flex;
            min-height: 100vh;
        }

        /* --- LAYOUT --- */
        /* LEFT SIDEBAR (Fixed) */
        .sidebar {
            width: 350px;
            background-color: var(--bg-sidebar);
            height: 100vh;
            position: fixed;
            padding: 40px 30px;
            border-right: 1px solid var(--border);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            z-index: 10;
        }

        /* RIGHT CONTENT (Scrollable) */
        .main-content {
            margin-left: 350px; /* Width of sidebar */
            flex: 1;
            padding: 60px 80px;
            max-width: 1200px;
        }

        /* --- TYPOGRAPHY --- */
        h1 { font-size: 2.5rem; font-weight: 800; line-height: 1.1; margin-bottom: 10px; color: #fff; }
        h2 { font-size: 1.8rem; font-weight: 700; margin-bottom: 30px; color: #fff; border-bottom: 2px solid var(--border); padding-bottom: 10px; display: inline-block; }
        h3 { font-size: 1.4rem; font-weight: 600; margin-bottom: 10px; color: var(--text-main); }
        p { color: var(--text-muted); margin-bottom: 15px; font-size: 1rem; }
        
        .role { color: var(--accent); font-weight: 600; font-size: 1.1rem; margin-bottom: 30px; display: block; letter-spacing: 1px; text-transform: uppercase; }
        
        /* --- SIDEBAR ELEMENTS --- */
        .profile-section { text-align: left; }
        .contact-list { list-style: none; margin-top: 30px; }
        .contact-list li { margin-bottom: 15px; display: flex; align-items: center; gap: 10px; color: var(--text-muted); font-size: 0.9rem; }
        .contact-list i { color: var(--accent); width: 20px; }
        
        .skills-cloud { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 30px; }
        .skill-pill {
            background: rgba(56, 189, 248, 0.1); border: 1px solid rgba(56, 189, 248, 0.2);
            color: var(--accent); padding: 5px 12px; border-radius: 4px; font-size: 0.8rem; font-weight: 600;
        }

        .social-links { display: flex; gap: 20px; margin-top: auto; }
        .social-links a { color: var(--text-muted); font-size: 1.5rem; transition: 0.3s; }
        .social-links a:hover { color: var(--accent); }

        /* --- PROJECTS SECTION (THE CORE) --- */
        .project-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 35px;
            margin-bottom: 40px;
            position: relative;
        }
        .project-card::before {
            content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 4px;
            background: var(--accent); border-top-left-radius: 8px; border-bottom-left-radius: 8px;
        }

        .project-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 20px; }
        .project-tags { display: flex; gap: 10px; flex-wrap: wrap; }
        .tag { font-family: 'Roboto Mono', monospace; font-size: 0.75rem; background: #0f172a; padding: 4px 8px; border-radius: 4px; color: var(--accent-sec); border: 1px solid #333; }

        .project-details h4 { color: #fff; margin-top: 20px; margin-bottom: 10px; font-size: 1.1rem; }
        .project-details ul { padding-left: 20px; color: var(--text-muted); margin-bottom: 20px; }
        .project-details li { margin-bottom: 8px; }

        /* --- CERTIFICATION GRID (Compact) --- */
        .cert-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 20px; margin-bottom: 60px;
        }
        .cert-item {
            background: rgba(255,255,255,0.03); border: 1px solid var(--border);
            padding: 20px; border-radius: 6px; display: flex; align-items: center; gap: 15px;
            transition: 0.2s;
        }
        .cert-item:hover { border-color: var(--accent); background: rgba(56, 189, 248, 0.05); }
        .cert-icon { font-size: 1.5rem; color: var(--text-muted); }
        .cert-text h4 { font-size: 0.95rem; margin: 0; color: #fff; }
        .cert-text span { font-size: 0.8rem; color: var(--text-muted); }

        /* Color coding for certs */
        .c-db .cert-icon { color: #FF3621; }
        .c-ms .cert-icon { color: #0078D4; }
        .c-ai .cert-icon { color: #D256E1; }

        /* --- EXPERIENCE TIMELINE --- */
        .timeline-item {
            display: grid; grid-template-columns: 150px 1fr; gap: 30px; margin-bottom: 40px;
        }
        .time-period { font-family: 'Roboto Mono'; color: var(--text-muted); font-size: 0.9rem; text-align: right; padding-top: 5px; }
        .job-content { border-left: 2px solid var(--border); padding-left: 30px; position: relative; }
        .job-content::before {
            content: ''; position: absolute; left: -6px; top: 8px; width: 10px; height: 10px;
            background: var(--accent); border-radius: 50%;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 900px) {
            body { flex-direction: column; }
            .sidebar { width: 100%; height: auto; position: relative; border-right: none; border-bottom: 1px solid var(--border); }
            .main-content { margin-left: 0; padding: 40px 20px; }
            .timeline-item { grid-template-columns: 1fr; gap: 10px; }
            .time-period { text-align: left; }
            .job-content { border-left: none; padding-left: 0; }
            .job-content::before { display: none; }
        }
    </style>
</head>
<body>

    <aside class="sidebar">
        <div class="profile-section">
            <h1>Damian<br>Kędzierski</h1>
            <span class="role">Senior Data Engineer</span>
            <p style="font-size: 0.9rem; margin-top: 20px;">
                Specialized in building scalable Data Products and Lakehouse Architectures. 
                Expert in Databricks, Azure, and Generative AI integration.
            </p>

            <ul class="contact-list">
                <li><i class="fa-solid fa-location-dot"></i> Wrocław, Poland</li>
                <li><i class="fa-solid fa-envelope"></i> Damian.kedzierski@op.pl</li>
                <li><i class="fa-solid fa-phone"></i> +48 533 864 722</li>
            </ul>

            <h4 style="color: #fff; margin-top: 40px; font-size: 0.9rem; text-transform: uppercase;">Core Stack</h4>
            <div class="skills-cloud">
                <span class="skill-pill">Databricks</span>
                <span class="skill-pill">Spark</span>
                <span class="skill-pill">Python</span>
                <span class="skill-pill">SQL</span>
                <span class="skill-pill">Delta Lake</span>
                <span class="skill-pill">Data Vault 2.0</span>
                <span class="skill-pill">DBT</span>
                <span class="skill-pill">Azure Fabric</span>
                <span class="skill-pill">Terraform</span>
                <span class="skill-pill">Gen AI / RAG</span>
            </div>
        </div>

        <div class="social-links">
            <a href="https://linkedin.com" target="_blank"><i class="fa-brands fa-linkedin"></i></a>
            <a href="https://github.com" target="_blank"><i class="fa-brands fa-github"></i></a>
            <a href="mailto:Damian.kedzierski@op.pl"><i class="fa-solid fa-envelope"></i></a>
        </div>
    </aside>

    <main class="main-content">
        
        <section id="about" style="margin-bottom: 80px;">
            <h2>About Me</h2>
            <p style="max-width: 800px; font-size: 1.1rem; color: #cbd5e1;">
                I am a Senior Data Engineer with a strong focus on architectural patterns like <strong>Data Vault 2.0</strong> and <strong>Medallion Architecture</strong>. 
                Currently working at EY, I lead initiatives to modernize legacy data warehouses into scalable cloud-native platforms. 
                I combine deep technical expertise in <strong>Databricks & Spark</strong> with a business-oriented approach to delivering high-quality Data Products.
            </p>
        </section>

        <section id="projects" style="margin-bottom: 80px;">
            <h2>Key Projects & Case Studies</h2>

            <div class="project-card">
                <div class="project-header">
                    <h3>Data Products Transformation (Data Vault 2.0)</h3>
                    <div class="project-tags">
                        <span class="tag">Databricks</span>
                        <span class="tag">DBT</span>
                        <span class="tag">Data Vault 2.0</span>
                        <span class="tag">Azure</span>
                    </div>
                </div>
                <p>
                    Led the transformation of a monolithic on-premise Data Warehouse into a scalable <strong>Data Mesh</strong> architecture on Azure Databricks.
                </p>
                
                <div class="project-details">
                    <h4><i class="fa-solid fa-bullseye" style="color: var(--accent); margin-right: 10px;"></i>The Challenge</h4>
                    <p>The client struggled with slow reporting (24h+ latency), lack of historical tracking, and tight coupling between ingestion and logic.</p>
                    
                    <h4><i class="fa-solid fa-code-branch" style="color: var(--accent); margin-right: 10px;"></i>The Solution</h4>
                    <ul>
                        <li>Implemented <strong>Data Vault 2.0</strong> modeling (Hubs, Links, Satellites) to enable agile data integration and full auditability.</li>
                        <li>Utilized <strong>DBT (Data Build Tool)</strong> on Databricks for managing SQL transformations and lineage.</li>
                        <li>Automated generation of Hash Keys using PySpark UDFs for consistent identification across sources.</li>
                        <li>Decoupled "Raw Data Vault" from "Business Vault" to allow parallel development of business rules.</li>
                    </ul>

                    <h4><i class="fa-solid fa-chart-line" style="color: var(--accent); margin-right: 10px;"></i>The Result</h4>
                    <p style="color: #fff;">Reduced data availability latency from 24h to <strong>15 minutes</strong>. Enabled full historical tracking of business entities without performance degradation.</p>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <h3>Enterprise RAG System for Internal Docs</h3>
                    <div class="project-tags">
                        <span class="tag">Gen AI</span>
                        <span class="tag">Vector Search</span>
                        <span class="tag">LangChain</span>
                        <span class="tag">Unity Catalog</span>
                    </div>
                </div>
                <p>
                    Developed an internal Knowledge Base Assistant using Generative AI to democratize access to technical documentation.
                </p>
                
                <div class="project-details">
                    <h4>The Solution</h4>
                    <ul>
                        <li>Built an ingestion pipeline to parse PDFs/Confluence pages and store embeddings in <strong>Databricks Vector Search</strong>.</li>
                        <li>Implemented a RAG (Retrieval Augmented Generation) architecture using Azure OpenAI (GPT-4) and LangChain.</li>
                        <li>Secured data access using Unity Catalog row-level filtering based on user AD groups.</li>
                    </ul>
                </div>
            </div>

            <div class="project-card">
                <div class="project-header">
                    <h3>Legacy SQL to Spark Migration (Cost Opt.)</h3>
                    <div class="project-tags">
                        <span class="tag">PySpark</span>
                        <span class="tag">FinOps</span>
                        <span class="tag">Performance Tuning</span>
                    </div>
                </div>
                <p>
                    Refactored legacy stored procedures into optimized PySpark jobs.
                </p>
                <div class="project-details">
                    <ul>
                        <li>Analyzed Spark Execution Plans to identify bottlenecks (skew, spills).</li>
                        <li>Implemented <strong>Liquid Clustering</strong> and Z-Ordering to prune data scanning.</li>
                        <li><strong>Result:</strong> Reduced cloud compute costs by <strong>40%</strong> while handling 3x more data volume.</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="experience" style="margin-bottom: 80px;">
            <h2>Experience</h2>
            
            <div class="timeline-item">
                <div class="time-period">Oct 2024 - Present</div>
                <div class="job-content">
                    <h3>Data Engineer</h3>
                    <span style="color: var(--accent);">EY (Ernst & Young)</span>
                    <p>Designing Lakehouse Architectures and implementing Data Governance.</p>
                </div>
            </div>

            <div class="timeline-item">
                <div class="time-period">Feb 2024 - Oct 2024</div>
                <div class="job-content">
                    <h3>Data Engineer Intern</h3>
                    <span style="color: var(--accent);">Sii Poland</span>
                    <p>Azure Data Factory pipelines, ETL automation, and data migration.</p>
                </div>
            </div>

            <div class="timeline-item">
                <div class="time-period">Aug 2022 - Jun 2023</div>
                <div class="job-content">
                    <h3>Junior BI Specialist</h3>
                    <span style="color: var(--accent);">Micro Solutions</span>
                    <p>Power BI reporting, SQL analysis, and business requirements gathering.</p>
                </div>
            </div>
        </section>

        <section id="certs">
            <h2>Certifications</h2>
            <div class="cert-grid">
                <div class="cert-item c-db">
                    <i class="fa-solid fa-layer-group cert-icon"></i>
                    <div class="cert-text">
                        <h4>Databricks Professional</h4>
                        <span>Data Engineer Expert</span>
                    </div>
                </div>
                <div class="cert-item c-db">
                    <i class="fa-solid fa-wand-magic-sparkles cert-icon"></i>
                    <div class="cert-text">
                        <h4>Gen AI Associate</h4>
                        <span>Databricks Certified</span>
                    </div>
                </div>
                <div class="cert-item c-db">
                    <i class="fa-solid fa-fire cert-icon"></i>
                    <div class="cert-text">
                        <h4>Apache Spark Dev</h4>
                        <span>Core Engine</span>
                    </div>
                </div>

                <div class="cert-item c-ms">
                    <i class="fa-brands fa-microsoft cert-icon"></i>
                    <div class="cert-text">
                        <h4>Fabric Analytics</h4>
                        <span>DP-600 Associate</span>
                    </div>
                </div>
                <div class="cert-item c-ms">
                    <i class="fa-solid fa-brain cert-icon"></i>
                    <div class="cert-text">
                        <h4>Azure AI Engineer</h4>
                        <span>AI-102 Associate</span>
                    </div>
                </div>
                 <div class="cert-item c-ms">
                    <i class="fa-solid fa-database cert-icon"></i>
                    <div class="cert-text">
                        <h4>Azure DB Admin</h4>
                        <span>DP-300 Associate</span>
                    </div>
                </div>

                <div class="cert-item c-ai">
                    <i class="fa-brands fa-github cert-icon"></i>
                    <div class="cert-text">
                        <h4>GitHub Copilot</h4>
                        <span>GH-300 Expert</span>
                    </div>
                </div>
            </div>
        </section>

        <footer style="border-top: 1px solid var(--border); padding-top: 40px; color: var(--text-muted); font-size: 0.9rem;">
            &copy; 2025 Damian Kędzierski. All rights reserved.
        </footer>

    </main>

</body>
</html>
