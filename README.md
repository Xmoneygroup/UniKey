<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Specialist për Çelësa makinash</title>
    <style>
        /* --- STILI GLOBAL 'DARK TECH' --- */
        :root {
            --bg-dark: #06090f; /* E zezë absolute */
            --bg-panel: #0d1117; /* E zezë e hirtë për panelet */
            --accent-blue: #007bff; /* Bluja kryesore */
            --accent-electric: #00f2fe; /* Bluja elektrike */
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

        /* --- HEADER & NAVIGATION --- */
        header {
            background-color: rgba(13, 17, 23, 0.95);
            padding: 15px 50px;
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

        nav ul { display: flex; gap: 30px; }
        nav a { font-size: 13px; text-transform: uppercase; color: var(--text-muted); font-weight: 600; letter-spacing: 1px; }
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

        /* --- HERO SECTION (Zëvendësuar me Gradient Profesional) --- */
        .hero {
            height: 85vh;
            /* Gradient radial për efekt dëshire 'Premium' */
            background: radial-gradient(circle at center, #1a2236 0%, var(--bg-dark) 70%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 100px 20px 0 20px;
            position: relative;
        }
        /* Efekt vije elektrike poshtë hero */
        .hero::after {
            content: "";
            position: absolute; bottom: 0; left: 0; width: 100%; height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-electric), transparent);
            box-shadow: 0 0 15px var(--accent-electric);
        }

        .hero h1 {
            font-size: 56px;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 4px;
            font-weight: 900;
            background: linear-gradient(to bottom, #fff, #bbb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero h1 span { -webkit-text-fill-color: var(--accent-electric); text-shadow: 0 0 20px rgba(0,242,254,0.5); }
        .hero p { font-size: 18px; color: var(--text-muted); max-width: 650px; margin-bottom: 40px; font-weight: 300; }

        /* --- SERVICES DASHBOARD (Panele pa foto) --- */
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

        /* Efekti 'Glow' kur kalon miun */
        .service-panel:hover {
            border-color: var(--accent-electric);
            transform: translateY(-8px);
            box-shadow: 0 15px 40px rgba(0,242,254,0.15);
        }

        .service-panel h3 {
            font-size: 24px;
            text-transform: uppercase;
            color: var(--text-main);
            margin-top: 0;
            margin-bottom: 20px;
            font-weight: 800;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        /* Vijë dekorative elektrike anash titullit */
        .service-panel h3::before {
            content: ""; display: inline-block; width: 4px; height: 24px; background-color: var(--accent-electric);
            box-shadow: 0 0 10px var(--accent-electric);
        }

        .service-panel p {
            color: var(--text-muted);
            font-size: 15px;
            line-height: 1.7;
            margin-bottom: 30px;
            font-weight: 400;
        }

        .panel-link {
            font-size: 13px;
            color: var(--accent-electric);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            align-self: flex-start;
            padding-bottom: 5px;
            border-bottom: 1px solid transparent;
        }
        .service-panel:hover .panel-link { border-color: var(--accent-electric); }

        /* --- SECTION: DIAGNOISTIKË (Me Grafik SVG të integruar) --- */
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
            position: relative;
        }
        
        /* Grafiku Vektorial (SVG) i integruar direkt në kod */
        .diag-visual svg {
            width: 100%; height: 100%;
        }

        .diag-text { flex: 1.2; }
        .diag-text h2 { text-transform: uppercase; color: var(--text-main); font-size: 36px; font-weight: 900; margin-bottom: 20px; letter-spacing: 2px; }
        .diag-text h2 span { color: var(--accent-electric); text-shadow: 0 0 15px rgba(0,242,254,0.4); }
        .diag-text p { color: var(--text-muted); line-height: 1.8; font-size: 16px; margin-bottom: 20px; font-weight: 300; }

        /* --- FOOTER & CONTACT (Specifike) --- */
        footer {
            background-color: var(--bg-dark);
            padding: 70px 50px 40px 50px;
            border-top: 1px solid rgba(255,255,255,0.03);
            text-align: center;
        }

        .footer-logo { font-size: 36px; font-weight: 900; text-transform: uppercase; margin-bottom: 15px; font-style: italic; }
        .footer-logo span { color: var(--accent-electric); }
        .footer-tagline { color: var(--text-muted); margin-bottom: 40px; font-size: 15px; font-weight: 400; max-width: 500px; margin-left: auto; margin-right: auto;}

        .contact-card {
            background-color: var(--bg-panel);
            padding: 40px;
            border-radius: 12px;
            display: inline-block;
            border: 1px solid rgba(255,255,255,0.05);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }
        .contact-label { font-size: 12px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 2px; margin-bottom: 10px; }
        .contact-name { font-size: 22px; font-weight: 800; color: var(--text-main); margin-bottom: 10px; letter-spacing: 1px;}
        .contact-phone { font-size: 28px; color: var(--accent-electric); font-family: 'Courier New', Courier, monospace; font-weight: bold; }
        .contact-phone a:hover { text-shadow: 0 0 15px var(--accent-electric); }

        .copyright { margin-top: 60px; font-size: 12px; color: #444; letter-spacing: 1px; text-transform: uppercase; }

        /* --- RESPONSIVE DESIGN --- */
        @media (max-width: 992px) {
            .diagnostike-tech { flex-direction: column; text-align: center; padding: 60px 20px; }
            .hero h1 { font-size: 40px; }
        }

        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 10px; text-align: center; }
            nav ul { gap: 15px; flex-wrap: wrap; justify-content: center; }
            .hero h1 { font-size: 32px; letter-spacing: 2px; }
            .services-dashboard { padding: 40px 20px; }
            .contact-phone { font-size: 22px; }
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
        <h1>UNI<span>KEY</span> AUTOTECH</h1>
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
                <circle cx="265" cy="75" r="5" fill="#00f2fe">
                    <animate attributeName="r" from="5" to="8" dur="1s" repeatCount="indefinite" />
                    <animate attributeName="opacity" from="1" to="0.5" dur="1s" repeatCount="indefinite" />
                </circle>
            </svg>
        </div>
        <div class="diag-text">
            <h2>Diagnoistikë <span>Kompjuterike</span></h2>
            <p>Zbulimi i saktë i problemeve elektronike me sistemet e sigurisë së makinës (Immobilizer, Keyless Go) duke përdorur pajisjet më të fundit diagnoistike.</p>
            <p>Ne eliminojmë gabimet dhe sigurojmë që kodimi i çelësit të bëhet në përputhje të plotë me kompjuterin e makinës.</p>
        </div>
    </section>

    <footer id="kontakt">
        <div class="footer-logo">UNI<span>KEY</span></div>
        <p class="footer-tagline">Zgjidhje Profesionale dhe Teknologjike për Çelësa dhe Siguri Automjetesh</p>
        
        <div class="contact-card">
            <div class="contact-label">Personi Kontakt</div>
            <div class="contact-name">Muhamed Musili</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>

        <div class="copyright">
            &copy; 2023 UNIKEY. All rights reserved. <br>
            Professional No-Image Template.
        </div>
    </footer>

</body>
</html>
