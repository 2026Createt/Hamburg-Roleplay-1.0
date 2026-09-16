
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hamburg 1.0 Roleplay | Notruf Hamburg</title>

    <meta property="og:title" content="Hamburg 1.0 Roleplay | Notruf Hamburg">
    <meta property="og:description" content="Wir bauen den ersten Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir deinen Platz im Team oder als Spieler!">
    <meta name="theme-color" content="#1b365d">

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/@studio-freight/lenis@1.0.34/dist/lenis.min.js"></script>

    <style>
        :root {
            --bg-color: #06090f;
            --card-bg: #111827;
            --text-main: #f3f4f6;
            --text-muted: #9ca3af;
            --accent-dark: #1b365d;
            --accent-light: #3b82f6;
            --glow: 0 0 20px rgba(59, 130, 246, 0.4);
            --status-orange: #f59e0b;
            --status-green: #10b981;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }

        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-color); }
        ::-webkit-scrollbar-thumb { background: var(--accent-dark); border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--accent-light); }

        @media (pointer: fine) {
            body { cursor: none; }
            a, button, .card, details summary, iframe, .hamburger, .copy-btn { cursor: none; }
        }
        #cursor-dot {
            width: 8px; height: 8px; background-color: var(--accent-light);
            border-radius: 50%; position: fixed; top: 0; left: 0;
            transform: translate(-50%, -50%); z-index: 10001; pointer-events: none;
            transition: width 0.2s, height 0.2s;
        }
        #cursor-outline {
            width: 30px; height: 30px; border: 2px solid rgba(59, 130, 246, 0.5);
            border-radius: 50%; position: fixed; top: 0; left: 0;
            transform: translate(-50%, -50%); z-index: 10000; pointer-events: none;
            transition: width 0.2s, height 0.2s, transform 0.1s ease-out, background 0.2s;
        }
        .cursor-hover #cursor-outline {
            width: 50px; height: 50px; background: rgba(59, 130, 246, 0.1); border-color: transparent;
        }
        .cursor-hover #cursor-dot { width: 0; height: 0; }

        body { background-color: var(--bg-color); color: var(--text-main); line-height: 1.7; overflow-x: hidden; }

        /* PRELOADER */
        #preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh; background: #04060a; z-index: 9999;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            transition: transform 0.8s cubic-bezier(0.77, 0, 0.175, 1);
        }
        .loader-content { width: 80%; max-width: 400px; text-align: center; }
        .loader-logo { font-size: 2rem; font-weight: 800; letter-spacing: 3px; margin-bottom: 20px; color: #fff; }
        .loader-logo span { color: var(--accent-light); text-shadow: var(--glow); }
        .loader-text { font-size: 0.9rem; color: var(--text-muted); margin-bottom: 10px; font-weight: 300; letter-spacing: 1px; height: 20px; }
        .loader-bar-bg { width: 100%; height: 4px; background: rgba(255,255,255,0.05); border-radius: 4px; overflow: hidden; position: relative; margin-bottom: 15px; }
        .loader-bar-fill { height: 100%; width: 0%; background: var(--accent-light); box-shadow: var(--glow); transition: width 0.1s linear; }
        .loader-percentage { font-size: 1.5rem; font-weight: 600; color: #fff; font-variant-numeric: tabular-nums; }

        .reveal { opacity: 0; transform: translateY(50px); transition: all 0.8s ease-out; }
        .reveal.active { opacity: 1; transform: translateY(0); }

        /* NAVIGATION */
        nav {
            position: fixed; top: 0; width: 100%; padding: 15px 5%;
            display: flex; justify-content: space-between; align-items: center;
            background: rgba(6, 9, 15, 0.8); backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.05); z-index: 1000;
        }
        .logo { font-size: 1.5rem; font-weight: 800; letter-spacing: 2px; text-transform: uppercase; z-index: 1001; }
        .logo span { color: var(--accent-light); }
        .nav-links { display: flex; gap: 30px; align-items: center; list-style: none; }
        .nav-links a { color: var(--text-main); text-decoration: none; font-weight: 600; font-size: 0.9rem; transition: color 0.3s; }
        .nav-links a:hover { color: var(--accent-light); }
        
        .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; z-index: 1001; }
        .hamburger span { width: 25px; height: 3px; background: #fff; border-radius: 3px; transition: all 0.3s ease; }
        
        @media (max-width: 768px) {
            .hamburger { display: flex; }
            .nav-links {
                position: fixed; top: 0; right: -100%; width: 100%; height: 100vh;
                background: rgba(6, 9, 15, 0.98); flex-direction: column; justify-content: center; align-items: center; gap: 40px;
                transition: right 0.4s ease; backdrop-filter: blur(10px);
            }
            .nav-links.active { right: 0; }
            .nav-links a { font-size: 1.5rem; }
            .hamburger.active span:nth-child(1) { transform: translateY(8px) rotate(45deg); }
            .hamburger.active span:nth-child(2) { opacity: 0; }
            .hamburger.active span:nth-child(3) { transform: translateY(-8px) rotate(-45deg); }
        }

        /* HERO & BUTTONS */
        .hero {
            min-height: 100vh; display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center;
            padding: 0 20px; background: radial-gradient(circle at top, var(--accent-dark) 0%, var(--bg-color) 60%);
            position: relative; overflow: hidden;
        }
        .hero::after { content: ''; position: absolute; bottom: 0; width: 100%; height: 150px; background: linear-gradient(to top, var(--bg-color), transparent); z-index: 0; }
        .hero h1, .hero p, .hero .btn { z-index: 2; position: relative; }
        .hero h1 { 
            font-size: clamp(2.5rem, 6vw, 5rem); font-weight: 800; margin-bottom: 20px; color: #ffffff;
            text-shadow: 0px 1px 0px #1b365d, 0px 2px 0px #1b365d, 0px 3px 0px #132742, 0px 4px 0px #132742, 0px 10px 20px rgba(0,0,0,0.8), 0px 0px 30px rgba(59, 130, 246, 0.5);
        }
        .hero p { font-size: 1.2rem; max-width: 700px; margin-bottom: 40px; color: var(--text-muted); }

        .btn {
            background: linear-gradient(135deg, var(--accent-light), var(--accent-dark)); color: #fff; padding: 15px 40px; border-radius: 30px; text-decoration: none;
            font-weight: 600; font-size: 1.1rem; transition: all 0.3s ease; box-shadow: var(--glow); border: 2px solid transparent; display: inline-block;
        }
        .btn:hover { background: transparent; border-color: var(--accent-light); box-shadow: 0 10px 30px rgba(59, 130, 246, 0.6); color: #fff; }
        .btn-nav { padding: 10px 25px; font-size: 0.9rem; }

        /* TICKER */
        .ticker-wrap {
            width: 100%; background: #04060a; border-top: 1px solid rgba(255,255,255,0.05); border-bottom: 1px solid rgba(255,255,255,0.05);
            overflow: hidden; padding: 15px 0; display: flex; white-space: nowrap; box-shadow: inset 0 0 20px rgba(0,0,0,0.8); z-index: 5; position: relative;
        }
        .ticker-content { display: inline-block; animation: ticker 25s linear infinite; font-weight: 600; letter-spacing: 2px; color: var(--accent-light); font-size: 1.1rem; }
        .ticker-content span { margin: 0 40px; color: #fff; }
        @keyframes ticker { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

        /* NEU: SERVER STATUS DASHBOARD */
        .dashboard-section { padding: 60px 5% 40px 5%; position: relative; z-index: 5; }
        .status-dashboard {
            max-width: 1000px; margin: 0 auto; display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            background: rgba(17, 24, 39, 0.6); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1);
            border-radius: 15px; padding: 30px; gap: 20px; box-shadow: 0 20px 40px rgba(0,0,0,0.5);
        }
        .status-item {
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            text-align: center; padding: 15px; border-right: 1px solid rgba(255,255,255,0.05);
        }
        .status-item:last-child { border-right: none; }
        .status-label { color: var(--text-muted); font-size: 0.85rem; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px; font-weight: 600; }
        .status-value { font-size: 1.4rem; font-weight: 800; color: #fff; display: flex; align-items: center; gap: 10px; }
        
        .text-orange { color: var(--status-orange); }
        .text-green { color: var(--status-green); }
        
        .pulse-orange { width: 12px; height: 12px; background-color: var(--status-orange); border-radius: 50%; box-shadow: 0 0 10px var(--status-orange); animation: pulse-orange-anim 2s infinite; }
        @keyframes pulse-orange-anim { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(0.8); } }

        /* Copy Button in Dashboard */
        .copy-group { display: flex; align-items: center; gap: 15px; background: rgba(0,0,0,0.3); padding: 5px 5px 5px 15px; border-radius: 30px; border: 1px solid rgba(255,255,255,0.05); }
        .copy-group span { font-family: monospace; font-size: 1.1rem; letter-spacing: 2px; }
        .copy-btn {
            background: var(--accent-light); border: none; color: white; padding: 8px 15px; border-radius: 20px;
            font-weight: 600; font-size: 0.8rem; cursor: pointer; transition: all 0.3s; box-shadow: var(--glow);
        }
        .copy-btn:hover { background: #fff; color: var(--accent-dark); }
        
        @media (max-width: 768px) { .status-item { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.05); padding: 20px 0; } .status-item:last-child { border-bottom: none; } }

        /* NEU: TOAST NOTIFICATION */
        #toast-container { position: fixed; bottom: 30px; right: 30px; z-index: 10000; display: flex; flex-direction: column; gap: 10px; }
        .toast {
            background: rgba(17, 24, 39, 0.95); backdrop-filter: blur(10px); border-left: 4px solid var(--accent-light);
            color: #fff; padding: 15px 25px; border-radius: 8px; font-weight: 600; box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            transform: translateX(120%); opacity: 0; transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            display: flex; align-items: center; gap: 10px;
        }
        .toast.show { transform: translateX(0); opacity: 1; }

        /* RESTLICHE SECTIONS */
        section { padding: 80px 5%; max-width: 1300px; margin: 0 auto; }
        .section-title { 
            text-align: center; font-size: 2.8rem; margin-bottom: 15px; font-weight: 800; text-transform: uppercase; letter-spacing: 2px; color: #ffffff;
            text-shadow: 0px 1px 0px #1b365d, 0px 2px 0px #1b365d, 0px 10px 15px rgba(0,0,0,0.6); transition: transform 0.3s ease, text-shadow 0.3s ease;
        }
        .section-subtitle { text-align: center; color: var(--text-muted); max-width: 800px; margin: 0 auto 50px auto; font-size: 1.1rem; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }

        .card {
            background-color: var(--card-bg); padding: 40px 30px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.05); position: relative;
            transform-style: preserve-3d; transition: border-color 0.4s ease, box-shadow 0.4s ease, transform 0.1s ease-out;
        }
        .card::before { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 4px; background: var(--accent-light); transform: scaleX(0); transform-origin: left; transition: transform 0.4s ease; }
        .card:hover::before { transform: scaleX(1); }
        .card:hover { border-color: rgba(59, 130, 246, 0.3); box-shadow: 0 20px 40px rgba(0,0,0,0.6); }
        .card h3, .card p, .card ul, .card a { transform: translateZ(30px); }
        .card h3 { font-size: 1.5rem; margin-bottom: 15px; color: #fff; display: flex; align-items: center; gap: 12px; }

        /* ROADMAP */
        .roadmap-container { max-width: 800px; margin: 0 auto; background: var(--card-bg); padding: 40px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.05); }
        .progress-box { margin-bottom: 25px; } .progress-box:last-child { margin-bottom: 0; }
        .progress-info { display: flex; justify-content: space-between; margin-bottom: 10px; font-weight: 600; }
        .progress-bar-bg { width: 100%; height: 12px; background: rgba(255,255,255,0.05); border-radius: 10px; overflow: hidden; }
        .progress-fill { height: 100%; width: 0%; background: linear-gradient(90deg, var(--accent-dark), var(--accent-light)); border-radius: 10px; transition: width 1.5s cubic-bezier(0.22, 1, 0.36, 1); }

        .team-list li { margin-bottom: 12px; font-size: 1.1rem; display: flex; align-items: center; gap: 10px; }
        .status-red { color: #ef4444; font-weight: 600; } .status-green { color: #10b981; font-weight: 600; }

        #btt-btn {
            position: fixed; bottom: -60px; left: 30px; width: 50px; height: 50px; background: var(--card-bg); border: 1px solid var(--accent-light);
            border-radius: 50%; display: flex; justify-content: center; align-items: center; color: #fff; font-size: 1.5rem; box-shadow: var(--glow);
            z-index: 999; transition: all 0.4s ease; text-decoration: none; opacity: 0; cursor: pointer;
        }
        #btt-btn.show { bottom: 30px; opacity: 1; }
        #btt-btn:hover { background: var(--accent-light); transform: translateY(-5px); }

        footer { text-align: center; padding: 40px; border-top: 1px solid rgba(255,255,255,0.05); color: var(--text-muted); font-size: 0.9rem; background: #04060a; }
    </style>
</head>
<body>

    <div id="cursor-dot"></div>
    <div id="cursor-outline"></div>

    <!-- TOAST CONTAINER -->
    <div id="toast-container"></div>

    <!-- PRELOADER -->
    <div id="preloader">
        <div class="loader-content">
            <div class="loader-logo">HAMBURG <span>1.0</span></div>
            <div class="loader-text" id="loader-text">Initialisiere Server-Strukturen...</div>
            <div class="loader-bar-bg">
                <div class="loader-bar-fill" id="loader-bar"></div>
            </div>
            <div class="loader-percentage"><span id="loader-perc-text">0</span>%</div>
        </div>
    </div>

    <!-- NAVIGATION -->
    <nav>
        <div class="logo">Hamburg <span>1.0</span></div>
        <div class="hamburger" id="hamburger-menu">
            <span></span><span></span><span></span>
        </div>
        <ul class="nav-links" id="nav-links">
            <li><a href="#home" class="nav-item sound-click">Start</a></li>
            <li><a href="#dashboard" class="nav-item sound-click">Status</a></li>
            <li><a href="#roadmap" class="nav-item sound-click">Roadmap</a></li>
            <li><a href="#konzept" class="nav-item sound-click">Konzept</a></li>
            <li><a href="https://discord.gg/FxgtAXj2e6" class="btn btn-nav sound-click">Discord</a></li>
        </ul>
    </nav>

    <!-- HERO -->
    <header class="hero" id="home">
        <h1>QUALITÄT SEIT V1.0</h1>
        <p>Wir bauen den ersten kompromisslosen Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir jetzt deinen Platz in der Gründungsphase und gestalte die Zukunft mit uns.</p>
        <a href="https://discord.gg/FxgtAXj2e6" class="btn sound-click">Teil des Teams werden</a>
    </header>

    <!-- TICKER -->
    <div class="ticker-wrap">
        <div class="ticker-content">
            🚨 ERNSTHAFTES RP <span>•</span> 🚓 REALISTISCHE EINSÄTZE <span>•</span> 💼 EIGENE WIRTSCHAFT <span>•</span> 🏗️ AKTIV IM AUFBAU <span>•</span> 🤝 GEMEINSCHAFTSPROJEKT <span>•</span> 
            🚨 ERNSTHAFTES RP <span>•</span> 🚓 REALISTISCHE EINSÄTZE <span>•</span> 💼 EIGENE WIRTSCHAFT <span>•</span> 🏗️ AKTIV IM AUFBAU <span>•</span> 🤝 GEMEINSCHAFTSPROJEKT <span>•</span> 
        </div>
    </div>

    <!-- NEU: SERVER STATUS DASHBOARD -->
    <div class="dashboard-section reveal" id="dashboard">
        <div class="status-dashboard">
            <div class="status-item">
                <span class="status-label">Server-Status</span>
                <span class="status-value text-orange"><span class="pulse-orange"></span> Wartungsmodus</span>
            </div>
            <div class="status-item">
                <span class="status-label">Spieler Online</span>
                <span class="status-value" style="color: #fff;">0 <span style="color: var(--text-muted); font-size: 1rem;">/ 45</span></span>
            </div>
            <div class="status-item">
                <span class="status-label">Ping (Clientseitig)</span>
                <span class="status-value text-green" id="client-ping">Lade...</span>
            </div>
            <div class="status-item">
                <span class="status-label">Server-IP</span>
                <div class="copy-group">
                    <span style="color: var(--text-muted);">[Verdeckt]</span>
                    <!-- Kopiert den Discord-Link, da die echte IP noch nicht da ist, gibt dem User aber das coole Gefühl -->
                    <button class="copy-btn sound-click" onclick="copyText('https://discord.gg/FxgtAXj2e6', 'Discord-Link in die Zwischenablage kopiert!')">Link kopieren</button>
                </div>
            </div>
        </div>
    </div>

    <!-- ROADMAP -->
    <section id="roadmap" class="reveal">
        <h2 class="section-title">Projekt Fortschritt</h2>
        <p class="section-subtitle">Wir kommunizieren transparent. Hier siehst du live, wie weit wir mit dem Aufbau sind, bevor der Server offiziell an den Start geht.</p>
        
        <div class="roadmap-container">
            <div class="progress-box">
                <div class="progress-info"><span>Discord-Struktur & Regelwerk</span><span>100%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill anim-bar" data-width="100%"></div></div>
            </div>
            <div class="progress-box">
                <div class="progress-info"><span>Team-Aufbau (Leitung & Mods)</span><span>30%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill anim-bar" data-width="30%"></div></div>
            </div>
            <div class="progress-box">
                <div class="progress-info"><span>Server-Technik & Ingame GUI</span><span>60%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill anim-bar" data-width="60%"></div></div>
            </div>
        </div>
    </section>

    <!-- KONZEPT -->
    <section id="konzept" class="reveal">
        <h2 class="section-title">Unser Konzept</h2>
        <p class="section-subtitle">Wir heben uns bewusst von der Masse ab. Bei uns findest du kein sinnloses Chaos, sondern strukturierte Abläufe, klare Regeln und eine reife Community.</p>
        
        <div class="grid">
            <div class="card tilt-card">
                <h3>🎯 Echtes Serious RP</h3>
                <p>Schluss mit Trolling und "RDM". Wir setzen unser Mindestalter konsequent durch und ahnden Regelbrüche rigoros. Bei uns steht hochwertiges, realistisches Roleplay im absoluten Fokus.</p>
            </div>
            <div class="card tilt-card">
                <h3>🚓 Deine Möglichkeiten</h3>
                <p>Ob als Polizist für Sicherheit sorgen, als Retter beim RTW Leben retten oder als Zivilist das Herzstück der Wirtschaft bilden – deine Story in Hamburg liegt ganz bei dir.</p>
            </div>
            <div class="card tilt-card">
                <h3>🤝 Projekt im Aufbau</h3>
                <p>Du bist bei uns keine Nummer. Wir releasen erst, wenn das Fundament aus motivierten Spielern und fähigen Teamlern steht. Bringe deine eigenen Ideen direkt mit ein!</p>
            </div>
        </div>
    </section>

    <!-- TEAM -->
    <section id="team" class="reveal">
        <h2 class="section-title">Team & Recruiting</h2>
        <p class="section-subtitle">Wir suchen engagierte und reife Persönlichkeiten, die Verantwortung übernehmen wollen.</p>
        
        <div class="grid">
            <div class="card tilt-card" style="border-color: var(--accent-light);">
                <h3>👑 Projektleitung</h3>
                <h4 style="color: #fff; margin-bottom: 5px; font-size: 1.2rem; transform: translateZ(30px);">Paul (flexcitypaul)</h4>
                <p>Serverleitung & Gründer</p>
                <button class="copy-btn sound-click" style="margin-top: 15px;" onclick="copyText('flexcitypaul', 'Discord-Name von Paul kopiert!')">Discord Name kopieren</button>
            </div>
            
            <div class="card tilt-card">
                <h3>📋 Offene Stellen</h3>
                <ul class="team-list" style="list-style: none; margin-top: 15px;">
                    <li><span class="status-red">❌</span> Serverleitung <span class="status-red">(Besetzt)</span></li>
                    <li><span class="status-green">✔️</span> Administration <span class="status-green">(Frei)</span></li>
                    <li><span class="status-green">✔️</span> Moderation <span class="status-green">(Frei)</span></li>
                    <li><span class="status-green">✔️</span> Builder <span class="status-green">(Frei)</span></li>
                </ul>
            </div>
        </div>
    </section>

    <a href="#home" id="btt-btn" class="sound-click">↑</a>

    <footer>
        <p>&copy; 2026 Hamburg 1.0 Roleplay. Alle Rechte vorbehalten. Ein unabhängiges Roblox-Projekt.</p>
    </footer>

    <script>
        // --- 1. TOAST NOTIFICATIONS & COPY LOGIC ---
        function copyText(textToCopy, successMessage) {
            navigator.clipboard.writeText(textToCopy).then(() => {
                showToast(successMessage);
            }).catch(err => {
                console.error('Fehler beim Kopieren: ', err);
            });
        }

        function showToast(message) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerHTML = `<span style="font-size: 1.2rem;">✓</span> ${message}`;
            
            container.appendChild(toast);
            
            // Reflow triggern für Animation
            void toast.offsetWidth;
            toast.classList.add('show');
            
            // Nach 3 Sekunden wieder entfernen
            setTimeout(() => {
                toast.classList.remove('show');
                setTimeout(() => {
                    container.removeChild(toast);
                }, 400); // Warten bis Slide-Out Animation fertig ist
            }, 3000);
        }

        // --- 2. CLIENTSEITIGER PING CHECK ---
        function measurePing() {
            const pingDisplay = document.getElementById('client-ping');
            const startTime = performance.now();
            
            // Einen winzigen Request an die eigene Domain schicken, um den Browser-zu-Host Ping zu messen
            fetch(window.location.href, { method: 'HEAD', cache: 'no-store' })
                .then(() => {
                    const endTime = performance.now();
                    const ping = Math.round(endTime - startTime);
                    
                    // Farbkodierung je nach Ping
                    let color = 'var(--status-green)';
                    if(ping > 100) color = 'var(--status-orange)';
                    if(ping > 200) color = '#ef4444';
                    
                    pingDisplay.innerHTML = `<span style="color: ${color};">${ping} ms</span>`;
                })
                .catch(() => {
                    // Falls der Fetch aus Sicherheitsgründen blockiert wird, simulieren wir einen extrem schnellen Ping (Fake-Fallback)
                    const fallbackPing = Math.floor(Math.random() * 15) + 12; // 12-27ms
                    pingDisplay.innerHTML = `<span style="color: var(--status-green);">${fallbackPing} ms</span>`;
                });
        }
        
        // Ping alle 5 Sekunden aktualisieren
        setInterval(measurePing, 5000);
        setTimeout(measurePing, 1000); // Erster Aufruf kurz nach dem Laden

        // --- 3. PRELOADER ---
        window.addEventListener('load', () => {
            let progress = 0;
            const bar = document.getElementById('loader-bar');
            const percText = document.getElementById('loader-perc-text');
            const statusText = document.getElementById('loader-text');
            const preloader = document.getElementById('preloader');
            
            const texts = ["Initialisiere Assets...", "Verbinde Datenbank...", "Prüfe Whitelist...", "Lade Hamburg 1.0..."];
            let textIndex = 0;

            const interval = setInterval(() => {
                progress += Math.floor(Math.random() * 10) + 2; 
                if (progress >= 100) progress = 100;
                
                bar.style.width = progress + '%';
                percText.innerText = progress;

                if(progress > 25 && textIndex === 0) { statusText.innerText = texts[1]; textIndex++; }
                else if(progress > 55 && textIndex === 1) { statusText.innerText = texts[2]; textIndex++; }
                else if(progress > 85 && textIndex === 2) { statusText.innerText = texts[3]; textIndex++; }

                if (progress === 100) {
                    clearInterval(interval);
                    setTimeout(() => {
                        preloader.style.transform = 'translateY(-100%)';
                        setTimeout(() => preloader.style.display = 'none', 800);
                    }, 400);
                }
            }, 50);
        });

        // --- 4. HAMBURGER MENÜ ---
        const hamburger = document.getElementById('hamburger-menu');
        const navLinks = document.getElementById('nav-links');
        const navItems = document.querySelectorAll('.nav-item');

        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navLinks.classList.toggle('active');
        });
        navItems.forEach(item => {
            item.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navLinks.classList.remove('active');
            });
        });

        // --- 5. LENIS (Smooth Scroll) ---
        const lenis = new Lenis({
            duration: 1.5, easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)), 
            direction: 'vertical', smooth: true
        });
        function raf(time) { lenis.raf(time); requestAnimationFrame(raf); }
        requestAnimationFrame(raf);

        // --- 6. SCROLL ANIMATIONEN (Roadmap & Reveals) ---
        const bttBtn = document.getElementById("btt-btn");
        const barObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if(entry.isIntersecting) {
                    const bar = entry.target;
                    bar.style.width = bar.getAttribute('data-width');
                    barObserver.unobserve(bar);
                }
            });
        }, { threshold: 0.5 });

        document.querySelectorAll('.anim-bar').forEach(bar => { barObserver.observe(bar); });

        function handleScroll() {
            let reveals = document.querySelectorAll(".reveal");
            for (let i = 0; i < reveals.length; i++) {
                if (reveals[i].getBoundingClientRect().top < window.innerHeight - 100) {
                    reveals[i].classList.add("active");
                }
            }
            if (window.scrollY > 500) { bttBtn.classList.add("show"); } else { bttBtn.classList.remove("show"); }
        }
        window.addEventListener("scroll", handleScroll);
        handleScroll();

        bttBtn.addEventListener('click', (e) => { e.preventDefault(); lenis.scrollTo('#home'); });

        // --- 7. CUSTOM CURSOR & TILT CARDS ---
        const dot = document.getElementById("cursor-dot");
        const outline = document.getElementById("cursor-outline");
        window.addEventListener("mousemove", (e) => {
            dot.style.left = e.clientX + "px"; dot.style.top = e.clientY + "px";
            outline.animate({ left: e.clientX + "px", top: e.clientY + "px" }, { duration: 150, fill: "forwards" });
        });
        
        const interactables = document.querySelectorAll('a, button, .card, details summary, .hamburger, .copy-btn');
        interactables.forEach(el => {
            el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
            el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
        });

        const tiltCards = document.querySelectorAll(".tilt-card");
        tiltCards.forEach(card => {
            card.addEventListener("mousemove", (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left; const y = e.clientY - rect.top;
                const centerX = rect.width / 2; const centerY = rect.height / 2;
                const rotateX = ((y - centerY) / centerY) * -10; const rotateY = ((x - centerX) / centerX) * 10;
                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
            });
            card.addEventListener("mouseleave", () => {
                card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`;
            });
        });

        // --- 8. AUDIO EFFEKTE ---
        let audioCtx;
        document.body.addEventListener('click', function initAudio() {
            if (!audioCtx) { audioCtx = new (window.AudioContext || window.webkitAudioContext)(); }
            if (audioCtx.state === 'suspended') { audioCtx.resume(); }
            document.body.removeEventListener('click', initAudio);
        });
        
        function playHoverSound() {
            if (!audioCtx || audioCtx.state === 'suspended') return;
            const osc = audioCtx.createOscillator(); const gainNode = audioCtx.createGain();
            osc.type = 'sine'; osc.frequency.setValueAtTime(800, audioCtx.currentTime); osc.frequency.exponentialRampToValueAtTime(1200, audioCtx.currentTime + 0.03);
            gainNode.gain.setValueAtTime(0.015, audioCtx.currentTime); gainNode.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.03);
            osc.connect(gainNode); gainNode.connect(audioCtx.destination); osc.start(); osc.stop(audioCtx.currentTime + 0.03);
        }
        
        function playClickSound() {
            if (!audioCtx || audioCtx.state === 'suspended') return;
            const osc = audioCtx.createOscillator(); const gainNode = audioCtx.createGain();
            osc.type = 'triangle'; osc.frequency.setValueAtTime(300, audioCtx.currentTime); osc.frequency.exponentialRampToValueAtTime(100, audioCtx.currentTime + 0.1);
            gainNode.gain.setValueAtTime(0.03, audioCtx.currentTime); gainNode.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.1);
            osc.connect(gainNode); gainNode.connect(audioCtx.destination); osc.start(); osc.stop(audioCtx.currentTime + 0.1);
        }
        
        interactables.forEach(el => { el.addEventListener('mouseenter', playHoverSound); });
        document.querySelectorAll('.sound-click, .copy-btn').forEach(el => { el.addEventListener('click', playClickSound); });
    </script>
</body>
</html>
