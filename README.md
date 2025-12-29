<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Senior Data Engineer</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Space+Grotesk:wght@300;500;700&family=Inter:wght@300;400&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            --bg: #030303;
            --primary: #FF3621; /* Databricks Red */
            --secondary: #0078D4; /* Azure Blue */
            --accent: #D256E1; /* AI Purple */
            --white: #ffffff;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.08);
            --cursor-size: 20px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; cursor: none; /* Ukrywamy systemowy kursor */ }

        body {
            background-color: var(--bg);
            color: var(--white);
            font-family: 'Space Grotesk', sans-serif;
            overflow-x: hidden;
            width: 100vw;
        }

        /* --- CUSTOM CURSOR --- */
        .cursor {
            position: fixed; top: 0; left: 0; width: var(--cursor-size); height: var(--cursor-size);
            border: 1px solid rgba(255,255,255,0.5); border-radius: 50%;
            pointer-events: none; z-index: 9999;
            transform: translate(-50%, -50%); transition: width 0.3s, height 0.3s, background 0.3s;
            mix-blend-mode: difference;
        }
        .cursor-dot {
            position: fixed; top: 0; left: 0; width: 4px; height: 4px; background: white; border-radius: 50%;
            pointer-events: none; z-index: 9999; transform: translate(-50%, -50%);
        }
        body:hover .cursor { opacity: 1; }

        /* --- NOISE OVERLAY (High-End Effect) --- */
        .noise {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; z-index: 9000; opacity: 0.05;
            background: url('https://grainy-gradients.vercel.app/noise.svg');
        }

        /* --- WEBGL BACKGROUND --- */
        #vanta-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh; z-index: -1;
            opacity: 0.4;
        }

        /* --- TYPOGRAPHY & LAYOUT --- */
        h1 {
            font-family: 'Syncopate', sans-serif; font-weight: 700; text-transform: uppercase;
            font-size: 6vw; line-height: 0.9; mix-blend-mode: overlay;
        }
        h2 { font-family: 'Syncopate', sans-serif; font-size: 3rem; margin-bottom: 40px; }
        
        .container { max-width: 1400px; margin: 0 auto; padding: 0 5%; }
        section { padding: 150px 0; position: relative; }

        /* --- NAV --- */
        nav {
            position: fixed; top: 30px; left: 50%; transform: translateX(-50%);
            z-index: 1000;
            background: rgba(255,255,255,0.05); backdrop-filter: blur(10px);
            padding: 15px 30px; border-radius: 50px; border: 1px solid rgba(255,255,255,0.1);
            display: flex; gap: 30px;
        }
        nav a {
            text-decoration: none; color: #aaa; font-size: 0.8rem; text-transform: uppercase; letter-spacing: 1px;
            font-weight: 700; transition: 0.3s;
        }
        nav a:hover { color: #fff; }

        /* --- HERO --- */
        .hero { height: 100vh; display: flex; align-items: center; }
        .hero-content { position: relative; z-index: 2; }
        .hero-role {
            display: block; font-family: 'Space Grotesk'; color: var(--primary); letter-spacing: 4px;
            margin-bottom: 20px; font-weight: 700; font-size: 1rem;
        }
        
        /* Glitch Effect on Text Hover */
        .glitch-wrapper { display: inline-block; position: relative; }
        
        /* --- BENTO GRID (PROJECTS) --- */
        .bento-grid {
            display: grid; grid-template-columns: repeat(12, 1fr); grid-auto-rows: minmax(200px, auto);
            gap: 20px;
        }
        .bento-item {
            background: var(--glass); border: 1px solid var(--border); border-radius: 20px;
            padding: 40px; position: relative; overflow: hidden; transition: 0.4s;
            display: flex; flex-direction: column; justify-content: space-between;
        }
        .bento-item:hover { background: rgba(255,255,255,0.06); border-color: rgba(255,255,255,0.2); transform: scale(0.98); }
        
        /* Sizes */
        .span-12 { grid-column: span 12; }
        .span-8 { grid-column: span 8; }
        .span-6 { grid-column: span 6; }
        .span-4 { grid-column: span 4; }
        @media (max-width: 900px) { .span-8, .span-6, .span-4 { grid-column: span 12; } }

        .project-tag {
            font-family: 'Syncopate'; font-size: 3rem; color: rgba(255,255,255,0.1);
            position: absolute; top: 20px; right: 20px; font-weight: 700;
        }
        .bento-title { font-size: 2rem; margin-bottom: 10px; font-weight: 700; }
        .bento-desc { color: #888; font-size: 1rem; max-width: 80%; }
        .tech-stack { margin-top: 20px; display: flex; gap: 10px; flex-wrap: wrap; }
        .pill { 
            padding: 5px 15px; border: 1px solid rgba(255,255,255,0.2); border-radius: 50px; 
            font-size: 0.75rem; text-transform: uppercase; 
        }

        /* --- MARQUEE (SKILLS) --- */
        .marquee-wrapper {
            background: var(--primary); color: #000; padding: 20px 0; overflow: hidden;
            transform: rotate(-2deg) scale(1.1); margin: 50px 0;
        }
        .marquee-content {
            display: flex; gap: 50px; animation: scroll 20s linear infinite; white-space: nowrap;
        }
        .marquee-item { font-family: 'Syncopate'; font-weight: 700; font-size: 3rem; text-transform: uppercase; }
        @keyframes scroll { 0% { transform: translateX(0); } 100% { transform: translateX(-100%); } }

        /* --- EXPERIENCE LIST --- */
        .exp-row {
            border-top: 1px solid rgba(255,255,255,0.1); padding: 40px 0;
            display: flex; justify-content: space-between; align-items: flex-start;
            transition: 0.3s;
        }
        .exp-row:hover { background: rgba(255,255,255,0.02); padding-left: 20px; padding-right: 20px;}
        .exp-year { font-family: 'Syncopate'; color: #555; font-size: 1.2rem; }
        .exp-role { font-size: 2rem; font-weight: 700; }
        .exp-company { color: var(--primary); font-family: 'Space Grotesk'; font-size: 1.2rem; margin-bottom: 10px; display: block;}
        
        /* --- FOOTER (BIG) --- */
        footer { height: 80vh; display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
        .contact-big {
            font-family: 'Syncopate'; font-size: 5vw; font-weight: 700; color: transparent;
            -webkit-text-stroke: 1px rgba(255,255,255,0.5); text-decoration: none;
            transition: 0.3s;
        }
        .contact-big:hover { color: var(--primary); -webkit-text-stroke: 1px var(--primary); }

        /* --- UTILS --- */
        .glow-text { text-shadow: 0 0 20px rgba(255, 54, 33, 0.5); }
        .reveal-text { opacity: 0; transform: translateY(50px); } /* For GSAP */

    </style>
</head>
<body>

    <div class="noise"></div>
    <div id="vanta-canvas"></div>
    <div class="cursor"></div>
    <div class="cursor-dot"></div>

    <nav>
        <a href="#work" data-cursor-hover>Work</a>
        <a href="#stack" data-cursor-hover>Stack</a>
        <a href="#about" data-cursor-hover>About</a>
    </nav>

    <section class="hero container">
        <div class="hero-content">
            <span class="hero-role reveal-text">Senior Data Engineer</span>
            <h1 class="reveal-text">Architecting<br><span style="color: var(--primary);">Intelligent</span><br>Data Systems</h1>
            <p class="reveal-text" style="max-width: 500px; margin-top: 30px; font-size: 1.1rem; color: #ccc;">
                Transforming chaos into Medallion Architecture. Databricks & Azure Expert focusing on Data Vault 2.0 and Gen AI scalability.
            </p>
        </div>
    </section>

    <div class="marquee-wrapper">
        <div class="marquee-content">
            <span class="marquee-item">Databricks Pro</span>
            <span class="marquee-item">///</span>
            <span class="marquee-item">Gen AI Associate</span>
            <span class="marquee-item">///</span>
            <span class="marquee-item">Spark Optimization</span>
            <span class="marquee-item">///</span>
            <span class="marquee-item">Azure Architect</span>
            <span class="marquee-item">///</span>
            <span class="marquee-item">GitHub Copilot Expert</span>
            <span class="marquee-item">///</span>
            <span class="marquee-item">Databricks Pro</span> <span class="marquee-item">///</span>
            <span class="marquee-item">Gen AI Associate</span>
        </div>
    </div>

    <section id="work" class="container">
        <h2 data-cursor-hover>Selected Works</h2>
        
        <div class="bento-grid">
            
            <div class="bento-item span-8" data-cursor-hover style="border-top: 2px solid var(--primary);">
                <div class="project-tag">01</div>
                <div>
                    <h3 class="bento-title">Data Vault 2.0 Transformation</h3>
                    <p class="bento-desc">
                        Complete overhaul of a monolithic Warehouse into a scalable Data Mesh. 
                        Implemented <strong>Hash Keys</strong>, Hubs/Sats using DBT on Databricks.
                        Reduced data latency from 24h to 15min.
                    </p>
                    <div class="tech-stack">
                        <span class="pill">Databricks</span>
                        <span class="pill">DBT Core</span>
                        <span class="pill">Data Vault</span>
                        <span class="pill">PySpark</span>
                    </div>
                </div>
            </div>

            <div class="bento-item span-4" data-cursor-hover style="border-top: 2px solid var(--accent);">
                <div class="project-tag">02</div>
                <div>
                    <h3 class="bento-title">Enterprise RAG System</h3>
                    <p class="bento-desc">
                        Internal Knowledge Base using LLMs. 
                        Vector Search & Unity Catalog security.
                    </p>
                    <div class="tech-stack">
                        <span class="pill">LangChain</span>
                        <span class="pill">Vector DB</span>
                        <span class="pill">Azure OpenAI</span>
                    </div>
                </div>
            </div>

            <div class="bento-item span-4" data-cursor-hover>
                <i class="fa-solid fa-layer-group" style="font-size: 3rem; color: var(--primary); margin-bottom: 20px;"></i>
                <h3 class="bento-title">Databricks Pro</h3>
                <p class="bento-desc">Certified Data Engineer Professional. Expert in Delta Lake internals.</p>
            </div>

            <div class="bento-item span-4" data-cursor-hover>
                <i class="fa-brands fa-microsoft" style="font-size: 3rem; color: var(--secondary); margin-bottom: 20px;"></i>
                <h3 class="bento-title">Fabric Engineer</h3>
                <p class="bento-desc">DP-600 Certified. OneLake & Synapse Architecture specialist.</p>
            </div>

            <div class="bento-item span-4" data-cursor-hover>
                <i class="fa-brands fa-github" style="font-size: 3rem; color: #fff; margin-bottom: 20px;"></i>
                <h3 class="bento-title">Copilot Expert</h3>
                <p class="bento-desc">GH-300 Certified. AI-Augmented programming & CI/CD.</p>
            </div>

        </div>
    </section>

    <section id="about" class="container">
        <h2 data-cursor-hover>Experience Timeline</h2>
        
        <div class="exp-row" data-cursor-hover>
            <span class="exp-year">2024 - Present</span>
            <div>
                <span class="exp-company">EY (Ernst & Young)</span>
                <div class="exp-role">Senior Data Engineer</div>
                <p style="color: #888; margin-top: 10px;">Lakehouse Architecture, FinOps, ESG Data Platforms.</p>
            </div>
        </div>

        <div class="exp-row" data-cursor-hover>
            <span class="exp-year">2024 - 2024</span>
            <div>
                <span class="exp-company">Sii Poland</span>
                <div class="exp-role">Data Engineer Intern</div>
                <p style="color: #888; margin-top: 10px;">Azure Data Factory, ETL Migrations, Python Scripting.</p>
            </div>
        </div>

        <div class="exp-row" data-cursor-hover>
            <span class="exp-year">2022 - 2023</span>
            <div>
                <span class="exp-company">Micro Solutions</span>
                <div class="exp-role">Junior BI Specialist</div>
                <p style="color: #888; margin-top: 10px;">Power BI (PL-300), SQL Analysis, Reporting.</p>
            </div>
        </div>
    </section>

    <footer>
        <p style="font-family: 'Space Grotesk'; margin-bottom: 20px;">Ready to scale your data?</p>
        <a href="mailto:Damian.kedzierski@op.pl" class="contact-big" data-cursor-hover>GET IN TOUCH</a>
        
        <div style="margin-top: 50px; display: flex; gap: 30px;">
            <a href="https://linkedin.com" style="color:#fff; font-size: 1.5rem;" data-cursor-hover><i class="fa-brands fa-linkedin"></i></a>
            <a href="https://github.com" style="color:#fff; font-size: 1.5rem;" data-cursor-hover><i class="fa-brands fa-github"></i></a>
        </div>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vanta@latest/dist/vanta.net.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

    <script>
        // 1. INIT VANTA.JS (3D Background)
        VANTA.NET({
            el: "#vanta-canvas",
            mouseControls: true,
            touchControls: true,
            gyroControls: false,
            minHeight: 200.00,
            minWidth: 200.00,
            scale: 1.00,
            scaleMobile: 1.00,
            color: 0xff3621,       /* Databricks Red Dots */
            backgroundColor: 0x030303,
            points: 12.00,
            maxDistance: 22.00,
            spacing: 18.00
        });

        // 2. CUSTOM CURSOR LOGIC
        const cursor = document.querySelector('.cursor');
        const cursorDot = document.querySelector('.cursor-dot');
        const hoverElements = document.querySelectorAll('[data-cursor-hover]');

        document.addEventListener('mousemove', (e) => {
            cursorDot.style.left = e.clientX + 'px';
            cursorDot.style.top = e.clientY + 'px';
            
            // Lag effect for outer circle
            setTimeout(() => {
                cursor.style.left = e.clientX + 'px';
                cursor.style.top = e.clientY + 'px';
            }, 50);
        });

        // Hover Effect
        hoverElements.forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursor.style.transform = 'translate(-50%, -50%) scale(3)';
                cursor.style.background = 'rgba(255,255,255,0.1)';
                cursor.style.border = 'none';
            });
            el.addEventListener('mouseleave', () => {
                cursor.style.transform = 'translate(-50%, -50%) scale(1)';
                cursor.style.background = 'transparent';
                cursor.style.border = '1px solid rgba(255,255,255,0.5)';
            });
        });

        // 3. GSAP ANIMATIONS
        gsap.registerPlugin(ScrollTrigger);

        // Hero Text Reveal
        gsap.from(".reveal-text", {
            y: 100,
            opacity: 0,
            duration: 1.5,
            stagger: 0.2,
            ease: "power4.out",
            delay: 0.5
        });

        // Bento Grid Reveal on Scroll
        gsap.from(".bento-item", {
            scrollTrigger: {
                trigger: ".bento-grid",
                start: "top 80%",
            },
            y: 50,
            opacity: 0,
            duration: 1,
            stagger: 0.1,
            ease: "power3.out"
        });

        // Experience Rows Reveal
        gsap.from(".exp-row", {
            scrollTrigger: {
                trigger: "#about",
                start: "top 70%",
            },
            x: -50,
            opacity: 0,
            duration: 1,
            stagger: 0.2,
            ease: "power3.out"
        });

    </script>
</body>
</html>
