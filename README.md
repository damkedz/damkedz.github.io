<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Damian Kędzierski | Data Architect</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/framer-motion@10.16.4/dist/framer-motion.js"></script>
    
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Space+Grotesk:wght@400;700&display=swap');
        body { background-color: #02040a; font-family: 'Inter', sans-serif; }
        h1, h2, h3 { font-family: 'Space Grotesk', sans-serif; }
        .glass-card { background: rgba(5, 10, 20, 0.9); backdrop-filter: blur(12px); border: 1px solid rgba(255,255,255,0.05); }
    </style>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        databricks: '#FF3621',
                        azure: '#0078D4',
                        ai: '#9D28AC',
                        dark: '#02040a'
                    }
                }
            }
        }
    </script>
</head>
<body class="text-slate-300 selection:bg-azure selection:text-white overflow-x-hidden">

    <div id="root"></div>

    <script type="text/babel">
        // Access React and Motion from the global window object
        const { useState, useEffect } = React;
        const { motion } = window.Motion;

        // --- ICONS (Inline SVGs to avoid complex imports) ---
        const Icon = ({ path, color, className }) => (
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke={color || "currentColor"} strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}>
                {path}
            </svg>
        );

        const Icons = {
            Database: (props) => <Icon {...props} path={<><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></>} />,
            Cloud: (props) => <Icon {...props} path={<><path d="M17.5 19c0-3.037-2.463-5.5-5.5-5.5S6.5 15.963 6.5 19"/><path d="M19 12a7 7 0 1 0-14 0"/></>} />,
            Brain: (props) => <Icon {...props} path={<><path d="M9.5 2A2.5 2.5 0 0 1 12 4.5v15a2.5 2.5 0 0 1-4.96.44 2.5 2.5 0 0 1-2.96-3.08 3 3 0 0 1-.34-5.58 2.5 2.5 0 0 1 1.32-4.24 2.5 2.5 0 0 1 1.98-3A2.5 2.5 0 0 1 9.5 2Z"/><path d="M14.5 2A2.5 2.5 0 0 0 12 4.5v15a2.5 2.5 0 0 0 4.96.44 2.5 2.5 0 0 0 2.96-3.08 3 3 0 0 0 .34-5.58 2.5 2.5 0 0 0-1.32-4.24 2.5 2.5 0 0 0-1.98-3A2.5 2.5 0 0 0 14.5 2Z"/></>} />,
            Code: (props) => <Icon {...props} path={<><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></>} />,
            ArrowRight: (props) => <Icon {...props} path={<><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></>} />
        };

        // --- COMPONENTS ---

        const GlowCard = ({ children, color, className = "" }) => {
            const glowColor = color === 'databricks' ? '#FF3621' : color === 'azure' ? '#0078D4' : '#9D28AC';
            return (
                <div className={`relative group rounded-2xl p-[1px] overflow-hidden ${className}`}>
                    <div className="absolute inset-0 transition-opacity duration-500 opacity-0 group-hover:opacity-100"
                        style={{ background: `radial-gradient(circle at center, ${glowColor} 0%, transparent 70%)` }} />
                    <div className="relative h-full glass-card rounded-2xl p-6 transition-all duration-300 group-hover:border-white/20">
                        {children}
                    </div>
                </div>
            );
        };

        const TechBadge = ({ text, color }) => {
            const colors = {
                databricks: 'bg-red-500/10 text-red-500',
                azure: 'bg-blue-500/10 text-blue-500',
                ai: 'bg-purple-500/10 text-purple-500'
            };
            return (
                <span className={`px-3 py-1 rounded-full text-xs font-mono font-medium tracking-wide ${colors[color]} border border-white/5`}>
                    {text}
                </span>
            );
        };

        // --- MAIN APP ---

        const App = () => {
            return (
                <div className="min-h-screen pb-20">
                    
                    {/* Background Ambience */}
                    <div className="fixed inset-0 z-0 pointer-events-none">
                        <div className="absolute top-0 left-1/4 w-96 h-96 bg-blue-600/10 rounded-full blur-[120px] mix-blend-screen animate-pulse" />
                        <div className="absolute bottom-0 right-1/4 w-96 h-96 bg-red-600/10 rounded-full blur-[120px] mix-blend-screen animate-pulse" />
                    </div>

                    {/* HERO SECTION */}
                    <section className="relative z-10 min-h-screen flex flex-col justify-center px-6 pt-10">
                        <div className="max-w-7xl mx-auto w-full grid lg:grid-cols-2 gap-12 items-center">
                            
                            <motion.div initial={{ opacity: 0, x: -50 }} animate={{ opacity: 1, x: 0 }} transition={{ duration: 0.8 }}>
                                <div className="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-white/10 bg-white/5 backdrop-blur-md mb-6">
                                    <span className="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>
                                    <span className="text-xs font-mono text-emerald-400">AVAILABLE FOR NEW PROJECTS</span>
                                </div>
                                <h1 className="text-5xl md:text-7xl font-bold tracking-tight text-white mb-6 leading-tight">
                                    Damian Kędzierski <br />
                                    <span className="text-transparent bg-clip-text bg-gradient-to-r from-slate-200 to-slate-500">Data Architect</span>
                                </h1>
                                <p className="text-xl text-slate-400 mb-8 max-w-lg leading-relaxed">
                                    Transforming raw signals into <span className="text-white font-medium">Gold-standard Data Products</span>. 
                                    Expert in Databricks, Azure & Gen AI.
                                </p>
                                <div className="flex gap-4">
                                    <button className="px-8 py-4 bg-white text-black font-bold rounded-lg hover:bg-slate-200 transition-colors">View Projects</button>
                                </div>
                            </motion.div>

                            {/* Abstract Visual */}
                            <motion.div initial={{ opacity: 0, scale: 0.8 }} animate={{ opacity: 1, scale: 1 }} transition={{ duration: 1 }} className="hidden lg:flex justify-center relative">
                                <div className="w-64 h-64 bg-gradient-to-br from-azure to-ai rounded-full blur-3xl opacity-20 animate-pulse"></div>
                                <div className="absolute inset-0 flex items-center justify-center">
                                    <Icons.Database className="text-white w-32 h-32 opacity-80" />
                                </div>
                            </motion.div>
                        </div>
                    </section>

                    {/* STACK SECTION */}
                    <section className="px-6 py-20 max-w-7xl mx-auto">
                         <div className="grid md:grid-cols-2 gap-8">
                            <GlowCard color="databricks">
                                <div className="flex items-center gap-3 mb-6">
                                    <Icons.Database className="text-databricks w-8 h-8" />
                                    <h3 className="text-2xl font-bold text-white">Databricks Authority</h3>
                                </div>
                                <div className="space-y-4">
                                    <TechBadge text="Certified Professional" color="databricks" />
                                    <TechBadge text="Apache Spark Developer" color="databricks" />
                                    <div className="mt-4 p-4 bg-black/40 rounded border border-white/5 text-center text-sm font-mono text-slate-400">
                                        Bronze &rarr; Silver &rarr; <span className="text-yellow-500 font-bold">Gold</span>
                                    </div>
                                </div>
                            </GlowCard>

                            <GlowCard color="azure">
                                <div className="flex items-center gap-3 mb-6">
                                    <Icons.Cloud className="text-azure w-8 h-8" />
                                    <h3 className="text-2xl font-bold text-white">Azure Infrastructure</h3>
                                </div>
                                <div className="space-y-4">
                                    <TechBadge text="Fabric Analytics (DP-600)" color="azure" />
                                    <TechBadge text="AI Engineer (AI-102)" color="azure" />
                                    <div className="mt-4 p-4 bg-black/40 rounded border border-white/5 text-center text-sm font-mono text-slate-400">
                                        Synapse • Data Factory • Purview
                                    </div>
                                </div>
                            </GlowCard>
                        </div>
                    </section>

                    {/* CODE LAB */}
                    <section className="px-6 py-10 max-w-5xl mx-auto">
                        <div className="rounded-xl overflow-hidden border border-white/10 bg-[#0d1117] shadow-2xl">
                            <div className="bg-[#161b22] px-4 py-2 flex items-center gap-2 border-b border-white/5">
                                <div className="w-3 h-3 rounded-full bg-red-500/50"></div>
                                <div className="w-3 h-3 rounded-full bg-yellow-500/50"></div>
                                <div className="w-3 h-3 rounded-full bg-green-500/50"></div>
                                <span className="ml-2 text-xs font-mono text-slate-500">optimization.py</span>
                            </div>
                            <div className="p-6 font-mono text-sm text-slate-300">
                                <div className="text-slate-500 mb-2"># Liquid Clustering Optimization</div>
                                <div><span className="text-purple-400">def</span> <span className="text-blue-400">optimize_delta_table</span>(df):</div>
                                <div className="pl-4">return df.write.format(<span className="text-green-400">"delta"</span>) \</div>
                                <div className="pl-8">.option(<span className="text-green-400">"liquidClustering"</span>, <span className="text-blue-400">"true"</span>) \</div>
                                <div className="pl-8">.saveAsTable(<span className="text-green-400">"catalog.gold.kpis"</span>)</div>
                            </div>
                        </div>
                    </section>
                    
                    {/* FOOTER */}
                    <footer className="text-center py-12 text-slate-600 text-sm">
                        <p>&copy; 2024 Damian Kędzierski. Single-Page React Portfolio.</p>
                    </footer>
                </div>
            );
        };

        const root = ReactDOM.createRoot(document.getElementById("root"));
        root.render(<App />);
    </script>
</body>
</html>
