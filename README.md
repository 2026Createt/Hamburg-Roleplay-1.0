<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hamburg 1.0 Roleplay | Roblox Notruf Hamburg</title>

    <!-- Discord & Social Media Embed -->
    <meta property="og:title" content="Hamburg 1.0 Roleplay | Notruf Hamburg">
    <meta property="og:description" content="Wir bauen den ersten Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir deinen Platz im Team oder als Spieler!">
    <!-- ERSETZE DIESE URL durch den echten Link zu deinem Banner-Bild -->
    <meta property="og:image" content="https://images-ext-1.discordapp.net/external/LhY2dwlnsWtWn1Gry4pQnq_VSC66gNHwTypoEXoxOzc/https/media.galaxybot.app/server/1548738485324619907/f0346fa9-dd0d-4f74-bef2-a3d9fe88af6d.jpeg?format=webp">
    <!-- ERSETZE DIESE URL durch die echte Adresse deiner Website -->
    <meta property="og:url" content="https://2026createt.github.io/Hamburg-Roleplay-1.0/">
    <meta name="theme-color" content="#1b365d">

    <!-- Favicon (Das kleine Logo im Browser-Tab) -->
    <!-- ERSETZE DIESE URL durch den Link zu deinem kleinen Logo -->
    <link rel="icon" type="image/png" href="HIER_LOGO_URL_EINTRAGEN.png">

    <style>
        /* Farbpalette und grundlegende Einstellungen */
        :root {
            --bg-color: #0a0e17;
            --card-bg: #111827;
            --text-main: #f3f4f6;
            --text-muted: #9ca3af;
            --accent-dark: #1b365d;
            --accent-light: #3b82f6;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(10, 14, 23, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .logo span {
            color: var(--accent-light);
        }

        /* Hero Section (Startbereich) */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(circle at center, var(--accent-dark) 0%, var(--bg-color) 70%);
        }

        .hero h1 {
            font-size: clamp(3rem, 5vw, 5rem);
            font-weight: 800;
            margin-bottom: 15px;
            letter-spacing: 2px;
            text-shadow: 0 4px 20px rgba(0,0,0,0.5);
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin-bottom: 40px;
            color: var(--text-muted);
        }

        .btn {
            background-color: var(--accent-light);
            color: #fff;
            padding: 15px 35px;
            border-radius: 4px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.3);
            border: 1px solid transparent;
        }

        .btn:hover {
            background-color: transparent;
            border-color: var(--accent-light);
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.2);
        }

        /* Info Grid Section */
        .features {
            padding: 100px 5%;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 60px;
            font-weight: 700;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .card {
            background-color: var(--card-bg);
            padding: 40px 30px;
            border-radius: 8px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: transform 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: rgba(59, 130, 246, 0.3);
        }

        .card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #fff;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card p {
            color: var(--text-muted);
            font-size: 1.05rem;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 30px;
            border-top: 1px solid rgba(255,255,255,0.05);
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 50px;
        }

    </style>
</head>
<body>

    <!-- Navigation -->
    <nav>
        <div class="logo">Hamburg <span>1.0</span></div>
        <!-- ERSETZE DIESEN LINK -->
        <a href="HIER_DISCORD_LINK_EINTRAGEN" class="btn" style="padding: 10px 20px; font-size: 0.9rem; box-shadow: none;">Discord Joinen</a>
    </nav>

    <!-- Startbereich -->
    <header class="hero">
        <h1>Qualität seit V1.0</h1>
        <p>Wir bauen den ersten kompromisslosen Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir jetzt deinen Platz in der Gründungsphase.</p>
        <!-- ERSETZE DIESEN LINK -->
        <a href="HIER_DISCORD_LINK_EINTRAGEN" class="btn">Team & Projekt beitreten</a>
    </header>

    <!-- Infos / Vorteile -->
    <section class="features">
        <h2 class="section-title">Unser Konzept</h2>
        <div class="grid">
            
            <div class="card">
                <h3>🎯 Echtes Serious RP</h3>
                <p>Schluss mit Trolling und Chaos. Wir setzen unser Mindestalter konsequent durch und bannen bei Verstößen rigoros. Bei uns steht echtes, reifes und durchdachtes Roleplay im Fokus.</p>
            </div>

            <div class="card">
                <h3>🏗️ Projekt im Aufbau</h3>
                <p>Du bist nicht einfach Spieler Nummer X. Wir releasen erst, wenn wir eine starke Basis aus motivierten Spielern und fähigen Teamlern haben. Gestalte das Fundament direkt mit!</p>
            </div>

            <div class="card">
                <h3>🤝 Teamler gesucht</h3>
                <p>Egal ob Support, Moderation oder Technik: Wir suchen engagierte Leute, die Lust haben Verantwortung zu übernehmen und das Projekt von der ersten Stunde an zu leiten.</p>
            </div>

        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Hamburg 1.0 Roleplay. Alle Rechte vorbehalten. Dies ist ein privates Roblox-Projekt.</p>
    </footer>

</body>
</html>
