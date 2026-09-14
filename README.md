<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hamburg 1.0 Roleplay | Roblox Notruf Hamburg</title>

    <!-- Discord & Social Media Embed -->
    <meta property="og:title" content="Hamburg 1.0 Roleplay | Notruf Hamburg">
    <meta property="og:description" content="Wir bauen den ersten Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir deinen Platz im Team oder als Spieler!">
    <meta property="og:image" content="https://images-ext-1.discordapp.net/external/LhY2dwlnsWtWn1Gry4pQnq_VSC66gNHwTypoEXoxOzc/https/media.galaxybot.app/server/1548738485324619907/f0346fa9-dd0d-4f74-bef2-a3d9fe88af6d.jpeg?format=webp">
    <meta property="og:url" content="https://2026createt.github.io/Hamburg-Roleplay-1.0/">
    <meta name="theme-color" content="#1b365d">

    <!-- Favicon -->
    <link rel="icon" type="image/png" href="HIER_LOGO_URL_EINTRAGEN.png">

    <!-- Moderne Google Schriftart importieren -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&display=swap" rel="stylesheet">

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
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        /* 1. EIGENER SCROLLBALKEN (Custom Scrollbar) */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-color); }
        ::-webkit-scrollbar-thumb { background: var(--accent-dark); border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--accent-light); }

        /* 2. EIGENER MAUSZEIGER (Versteckt Standard-Maus) */
        @media (pointer: fine) {
            body { cursor: none; }
            a, button, .card, details summary, iframe { cursor: none; }
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
        /* Wenn man über Buttons fährt (Hover-Effekt) */
        .cursor-hover #cursor-outline {
            width: 50px; height: 50px; background: rgba(59, 130, 246, 0.1); border-color: transparent;
        }
        .cursor-hover #cursor-dot { width: 0; height: 0; }

        body {
            background-color: var(--bg-color); color: var(--text-main);
            line-height: 1.7; overflow-x: hidden;
        }

        /* Ladebildschirm (Preloader) */
        #preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at center, #111827 0%, #04060a 100%);
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            z-index: 9999; transition: opacity 0.8s ease-out, visibility 0.8s ease-out;
        }
        .preloader-content { position: relative; display: flex; justify-content: center; align-items: center; }
        .preloader-content::before {
            content: ''; position: absolute; width: 140%; height: 140%;
            background: radial-gradient(circle, rgba(59, 130, 246, 0.4) 0%, transparent 60%);
            z-index: -1; animation: preloader-glow 2s infinite ease-in-out;
        }
        .preloader-img {
            max-width: 400px; width: 90%; border-radius: 15px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8); border: 1px solid rgba(255,255,255,0.05);
            animation: preloader-pulse 2s infinite ease-in-out;
        }
        @keyframes preloader-glow { 0%, 100% { transform: scale(0.8); opacity: 0.5; } 50% { transform: scale(1.1); opacity: 1; } }
        @keyframes preloader-pulse { 0%, 100% { transform: scale(0.98); } 50% { transform: scale(1.02); } }

        /* Scroll Animation Klassen */
        .reveal { opacity: 0; transform: translateY(50px); transition: all 0.8s ease-out; }
        .reveal.active { opacity: 1; transform: translateY(0); }

        /* Navigation */
        nav {
            position: fixed; top: 0; width: 100%; padding: 20px 5%;
            display: flex; justify-content: space-between; align-items: center;
            background: rgba(6, 9, 15, 0.9); backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.05); z-index: 1000;
        }
        .logo { font-size: 1.5rem; font-weight: 800; letter-spacing: 2px; text-transform: uppercase; }
        .logo span { color: var(--accent-light); }

        /* Status Badge */
        .status-badge {
            display: inline-flex; align-items: center; gap: 10px;
            background: rgba(245, 158, 11, 0.1); color: var(--status-orange);
            padding: 8px 16px; border-radius: 30px; font-size: 0.9rem; font-weight: 600;
            margin-bottom: 25px; border: 1px solid rgba(245, 158, 11, 0.3); z-index: 1;
        }
        .pulse {
            width: 10px; height: 10px; background-color: var(--status-orange); border-radius: 50%;
            animation: pulse-animation 2s infinite;
        }
        @keyframes pulse-animation { 0%, 100% { box-shadow: 0 0 0 0 rgba(245, 158, 11, 0); } 50% { box-shadow: 0 0 0 10px rgba(245, 158, 11, 0.4); } }

        /* Hero Section mit Partikeln */
        .hero {
            min-height: 100vh; display: flex; flex-direction: column;
            justify-content: center; align-items: center; text-align: center;
            padding: 0 20px; background: radial-gradient(circle at top, var(--accent-dark) 0%, var(--bg-color) 60%);
            position: relative; overflow: hidden;
        }
        .hero::after {
            content: ''; position: absolute; bottom: 0; width: 100%; height: 150px;
            background: linear-gradient(to top, var(--bg-color), transparent); z-index: 0;
        }
        .hero h1, .hero p, .hero .btn, .hero .status-badge { z-index: 2; position: relative; }
        .hero h1 { font-size: clamp(2.5rem, 6vw, 5rem); font-weight: 800; margin-bottom: 20px; text-shadow: var(--glow); }
        .hero p { font-size: 1.2rem; max-width: 700px; margin-bottom: 40px; color: var(--text-muted); }

        /* Partikel Styling */
        .particle {
            position: absolute; bottom: -20px; background: var(--accent-light);
            border-radius: 50%; box-shadow: 0 0 10px var(--accent-light);
            opacity: 0; animation: floatUp linear infinite; z-index: 1;
        }
        @keyframes floatUp {
            0% { transform: translateY(0) scale(1); opacity: 0; }
            20% { opacity: 0.6; }
            80% { opacity: 0.6; }
            100% { transform: translateY(-100vh) scale(0.5); opacity: 0; }
        }

        /* News Ticker Laufband */
        .ticker-wrap {
            width: 100%; background: #04060a; border-top: 1px solid rgba(255,255,255,0.05);
            border-bottom: 1px solid rgba(255,255,255,0.05); overflow: hidden;
            padding: 15px 0; display: flex; white-space: nowrap; box-shadow: inset 0 0 20px rgba(0,0,0,0.8);
        }
        .ticker-content {
            display: inline-block; animation: ticker 25s linear infinite;
            font-weight: 600; letter-spacing: 2px; color: var(--accent-light); font-size: 1.1rem;
        }
        .ticker-content span { margin: 0 40px; color: #fff; }
        @keyframes ticker { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

        /* Buttons */
        .btn {
            background: linear-gradient(135deg, var(--accent-light), var(--accent-dark));
            color: #fff; padding: 15px 40px; border-radius: 30px; text-decoration: none;
            font-weight: 600; font-size: 1.1rem; transition: all 0.3s ease;
            box-shadow: var(--glow); border: 2px solid transparent; display: inline-block;
        }
        .btn:hover { background: transparent; border-color: var(--accent-light); box-shadow: 0 10px 30px rgba(59, 130, 246, 0.6); }

        /* Back-to-Top Button */
        #btt-btn {
            position: fixed; bottom: -60px; right: 30px; width: 50px; height: 50px;
            background: var(--card-bg); border: 1px solid var(--accent-light);
            border-radius: 50%; display: flex; justify-content: center; align-items: center;
            color: #fff; font-size: 1.5rem; box-shadow: var(--glow); z-index: 999;
            transition: all 0.4s ease; text-decoration: none; opacity: 0;
        }
        #btt-btn.show { bottom: 30px; opacity: 1; }
        #btt-btn:hover { background: var(--accent-light); transform: translateY(-5px); }

        /* Sections & Cards */
        section { padding: 80px 5%; max-width: 1300px; margin: 0 auto; }
        .section-title { text-align: center; font-size: 2.5rem; margin-bottom: 15px; font-weight: 800; text-transform: uppercase; letter-spacing: 1px; }
        .section-subtitle { text-align: center; color: var(--text-muted); max-width: 800px; margin: 0 auto 50px auto; font-size: 1.1rem; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }

        /* 3D Karten Setup */
        .card {
            background-color: var(--card-bg); padding: 40px 30px; border-radius: 12px;
            border: 1px solid rgba(255,255,255,0.05); position: relative;
            transform-style: preserve-3d; /* Wichtig für den 3D Effekt */
            transition: border-color 0.4s ease, box-shadow 0.4s ease, transform 0.1s ease-out; /* Kein Transform All hier, JS regelt das */
        }
        .card::before {
            content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 4px;
            background: var(--accent-light); transform: scaleX(0); transform-origin: left; transition: transform 0.4s ease;
        }
        .card:hover::before { transform: scaleX(1); }
        .card:hover { border-color: rgba(59, 130, 246, 0.3); box-shadow: 0 20px 40px rgba(0,0,0,0.6); }
        .card h3, .card p, .card ul, .card a { transform: translateZ(30px); /* Hebt den Text leicht ab */ }
        .card h3 { font-size: 1.5rem; margin-bottom: 15px; color: #fff; display: flex; align-items: center; gap: 12px; }

        /* Roadmap, Partner, Team, FAQ... (Restliche Styles unverändert stark) */
        .roadmap-container { max-width: 800px; margin: 0 auto; background: var(--card-bg); padding: 40px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.05); }
        .progress-box { margin-bottom: 25px; } .progress-box:last-child { margin-bottom: 0; }
        .progress-info { display: flex; justify-content: space-between; margin-bottom: 10px; font-weight: 600; }
        .progress-bar-bg { width: 100%; height: 12px; background: rgba(255,255,255,0.05); border-radius: 10px; overflow: hidden; }
        .progress-fill { height: 100%; background: linear-gradient(90deg, var(--accent-dark), var(--accent-light)); border-radius: 10px; }
        
        .partner-grid { display: flex; flex-wrap: wrap; justify-content: center; gap: 30px; }
        .partner-card {
            background: var(--card-bg); width: 250px; height: 120px; border-radius: 12px;
            border: 1px dashed rgba(255,255,255,0.2); display: flex; justify-content: center; align-items: center;
            color: var(--text-muted); font-weight: 600; text-align: center; padding: 20px;
            transition: all 0.3s ease; text-decoration: none;
        }
        .partner-card:hover { border-color: var(--accent-light); color: #fff; transform: translateY(-5px); }
        .partner-card.disabled { cursor: default; } .partner-card.disabled:hover { transform: none; border-color: rgba(255,255,255,0.2); color: var(--text-muted); }

        .team-list li { margin-bottom: 12px; font-size: 1.1rem; display: flex; align-items: center; gap: 10px; }
        .status-red { color: #ef4444; font-weight: 600; } .status-green { color: #10b981; font-weight: 600; }
        .team-link { color: var(--text-muted); text-decoration: none; font-size: 0.9rem; margin-top: 15px; display: inline-block; transition: color 0.3s; }
        .team-link:hover { color: var(--accent-light); }

        .faq-container { max-width: 800px; margin: 0 auto; }
        details { background: var(--card-bg); margin-bottom: 15px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.05); overflow: hidden; }
        summary { padding: 20px; font-size: 1.2rem; font-weight: 600; list-style: none; display: flex; justify-content: space-between; align-items: center; }
        summary::after { content: '+'; font-size: 1.5rem; color: var(--accent-light); transition: transform 0.3s; }
        details[open] summary::after { transform: rotate(45deg); }
        details p { padding: 0 20px 20px 20px; color: var(--text-muted); }

        .discord-section {
            display: flex; flex-wrap: wrap; align-items: center; gap: 50px;
            background: var(--card-bg); padding: 50px; border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05); margin-top: 20px;
        }
        .discord-text { flex: 1; min-width: 300px; } .discord-text h2 { font-size: 2.2rem; margin-bottom: 20px; }
        .discord-text ul { list-style: none; margin-bottom: 30px; } .discord-text li { margin-bottom: 10px; padding-left: 30px; position: relative; color: var(--text-muted); }
        .discord-text li::before { content: '✔️'; position: absolute; left: 0; top: 0; }
        .discord-widget { flex: 1; min-width: 350px; display: flex; justify-content: center; }

        footer { text-align: center; padding: 40px; border-top: 1px solid rgba(255,255,255,0.05); color: var(--text-muted); font-size: 0.9rem; background: #04060a; }
    </style>
</head>
<body>

    <!-- Benutzerdefinierter Mauszeiger -->
    <div id="cursor-dot"></div>
    <div id="cursor-outline"></div>

    <!-- LADEBILDSCHIRM -->
    <div id="preloader">
        <div class="preloader-content">
            <img src="https://images-ext-1.discordapp.net/external/LhY2dwlnsWtWn1Gry4pQnq_VSC66gNHwTypoEXoxOzc/https/media.galaxybot.app/server/1548738485324619907/f0346fa9-dd0d-4f74-bef2-a3d9fe88af6d.jpeg?format=webp" alt="Hamburg 1.0 Roleplay Logo" class="preloader-img">
        </div>
    </div>

    <!-- Navigation -->
    <nav>
        <div class="logo">Hamburg <span>1.0</span></div>
        <a href="https://discord.gg/FxgtAXj2e6" class="btn" style="padding: 10px 25px; font-size: 0.9rem;">Jetzt Joinen</a>
    </nav>

    <!-- Startbereich -->
    <header class="hero" id="home">
        <!-- Partikel Container wird per JS gefüllt -->
        <div id="particles-container"></div>
        
        <div class="status-badge">
            <span class="pulse"></span> 🚧 Status: In der Gründungsphase
        </div>
        <h1>QUALITÄT SEIT V1.0</h1>
        <p>Wir bauen den ersten kompromisslosen Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir jetzt deinen Platz in der Gründungsphase und gestalte die Zukunft der Stadt mit uns.</p>
        <a href="https://discord.gg/FxgtAXj2e6" class="btn">Teil des Teams werden</a>
    </header>

    <!-- News Ticker -->
    <div class="ticker-wrap">
        <div class="ticker-content">
            <!-- Zweimal der gleiche Inhalt für einen flüssigen Endlos-Loop -->
            🚨 ERNSTHAFTES RP <span>•</span> 🚓 REALISTISCHE EINSÄTZE <span>•</span> 💼 EIGENE WIRTSCHAFT <span>•</span> 🏗️ AKTIV IM AUFBAU <span>•</span> 🤝 GEMEINSCHAFTSPROJEKT <span>•</span> 
            🚨 ERNSTHAFTES RP <span>•</span> 🚓 REALISTISCHE EINSÄTZE <span>•</span> 💼 EIGENE WIRTSCHAFT <span>•</span> 🏗️ AKTIV IM AUFBAU <span>•</span> 🤝 GEMEINSCHAFTSPROJEKT <span>•</span> 
        </div>
    </div>

    <!-- Entwicklungs-Roadmap -->
    <section id="roadmap" class="reveal">
        <h2 class="section-title">Projekt Fortschritt</h2>
        <p class="section-subtitle">Wir kommunizieren transparent. Hier siehst du live, wie weit wir mit dem Aufbau sind, bevor der Server offiziell an den Start geht.</p>
        
        <div class="roadmap-container">
            <div class="progress-box">
                <div class="progress-info"><span>Discord-Struktur & Regelwerk</span><span>100%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill" style="width: 100%;"></div></div>
            </div>
            <div class="progress-box">
                <div class="progress-info"><span>Team-Aufbau (Leitung & Mods)</span><span>30%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill" style="width: 30%;"></div></div>
            </div>
            <div class="progress-box">
                <div class="progress-info"><span>Server-Technik & Vorbereitung</span><span>60%</span></div>
                <div class="progress-bar-bg"><div class="progress-fill" style="width: 60%;"></div></div>
            </div>
        </div>
    </section>

    <!-- Konzept -->
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

    <!-- Team & Recruiting -->
    <section id="team" class="reveal">
        <h2 class="section-title">Team & Recruiting</h2>
        <p class="section-subtitle">Wir suchen engagierte und reife Persönlichkeiten, die Verantwortung übernehmen wollen. Komm ins Team!</p>
        
        <div class="grid">
            <div class="card tilt-card" style="border-color: var(--accent-light);">
                <h3>👑 Projektleitung</h3>
                <h4 style="color: #fff; margin-bottom: 5px; font-size: 1.2rem;">Paul (flexcitypaul)</h4>
                <p>Serverleitung & Gründer</p>
                <a href="https://discordapp.com/users/1404543050922987611" class="team-link" target="_blank">🔗 Discord Profil ansehen</a>
            </div>
            
            <div class="card tilt-card">
                <h3>📋 Offene Stellen</h3>
                <ul class="team-list" style="list-style: none; margin-top: 15px;">
                    <li><span class="status-red">❌</span> Serverleitung <span class="status-red">(Besetzt)</span></li>
                    <li><span class="status-red">❌</span> Stv. Serverleitung <span class="status-red">(Besetzt)</span></li>
                    <li><span class="status-green">✔️</span> Administration <span class="status-green">(Frei)</span></li>
                    <li><span class="status-green">✔️</span> Moderation <span class="status-green">(Frei)</span></li>
                    <li><span class="status-green">✔️</span> Support & Technik <span class="status-green">(Frei)</span></li>
                    <li><span class="status-green">✔️</span> Builder <span class="status-green">(Frei)</span></li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Unsere Partner -->
    <section id="partner" class="reveal">
        <h2 class="section-title">Unsere Partner</h2>
        <p class="section-subtitle">Wir arbeiten mit anderen großartigen Projekten zusammen. Willst du Partner werden? Melde dich!</p>
        <div class="partner-grid">
            <a href="https://discord.gg/BmAJErtxEU" target="_blank" class="partner-card">Xcom</a>
            <div class="partner-card disabled">Dein Server hier? Ticket öffnen!</div>
        </div>
    </section>

    <!-- FAQ Bereich -->
    <section id="faq" class="reveal">
        <h2 class="section-title">Häufige Fragen (FAQ)</h2>
        <div class="faq-container">
            <details>
                <summary>Was ist das Mindestalter auf dem Server?</summary>
                <p>Da wir großen Wert auf geistige Reife und seriöses RP legen, setzen wir ein Mindestalter konsequent durch. Genaue Details dazu findest du auf unserem Discord.</p>
            </details>
            <details>
                <summary>Brauche ich ein funktionierendes Mikrofon?</summary>
                <p>Ja, absolut. Für ein realistisches und flüssiges Roleplay ist die Kommunikation per Voice-Chat bei uns Pflicht.</p>
            </details>
            <details>
                <summary>Wie kann ich mich als Teamler bewerben?</summary>
                <p>Da viele Plätze aktuell frei sind, kannst du einfach auf unseren Discord joinen und ein Ticket für deine Teambewerbung eröffnen. Wir freuen uns auf dich!</p>
            </details>
        </div>
    </section>

    <!-- Discord & Widget Section -->
    <section id="discord" class="reveal">
        <div class="discord-section">
            <div class="discord-text">
                <h2>Werde Teil von Hamburg 1.0</h2>
                <p style="color: var(--text-muted); margin-bottom: 20px;">
                    Wir warten gezielt auf genügend Spieler und Teammitglieder, bevor der Release startet. Komm auf unseren Discord und erstelle dein Ticket für die Whitelist oder als Teamler!
                </p>
                <h3>Das erwarten wir:</h3><br>
                <ul>
                    <li>Geistige Reife und ein respektvoller Umgang</li>
                    <li>Ein funktionierendes Mikrofon für das Ingame-RP</li>
                    <li>Motivation, eine neue Community mit aufzubauen</li>
                </ul>
                <a href="https://discord.gg/FxgtAXj2e6" class="btn">Zum Discord Server</a>
            </div>
            <div class="discord-widget">
                <iframe src="https://discord.com/widget?id=1548738485324619907&theme=dark" width="350" height="500" allowtransparency="true" frameborder="0" sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts" style="border-radius: 10px; box-shadow: 0 10px 30px rgba(0,0,0,0.5);"></iframe>
            </div>
        </div>
    </section>

    <!-- Back to Top Button -->
    <a href="#home" id="btt-btn">↑</a>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Hamburg 1.0 Roleplay. Alle Rechte vorbehalten. Dies ist ein privates und unabhängiges Roblox-Projekt.</p>
    </footer>

    <!-- SKRIPTE FÜR ALLE EFFEKTE -->
    <script>
        // 1. Preloader
        window.addEventListener('load', () => {
            setTimeout(() => {
                let preloader = document.getElementById('preloader');
                preloader.style.opacity = '0';
                preloader.style.visibility = 'hidden';
            }, 1800);
        });

        // 2. Scroll Animation (Reveal) & Back to Top Button
        const bttBtn = document.getElementById("btt-btn");
        function handleScroll() {
            // Reveal Elemente
            let reveals = document.querySelectorAll(".reveal");
            for (let i = 0; i < reveals.length; i++) {
                if (reveals[i].getBoundingClientRect().top < window.innerHeight - 100) {
                    reveals[i].classList.add("active");
                }
            }
            // Back to Top Button ein/ausblenden
            if (window.scrollY > 500) { bttBtn.classList.add("show"); } 
            else { bttBtn.classList.remove("show"); }
        }
        window.addEventListener("scroll", handleScroll);
        handleScroll();

        // 3. Eigener Mauszeiger (Custom Cursor)
        const dot = document.getElementById("cursor-dot");
        const outline = document.getElementById("cursor-outline");
        window.addEventListener("mousemove", (e) => {
            dot.style.left = e.clientX + "px";
            dot.style.top = e.clientY + "px";
            // Outline folgt etwas verzögert (geschmeidiger Effekt)
            outline.animate({
                left: e.clientX + "px",
                top: e.clientY + "px"
            }, { duration: 150, fill: "forwards" });
        });
        // Hover Effekt für klickbare Elemente
        const interactables = document.querySelectorAll('a, button, .card, details summary');
        interactables.forEach(el => {
            el.addEventListener('mouseenter', () => document.body.classList.add('cursor-hover'));
            el.addEventListener('mouseleave', () => document.body.classList.remove('cursor-hover'));
        });

        // 4. 3D Tilt Effekt für die Karten
        const tiltCards = document.querySelectorAll(".tilt-card");
        tiltCards.forEach(card => {
            card.addEventListener("mousemove", (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left; // x Position in der Karte
                const y = e.clientY - rect.top;  // y Position in der Karte
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                
                // Berechne Rotation (max 10 Grad Neigung)
                const rotateX = ((y - centerY) / centerY) * -10; 
                const rotateY = ((x - centerX) / centerX) * 10;
                
                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
            });
            card.addEventListener("mouseleave", () => {
                card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`;
            });
        });

        // 5. Fliegende Lichtpartikel im Hintergrund
        const particlesContainer = document.getElementById('particles-container');
        for (let i = 0; i < 25; i++) {
            let span = document.createElement('span');
            span.classList.add('particle');
            // Zufällige Größe, Position und Geschwindigkeit
            let size = Math.random() * 4 + 2; 
            span.style.width = size + 'px';
            span.style.height = size + 'px';
            span.style.left = Math.random() * 100 + '%';
            span.style.animationDuration = (Math.random() * 10 + 5) + 's'; // 5-15 Sekunden
            span.style.animationDelay = (Math.random() * 5) + 's';
            particlesContainer.appendChild(span);
        }
    </script>
</body>
</html>
