<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski - Data Engineer</title>
    <style>
        /* Styl "Dark Mode" w czystym CSS */
        body {
            background-color: #02040a;
            color: #e2e8f0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 20px;
        }
        h1 { font-size: 2.5rem; margin-bottom: 10px; color: #fff; }
        h2 { border-bottom: 1px solid #333; padding-bottom: 10px; margin-top: 40px; color: #94a3b8; }
        .role { color: #3b82f6; font-family: monospace; font-size: 1.2rem; }
        
        .card {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 8px;
        }
        .tag {
            display: inline-block;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-right: 5px;
            background: #1e293b;
            color: #64748b;
        }
        .tag.db { color: #f87171; border: 1px solid rgba(248, 113, 113, 0.2); } /* Databricks Red */
        .tag.azure { color: #60a5fa; border: 1px solid rgba(96, 165, 250, 0.2); } /* Azure Blue */
        
        a { color: #fff; text-decoration: none; border-bottom: 1px dotted #666; }
        a:hover { border-bottom: 1px solid #fff; }
    </style>
</head>
<body>

    <div class="container">
        <header>
            <h1>Damian Kędzierski</h1>
            <div class="role">Senior Data Engineer & Lakehouse Architect</div>
            <p style="margin-top: 20px; color: #94a3b8;">
                Buduję skalowalne platformy danych w ekosystemach <strong>Databricks</strong> i <strong>Azure</strong>.
                Specjalizuję się w Data Mesh, FinOps oraz Gen AI.
            </p>
        </header>

        <section>
            <h2>Tech Stack</h2>
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div class="card">
                    <h3 style="margin-top: 0; color: #f87171;">Databricks</h3>
                    <p>Certified Professional, Spark Optimization, Unity Catalog, Delta Live Tables.</p>
                </div>
                <div class="card">
                    <h3 style="margin-top: 0; color: #60a5fa;">Azure</h3>
                    <p>Fabric Analytics (DP-600), Synapse, Data Factory, Security Governance.</p>
                </div>
            </div>
        </section>

        <section>
            <h2>Wybrane Projekty</h2>
            
            <div class="card">
                <h3>Data Products Transformation</h3>
                <div style="margin-bottom: 10px;">
                    <span class="tag db">Data Vault 2.0</span>
                    <span class="tag db">DBT</span>
                </div>
                <p>Modernizacja legacy warehouse do architektury Data Mesh. Implementacja domen danych i kontraktów danych.</p>
            </div>

            <div class="card">
                <h3>Enterprise RAG System</h3>
                <div style="margin-bottom: 10px;">
                    <span class="tag azure">Gen AI</span>
                    <span class="tag azure">Vector Search</span>
                </div>
                <p>Wewnętrzna baza wiedzy oparta o LLM z zachowaniem restrykcyjnych reguł bezpieczeństwa (RBAC).</p>
            </div>
        </section>

        <footer style="margin-top: 60px; font-size: 0.9rem; color: #666;">
            &copy; 2025 Damian Kędzierski. <a href="mailto:email@example.com">Kontakt</a>
        </footer>
    </div>

</body>
</html>
