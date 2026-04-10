<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY | Mansory Luxury Automotive</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700;900&family=Montserrat:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #c5a059;
            --black: #050505;
            --carbon: #121212;
        }

        body, html {
            margin: 0; padding: 0;
            background-color: var(--black);
            color: #fff;
            font-family: 'Montserrat', sans-serif;
            overflow-x: hidden;
        }

        /* SFONDI I PËRGJITHSHËM KARBON */
        .page-wrapper {
            background-image: radial-gradient(circle at center, #1a1a1a 0%, #050505 100%);
            width: 100%;
        }

        /* NAVBAR PROFESIONAL */
        nav {
            position: fixed; top: 0; width: 100%;
            display: flex; justify-content: space-between; align-items: center;
            padding: 25px 50px; z-index: 1000;
            background: rgba(0,0,0,0.9);
            border-bottom: 1px solid var(--gold);
            box-sizing: border-box;
        }

        .logo { font-family: 'Cinzel', serif; font-size: 2.2rem; color: var(--gold); letter-spacing: 5px; font-weight: 900; }
        
        .lang-switch button {
            background: transparent; border: 1px solid var(--gold); color: var(--gold);
            padding: 8px 18px; cursor: pointer; font-weight: bold; transition: 0.3s;
        }
        .lang-switch button:hover { background: var(--gold); color: #000; }

        /* SEKSIONI KRYESOR (HERO) */
        .hero {
            height: 100vh;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            text-align: center; background: url('https://images.unsplash.com/photo-1614162692292-7ac56d7f7f1e?auto=format&fit=crop&q=80&w=2000') center/cover no-repeat;
            position: relative;
        }

        .hero::after { content: ""; position: absolute; inset: 0; background: rgba(0,0,0,0.7); }

        .hero-content { position: relative; z-index: 10; }

        h1 { font-family: 'Cinzel', serif; font-size: 6vw; color: var(--gold); margin: 0; text-transform: uppercase; }
        .sub-title { font-size: 1.5rem; letter-spacing: 8px; opacity: 0.8; margin-bottom: 30px; }

        .btn-contact {
            padding: 18px 45px; background: transparent; border: 2px solid var(--gold);
            color: var(--gold); font-family: 'Cinzel'; font-size: 1.3rem;
            cursor: pointer; text-decoration: none; transition: 0.4s;
        }
        .btn-contact:hover { background: var(--gold); color: #000; box-shadow: 0 0 40px rgba(197, 160, 89, 0.4); }

        /* SEKSIONET SI NE FOTO (ME IMAZHE DHE TEKST GOLD) */
        .service-section {
            display: flex; min-height: 80vh; align-items: center;
            padding: 60px 10%; border-bottom: 1px solid rgba(197, 160, 89, 0.1);
            gap: 50px;
        }

        .service-text { flex: 1; }
        .service-text h2 { font-family: 'Cinzel', serif; font-size: 3.5rem; color: var(--gold); margin: 0; }
        .service-text p { font-size: 1.4rem; opacity: 0.8; line-height: 1.6; margin-top: 20px; }

        .service-image {
            flex: 1;
            height: 450px;
            border: 2px solid var(--gold);
            background-size: cover;
            background-position: center;
            box-shadow: 0 0 50px rgba(0,0,0,0.5);
            position: relative;
        }

        /* Foto specifike sipas shërbimit (Zëvendësoji me fotot e tua po deshe) */
        .img-keys { background-image: url('https://images.unsplash.com/photo-1622353100523-868cc9031940?auto=format&fit=crop&q=80&w=1000'); }
        .img-locks { background-image: url('https://images.unsplash.com/photo-1517524008410-b44c6659bc95?auto=format&fit=crop&q=80&w=1000'); }
        .img-diag { background-image: url('https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?auto=format&fit=crop&q=80&w=1000'); }

        /* FOOTER MANSORY */
        footer {
            padding: 100px 10%; text-align: center;
            background: #000 url('https://www.transparenttextures.com/patterns/carbon-fibre.png');
            border-top: 4px solid var(--gold);
        }

        .footer-logo { font-family: 'Cinzel', serif; font-size: 5rem; color: var(--gold); margin-bottom: 20px; }
        .tel-link { font-size: 3rem; color: var(--gold); text-decoration: none; font-weight: 900; display: block; margin: 20px 0; }
        .tel-link:hover { text-shadow: 0 0 20px var(--gold); }

        /* RESPONSIVE */
        @media (max-width: 900px) {
            .service-section { flex-direction: column; text-align: center; }
            h1 { font-size: 12vw; }
            .service-text h2 { font-size: 2.5rem; }
            .footer-logo { font-size: 3rem; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">UNIKEY</div>
        <div class="lang-switch">
            <button onclick="changeL('sq')">ALB</button>
            <button onclick="changeL('en')">ENG</button>
        </div>
    </nav>

    <div class="page-wrapper">
        
        <section class="hero">
            <div class="hero-content">
                <h1 id="h1">TEKNOLOGJIA E ÇELSAVE</h1>
                <p class="sub-title" id="p1">RIPARIM DHE KODIM PËR ÇDO MARKË MAKINASH</p>
                <a href="tel:+389070229348" class="btn-contact" id="b1">KONTAKTO TANI</a>
            </div>
        </section>

        <section class="service-section">
            <div class="service-text">
                <h2 id="t2">DUPLIKAT ÇELSASH</h2>
                <p id="d2">Saktësi milimetrike në çdo prerje dhe kodim. Përdorim teknologjinë më të fundit lazer për çelsa inteligjentë dhe mekanikë.</p>
            </div>
            <div class="service-image img-keys"></div>
        </section>

        <section class="service-section" style="flex-direction: row-reverse;">
            <div class="service-text">
                <h2 id="t3">RIPARIM BRAVASH</h2>
                <p id="d3">Siguri dhe funksionalitet maksimal. Riparojmë bravat e derës dhe mekanizmat e dritareve sikur të ishin të reja.</p>
            </div>
            <div class="service-image img-locks"></div>
        </section>

        <section class="service-section">
            <div class="service-text">
                <h2 id="t4">DIAGNOSTIKË</h2>
                <p id="d4">Gjejmë dhe zgjidhim çdo gabim elektronik. Skanim i plotë i moduleve të makinës suaj me pajisje profesionale.</p>
            </div>
            <div class="service-image img-diag"></div>
        </section>

    </div>

    <footer>
        <div class="footer-logo">UNIKEY</div>
        <div id="f-info">
            <p style="font-size: 1.5rem;">Mbi 15 Vite Eksperiencë</p>
            <p style="font-size: 1.2rem; opacity: 0.6;">Orari: 09:30 - 19:00 (E hënë - E shtunë)</p>
            <a href="tel:+389070229348" class="tel-link">+389 070 229 348</a>
        </div>
    </footer>

    <script>
        const data = {
            sq: {
                h1: "TEKNOLOGJIA E ÇELSAVE", p1: "RIPARIM DHE KODIM PËR ÇDO MARKË MAKINASH", b1: "KONTAKTO TANI",
                t2: "DUPLIKAT ÇELSASH", d2: "Saktësi milimetrike në çdo prerje dhe kodim. Përdorim teknologjinë më të fundit lazer.",
                t3: "RIPARIM BRAVASH", d3: "Siguri dhe funksionalitet maksimal. Riparojmë bravat dhe mekanizmat e dritareve.",
                t4: "DIAGNOSTIKË", d4: "Gjejmë dhe zgjidhim çdo gabim elektronik. Skanim i plotë i moduleve të makinës tuaj."
            },
            en: {
                h1: "KEY TECHNOLOGY", p1: "REPAIR AND CODING FOR EVERY CAR BRAND", b1: "CONTACT NOW",
                t2: "KEY DUPLICATION", d2: "Millimetric precision in every cut and coding. We use the latest laser technology.",
                t3: "LOCK REPAIR", d3: "Maximum security and functionality. We repair door locks and window mechanisms.",
                t4: "DIAGNOSTICS", d4: "We find and solve every electronic error. Full scanning of your car modules."
            }
        };

        function changeL(l) {
            document.getElementById('h1').innerText = data[l].h1;
            document.getElementById('p1').innerText = data[l].p1;
            document.getElementById('b1').innerText = data[l].b1;
            document.getElementById('t2').innerText = data[l].t2;
            document.getElementById('d2').innerText = data[l].d2;
            document.getElementById('t3').innerText = data[l].t3;
            document.getElementById('d3').innerText = data[l].d3;
            document.getElementById('t4').innerText = data[l].t4;
            document.getElementById('d4').innerText = data[l].d4;
        }
    </script>
</body>
</html>
