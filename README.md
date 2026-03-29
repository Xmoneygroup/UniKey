<html lang="sq">
<head>
    <meta charset="UTF-8">
   
    <title>UNIKEY - Specialist për Çelësa makinash</title>
    <style>
        /* --- STILI GLOBAL 'DARK TECH' --- */
        :root {
            --bg-dark: #06090f; 
            --bg-panel: #0d1117; 
            --accent-blue: #007bff; 
            --accent-electric: #00f2fe; 
            --text-main: #ffffff;
            --text-muted: #8b949e;
            --font-main: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            font-family: var(--font-main);
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            line-height: 1.6;
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        ul { list-style: none; padding: 0; margin: 0; }

        /* --- HEADER & NAVIGATION RREGULLUAR --- */
        header {
            background-color: rgba(13, 17, 23, 0.95);
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-sizing: border-box;
            border-bottom: 1px solid rgba(255,255,255,0.03);
            backdrop-filter: blur(5px);
        }

        .logo {
            font-size: 28px;
            font-weight: 900;
            color: var(--text-main);
            text-transform: uppercase;
            letter-spacing: 2px;
            font-style: italic;
        }
        .logo span { color: var(--accent-electric); }

        nav ul { 
            display: flex; 
            gap: 30px; 
            align-items: center; /* Kjo e mban 'HOME' ne vije te drejte me te tjerat */
        }
        nav a { 
            font-size: 13px; 
            text-transform: uppercase; 
            color: var(--text-muted); 
            font-weight: 600; 
            letter-spacing: 1px;
            display: inline-block;
            vertical-align: middle;
        }
        nav a:hover { color: var(--accent-electric); }

        .contact-btn {
            background-color: var(--accent-blue);
            color: white;
            padding: 10px 25px;
            border-radius: 5px;
            font-weight: bold;
            font-size: 14px;
            text-transform: uppercase;
        }
        .contact-btn:hover { background-color: #0056b3; transform: translateY(-2px); box-shadow: 0 5px 15px rgba(0,123,255,0.3); }

        /* --- HERO SECTION --- */
        .hero {
            height: 85vh;
            background: radial-gradient(circle at center, #1a2236 0%, var(--bg-dark) 70%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 100px 20px 0 20px;
            position: relative;
        }
        .hero::after {
            content: "";
            position: absolute; bottom: 0; left: 0; width: 100%; height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-electric), transparent);
            box-shadow: 0 0 15px var(--accent-electric);
        }

        .hero h1 {
            font-size: 65px; /* Pak me i madh pasi hoqem Autotech */
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 5px;
            font-weight: 900;
            background: linear-gradient(to bottom, #fff, #bbb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero h1 span { -webkit-text-fill-color: var(--accent-electric); text-shadow: 0 0 20px rgba(0,242,254,0.5); }
        .hero p { font-size: 18px; color: var(--text-muted); max-width: 650px; margin-bottom: 40px; font-weight: 300; }

        /* --- SERVICES DASHBOARD --- */
        .services-dashboard {
            padding: 80px 50px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
            background-color: var(--bg-dark);
        }

        .service-panel {
            background-color: var(--bg-panel);
            border: 1px solid rgba(255,255,255,0.03);
            border-radius: 12px;
            padding: 40px;
            transition: 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            overflow: hidden;
        }

        .service-panel:hover {
            border-color: var(--accent-electric);
            transform: translateY(-8px);
            box-shadow: 0 15px 40px rgba(0,242,254,0.15);
        }

        .service-panel h3 {
            font-size: 24px;
            text-transform: uppercase;
            color: var(--text-main);
            margin: 0 0 20px 0;
            font-weight: 800;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .service-panel h3::before {
            content: ""; display: inline-block; width: 4px; height: 24px; background-color: var(--accent-electric);
            box-shadow: 0 0 10px var(--accent-electric);
        }

        .service-panel p {
            color: var(--text-muted);
            font-size: 15px;
            line-height: 1.7;
            margin-bottom: 30px;
        }

        .panel-link {
            font-size: 13px;
            color: var(--accent-electric);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* --- SECTION: DIAGNOISTIKË --- */
        .diagnostike-tech {
            background-color: var(--bg-panel);
            padding: 100px 50px;
            display: flex;
            align-items: center;
            gap: 60px;
            border-top: 1px solid rgba(255,255,255,0.03);
        }

        .diag-visual {
            flex: 1;
            background-color: rgba(0,0,0,0.2);
            border-radius: 12px;
            padding: 30px;
            height: 320px;
            border: 1px solid rgba(255,255,255,0.05);
            display: flex; align-items: center; justify-content: center;
        }
        
        .diag-visual svg { width: 100%; height: 100%; }

        .diag-text { flex: 1.2; }
        .diag-text h2 { text-transform: uppercase; color: var(--text-main); font-size: 36px; font-weight: 900; margin-bottom: 20px; }
        .diag-text h2 span { color: var(--accent-electric); }
        .diag-text p { color: var(--text-muted); line-height: 1.8; font-size: 16px; }

        /* --- STYLE PER HARTEN (SHTUAR) --- */
        .map-wrapper {
            padding: 50px;
            background-color: var(--bg-dark);
            text-align: center;
        }
        .map-container {
            max-width: 1200px;
            margin: 0 auto;
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .map-container iframe {
            width: 100%;
            display: block;
        }

        /* --- FOOTER & CONTACT --- */
        footer {
            background-color: var(--bg-dark);
            padding: 70px 50px 40px 50px;
            border-top: 1px solid rgba(255,255,255,0.03);
            text-align: center;
        }

        .footer-logo { font-size: 36px; font-weight: 900; text-transform: uppercase; margin-bottom: 15px; font-style: italic; }
        .footer-logo span { color: var(--accent-electric); }

        .contact-card {
            background-color: var(--bg-panel);
            padding: 40px;
            border-radius: 12px;
            display: inline-block;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .contact-name { font-size: 22px; font-weight: 800; color: var(--text-main); margin-bottom: 10px; }
        .contact-phone { font-size: 28px; color: var(--accent-electric); font-family: monospace; font-weight: bold; }

        .copyright { margin-top: 60px; font-size: 12px; color: #444; text-transform: uppercase; }

        /* --- RESPONSIVE --- */
        @media (max-width: 992px) {
            .diagnostike-tech { flex-direction: column; text-align: center; padding: 60px 20px; }
            .hero h1 { font-size: 45px; }
            .map-wrapper { padding: 20px; }
        }

        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 15px; }
            nav ul { gap: 15px; flex-wrap: wrap; justify-content: center; }
            .hero h1 { font-size: 38px; }
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
        <a href="tel:+389070229348" class="contact-btn">TELEFONO TANI</a>
    </header>

    <section id="home" class="hero">
        <h1>UNI<span>KEY</span></h1>
        <p>Specialistë të çertifikuar për kodimin e çelësave inteligjentë, diagnostikë kompjuterike dhe riparimin e bravave për makina moderne.</p>
        <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
    </section>

    <section id="sherbimet" class="services-dashboard">
        <div class="service-panel">
            <div>
                <h3>Kodim Çelësash</h3>
                <p>Programim profesional i çelësave inteligjentë (Smart Keys), transponderëve dhe telekomandave për të gjitha markat e makinave.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>

        <div class="service-panel">
            <div>
                <h3>Mekanizma Dritareve</h3>
                <p>Riparim dhe ndërrim i mekanizmave elektrikë dhe manualë të dritareve të makinave. Siguri dhe funksionalitet i plotë.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>

        <div class="service-panel">
            <div>
                <h3>Brava Makinash</h3>
                <p>Hapje emergjente e makinave pa dëmtim, riparim i bravave të dyerve dhe të ndezjes (ignition), duplikat çelësa.</p>
            </div>
            <a href="tel:+389070229348" class="panel-link">Për Shërbim shpejt →</a>
        </div>
    </section>

    <section id="diagnostike" class="diagnostike-tech">
        <div class="diag-visual">
            <svg viewBox="0 0 400 150" xmlns="http://www.w3.org/2000/svg">
                <path d="M0,75 L400,75" stroke="rgba(255,255,255,0.05)" stroke-width="1"/>
                <path d="M0,75 L50,75 L60,30 L70,120 L80,75 L150,75 L160,50 L170,100 L180,75 L250,75 L260,10 L270,140 L280,75 L350,75 L360,60 L370,90 L380,75 L400,75" 
                      stroke="#00f2fe" stroke-width="3" fill="none" stroke-linecap="round" stroke-linejoin="round">
                      <animate attributeName="stroke-dasharray" from="0,1000" to="1000,0" dur="3s" repeatCount="indefinite" />
                </path>
            </svg>
        </div>
        <div class="diag-text">
            <h2>Diagnoistikë <span>Kompjuterike</span></h2>
            <p>Zbulimi i saktë i problemeve elektronike me sistemet e sigurisë së makinës (Immobilizer, Keyless Go) duke përdorur pajisjet më të fundit diagnoistike.</p>
        </div>
    </section>

    <!-- SECTION: MAPA E SHTUAR ME LINKUN TEND -->
    <div class="map-wrapper">
        <div class="map-container">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2964.6241305752023!2d21.362521075911967!3d42.00834157122769!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x135413a346233fcb%3A0xfaa3925c9659e6b!2zdW5pa2V5INC60LvRg9GH0LDRgA!5e0!3m2!1sen!2smk!4v1774827364470!5m2!1sen!2smk" width="100%" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
    </div>

    <footer id="kontakt">
        <div class="footer-logo">UNI<span>KEY</span></div>
        <div class="contact-card">
            <div class="contact-name">Muhamed Musli</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>
        <div class="copyright">
            &copy; 2026 UNIKEY. All rights reserved.
        </div>
    </footer>

</body>
</html>
