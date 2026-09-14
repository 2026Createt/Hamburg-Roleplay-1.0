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
    <!-- ERSETZE DIESE URL durch den Link zu deinem kleinen Logo -->
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
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.7;
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
            background: rgba(6, 9, 15, 0.9);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .logo span {
            color: var(--accent-light);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            background: radial-gradient(circle at top, var(--accent-dark) 0%, var(--bg-color) 60%);
            position: relative;
        }

        .hero::after {
            content: '';
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 150px;
            background: linear-gradient(to top, var(--bg-color), transparent);
        }

        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 800;
            margin-bottom: 20px;
            text-shadow: var(--glow);
            z-index: 1;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin-bottom: 40px;
            color: var(--text-muted);
            z-index: 1;
        }

        .btn {
            background: linear-gradient(135deg, var(--accent-light), var(--accent-dark));
            color: #fff;
            padding: 15px 40px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: var(--glow);
            border: 2px solid transparent;
            z-index: 1;
        }

        .btn:hover {
            background: transparent;
            border-color: var(--accent-light);
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(59, 130, 246, 0.6);
        }

        /* Sections General */
        section {
            padding: 100px 5%;
            max-width: 1300px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 20px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .section-subtitle {
            text-align: center;
            color: var(--text-muted);
            max-width: 800px;
            margin: 0 auto 60px auto;
            font-size: 1.1rem;
        }

        /* Grid Cards */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .card {
            background-color: var(--card-bg);
            padding: 40px 30px;
            border-radius: 12px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: var(--accent-light);
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.4s ease;
        }

        .card:hover::before {
            transform: scaleX(1);
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: rgba(59, 130, 246, 0.2);
            box-shadow: 0 15px 30px rgba(0,0,0,0.5);
        }

        .card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #fff;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        /* Info Layout für Discord Widget */
        .discord-section {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 50px;
            background: var(--card-bg);
            padding: 50px;
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05);
            margin-top: 50px;
        }

        .discord-text {
            flex: 1;
            min-width: 300px;
        }

        .discord-text h2 {
            font-size: 2.2rem;
            margin-bottom: 20px;
        }

        .discord-text ul {
            list-style: none;
            margin-bottom: 30px;
        }

        .discord-text li {
            margin-bottom: 10px;
            padding-left: 30px;
            position: relative;
            color: var(--text-muted);
        }

        .discord-text li::before {
            content: '✔️';
            position: absolute;
            left: 0;
            top: 0;
        }

        .discord-widget {
            flex: 1;
            min-width: 350px;
            display: flex;
            justify-content: center;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 40px;
            border-top: 1px solid rgba(255,255,255,0.05);
            color: var(--text-muted);
            font-size: 0.9rem;
            background: #04060a;
        }
    </style>
