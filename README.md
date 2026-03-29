<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Specialist për Çelësa dhe Brava Makinash</title>
    <style>
        /* --- STILI GLOBAL (inspiruar nga image_1.png) --- */
        :root {
            --bg-dark: #0a0e17; /* E zezë shumë e errët */
            --bg-panel: #111625; /* Pak më e çelët për panelet */
            --accent-blue: #007bff; /* Bluja kryesore */
            --accent-electric: #00f2fe; /* Bluja elektrike për thekse */
            --text-main: #ffffff;
            --text-muted: #a0aab5;
            --font-main: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            font-family: var(--font-main);
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        ul { list-style: none; padding: 0; margin: 0; }

        /* --- HEADER & NAVIGATION --- */
        header {
            background-color: rgba(17, 22, 37, 0.95);
            padding: 15px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-sizing: border-box;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: var(--text-main);
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .logo span { color: var(--accent-electric); }

        nav ul { display: flex; gap: 30px; }
        nav a { font-size: 14px; text-transform: uppercase; color: var(--text-muted); }
        nav a:hover { color: var(--accent-electric); }

        .contact-btn {
            background-color: var(--accent-blue);
            color: white;
            padding: 10px 25px;
            border-radius: 5px;
            font-weight: bold;
            font-size: 14px;
        }
        .contact-btn:hover { background-color: #0056b3; transform: scale(1.05); }

        /* --- HERO SECTION --- */
        .hero {
            height: 80vh;
            /* ZËVENDËSONI KËTË LIDHJE ME NJË FOTO SERIOZE TË NJË MAKINË OSE DASHBOARD */
            background-image: linear-gradient(to bottom, rgba(10,14,23,0.8), var(--bg-dark)), url('https://images.unsplash.com/photo-1549239100-2df6e1331304?q=80&w=1920'); 
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding-top: 100px; /* Hapësirë për header */
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;
        }
        .hero h1 span { color: var(--accent-electric); }
        .hero p { font-size: 18px; color: var(--text-muted); max-width: 600px; margin-bottom: 30px; }

        /* --- SERVICES DASHBOARD (Stili i Paneleve të image_1.png) --- */
        .services-dashboard {
            padding: 60px 50px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            background-color: var(--bg-dark);
        }

        .service-panel {
            background-color: var(--bg-panel);
            border: 1px solid rgba(255,255,255,0.03);
            border-radius: 10px;
            padding: 40px;
            position: relative;
            transition: 0.3s;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .service-panel:hover {
            border-color: var(--accent-electric);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,242,254,0.1);
        }

        /* Imazhi i sfondit për panelin (si te image_1.png) */
        .panel-bg-icon {
            position: absolute;
            bottom: -20px;
            right: -20px;
            opacity: 0.05;
            font-size: 150px;
            color: var(--accent-electric);
            pointer-events: none;
        }

        .service-panel h3 {
            font-size: 22px;
            text-transform: uppercase;
            color: var(--text-main);
            margin-top: 0;
            margin-bottom: 15px;
            border-left: 3px solid var(--accent-electric);
            padding-left: 15px;
        }

        .service-panel p {
            color: var(--text-muted);
            font-size: 15px;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .panel-link {
            font-size: 14px;
            color: var(--accent-electric);
            font-weight: bold;
            text-transform: uppercase;
        }

        /* --- SECTION: DIAGNOISTIKË (Fokus te Teknologjia) --- */
        .diagnostike-tech {
            background-color: var(--bg-panel);
            padding: 80px 50px;
            display: flex;
            align-items: center;
            gap: 50px;
        }

        .diag-chart {
            flex: 1;
            background-color: rgba(0,0,0,0.3);
            border-radius: 10px;
            padding: 20px;
            height: 300px;
            position: relative;
            border: 1px solid rgba(255,255,255,0.05);
            display: flex; align-items: center; justify-content: center; color: #333; font-size: 12px;
        }
        /* Placeholder vizual për grafikun (si te image_1.png) */
        .diag-chart::before {
            content: "DIAGNOSTIC WAVEFORM";
            color: var(--accent-electric);
            font-family: monospace;
            position: absolute; top: 10px; left: 10px;
        }
        .diag-chart::after {
            content: "";
            position: absolute; width: 90%; height: 2px; background: linear-gradient(90deg, transparent, var(--accent-electric), transparent);
            box-shadow: 0 0 10px var(--accent-electric);
        }

        .diag-text { flex: 1; }
        .diag-text h2 { text-transform: uppercase; color: var(--text-main); font-size: 32px; }
        .diag-text h2 span { color: var(--accent-electric); }
        .diag-text p { color: var(--text-muted); line-height: 1.7; }

        /* --- FOOTER & CONTACT (Specifike për kërkesën tuaj) --- */
        footer {
            background-color: var(--bg-panel);
            padding: 50px;
            border-top: 1px solid rgba(255,255,255,0.05);
            text-align: center;
        }

        .footer-logo { font-size: 32px; font-weight: bold; text-transform: uppercase; margin-bottom: 10px; }
        .footer-logo span { color: var(--accent-electric); }
        .footer-tagline { color: var(--text-muted); margin-bottom: 30px; font-size: 14px; }

        .contact-info {
            background-color: rgba(0,0,0,0.2);
            padding: 30px;
            border-radius: 10px;
            display: inline-block;
            border: 1px solid rgba(255,255,255,0.03);
        }
        .contact-name { font-size: 20px; font-weight: bold; color: var(--text-main); margin-bottom: 5px; }
        .contact-phone { font-size: 24px; color: var(--accent-electric); font-family: monospace; }
        .contact-phone a:hover { text-shadow: 0 0 10px var(--accent-electric); }

        .copyright { margin-top: 40px; font-size: 12px; color: #555; }

        /* --- RESPONSIVE DESIGN --- */
        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 10px; text-align: center; }
            nav ul { gap: 15px; flex-wrap: wrap; justify-content: center; }
            .hero h1 { font-size: 32px; }
            .services-dashboard, .diagnostike-tech { padding: 40px 20px; }
            .diagnostike-tech { flex-direction: column; }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">UNI<span>KEY</span></div>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#sherbimet">Shërbimet</a></li>
                <li><a href="#diagnostike">Diagnostikë</a></li>
                <li><a href="#kontakt">Kontakt</a></li>
            </ul>
        </nav>
        <a href="tel:+389070229348" class="contact-btn">NA TELEFONONI</a>
    </header>

    <section id="home" class="hero">
        <h1>UNI<span>KEY</span> PREMIUM</h1>
        <p>Specialistë të çertifikuar për kodimin e çelësave inteligjentë dhe riparimin e mekanizmave të sigurisë për makina moderne.</p>
        <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
    </section>

    <section id="sherbimet" class="services-dashboard">
        
        <div class="service-panel">
            <div class="panel-bg-icon">🔑</div> <div>
                <h3>Kodim Çelësash</h3>
                <p>Programim profesional i çelësave inteligjentë (Smart Keys), transponderëve dhe telekomandave për të gjitha markat e makinave.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>

        <div class="service-panel">
            <div class="panel-bg-icon">🪟</div> <div>
                <h3>Mekanizma Dritareve</h3>
                <p>Riparim dhe ndërrim i mekanizmave elektrikë dhe manualë të dritareve të makinave. Siguri dhe funksionalitet i plotë.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>

        <div class="service-panel">
            <div class="panel-bg-icon">🔒</div> <div>
                <h3>Brava Makinash</h3>
                <p>Hapje emergjente e makinave pa dëmtim, riparim i bravave të dyerve dhe të ndezjes (ignition), duplikat çelësa.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>

    </section>

    <section id="diagnostike" class="diagnostike-tech">
        <div class="diag-chart">
            </div>
        <div class="diag-text">
            <h2>Diagnoistikë <span>Kompjuterike</span></h2>
            <p>Zbulimi i saktë i problemeve elektronike me sistemet e sigurisë së makinës (Immobilizer, Keyless Go) duke përdorur pajisjet më të fundit diagnoistike.</p>
            <p>Ne eliminojmë gabimet dhe sigurojmë që kodimi i çelësit të bëhet në përputhje të plotë me kompjuterin e makinës.</p>
        </div>
    </section>

    <footer id="kontakt">
        <div class="footer-logo">UNI<span>KEY</span></div>
        <p class="footer-tagline">Zgjidhje Profesionale për Çelësa dhe Siguri Automjetesh</p>
        
        <div class="contact-info">
            <div class="contact-name">Muhamed Musili</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>

        <div class="copyright">
            &copy; 2023 UNIKEY. All rights reserved. <br>
            Hosted on GitHub Pages.
        </div>
    </footer>

</body>
</html>