</head>
<body>

    <!-- Navigation -->
    <nav>
        <div class="logo">Hamburg <span>1.0</span></div>
        <a href="#discord" class="btn" style="padding: 10px 25px; font-size: 0.9rem;">Jetzt Joinen</a>
    </nav>

    <!-- Startbereich -->
    <header class="hero">
        <h1>QUALITÄT SEIT V1.0</h1>
        <p>Wir bauen den ersten kompromisslosen Serious RP Server für Notruf Hamburg auf Roblox. Aktuell im Aufbau – sichere dir jetzt deinen Platz in der Gründungsphase und gestalte die Zukunft der Stadt mit uns.</p>
        <a href="#discord" class="btn">Teil des Teams werden</a>
    </header>

    <!-- Philosophie & Konzept -->
    <section id="konzept">
        <h2 class="section-title">Unser Konzept</h2>
        <p class="section-subtitle">Wir heben uns bewusst von der Masse ab. Bei uns findest du kein sinnloses Chaos, sondern strukturierte Abläufe, klare Regeln und eine reife Community.</p>
        
        <div class="grid">
            <div class="card">
                <h3>🎯 Echtes Serious RP</h3>
                <p>Schluss mit Trolling und "RDM". Wir setzen unser Mindestalter konsequent durch und ahnden Regelbrüche rigoros. Bei uns steht hochwertiges, realistisches und durchdachtes Roleplay im absoluten Fokus.</p>
            </div>
            <div class="card">
                <h3>🏗️ Projekt im Aufbau</h3>
                <p>Du bist bei uns keine Nummer. Wir releasen erst, wenn das Fundament aus motivierten Spielern und fähigen Teamlern steht. Gestalte den Server von Tag eins an mit und bringe deine eigenen Ideen ein!</p>
            </div>
            <div class="card">
                <h3>🤝 Team & Support</h3>
                <p>Egal ob als Moderator, im Support oder in der Server-Technik: Wir suchen engagierte und reife Persönlichkeiten, die Verantwortung übernehmen wollen. Ein fairer Umgang auf Augenhöhe ist uns dabei am wichtigsten.</p>
            </div>
        </div>
    </section>

    <!-- Fraktionen -->
    <section>
        <h2 class="section-title">Deine Möglichkeiten</h2>
        <p class="section-subtitle">Wähle deinen Weg in Hamburg. Welche Rolle übernimmst du in unserer Stadt?</p>
        
        <div class="grid">
            <div class="card">
                <h3>🚓 Polizei Hamburg</h3>
                <p>Sorge für Sicherheit auf den Straßen. Vom einfachen Streifendienst über Verkehrskontrollen bis hin zu Großeinsätzen – koordiniertes Vorgehen und Funkdisziplin stehen hier an der Tagesordnung.</p>
            </div>
            <div class="card">
                <h3>🚑 Feuerwehr & Rettung</h3>
                <p>Rette Leben in brenzligen Situationen. Fahre mit dem RTW zu medizinischen Notfällen, leiste Erste Hilfe oder bekämpfe als Teil der Feuerwehr Brände und technische Gefahren im Stadtgebiet.</p>
            </div>
            <div class="card">
                <h3>🚶 Zivilist & Wirtschaft</h3>
                <p>Das Herzstück der Stadt. Gehe einem normalen Beruf nach, gründe dein eigenes Unternehmen, plane spannende Zivil-Events oder schlage den kriminellen Weg ein – deine Story liegt ganz bei dir.</p>
            </div>
        </div>
    </section>

    <!-- Discord & Widget Section -->
    <section id="discord">
        <div class="discord-section">
            <div class="discord-text">
                <h2>Werde Teil von Hamburg 1.0</h2>
                <p style="color: var(--text-muted); margin-bottom: 20px;">
                    Wir warten gezielt auf genügend Spieler und Teammitglieder, bevor der große Release startet. Komm auf unseren Discord, lies dir das Regelwerk durch und erstelle dein Ticket für die Whitelist oder eine Teambewerbung!
                </p>
                
                <h3>Das erwarten wir:</h3>
                <br>
                <ul>
                    <li>Geistige Reife und ein respektvoller Umgang</li>
                    <li>Ein funktionierendes Mikrofon für das Ingame-RP</li>
                    <li>Motivation, eine neue Community mit aufzubauen</li>
                    <li>Spaß an fairem und realistischem Roleplay</li>
                </ul>

                <!-- ERSETZE DIESEN LINK durch deinen Discord-Einladungslink (z.B. https://discord.gg/...) -->
                <a href="HIER_DISCORD_LINK_EINTRAGEN" class="btn">Zum Discord Server</a>
            </div>
            
            <div class="discord-widget">
                <!-- Dein eingefügtes Discord Widget -->
                <iframe src="https://discord.com/widget?id=1548738485324619907&theme=dark" width="350" height="500" allowtransparency="true" frameborder="0" sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts" style="border-radius: 10px; box-shadow: 0 10px 30px rgba(0,0,0,0.5);"></iframe>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Hamburg 1.0 Roleplay. Alle Rechte vorbehalten. Dies ist ein privates und unabhängiges Roblox-Projekt.</p>
    </footer>

</body>
</html>
