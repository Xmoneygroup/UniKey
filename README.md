<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Professional Auto Locksmith</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #FFD700;
            --blue-accent: #00d4ff;
            --dark-bg: #050505;
            --glass: rgba(255, 255, 255, 0.05);
            --border-glass: rgba(255, 255, 255, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--dark-bg);
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* --- BACKGROUND ANIMACION ME LOGO --- */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at center, #111 0%, #000 100%);
        }

        .floating-logo {
            position: absolute;
            font-family: 'Orbitron', sans-serif;
            font-weight: bold;
            color: rgba(255, 255, 255, 0.08);
            user-select: none;
            pointer-events: none;
            white-space: nowrap;
            text-transform: uppercase;
        }

        /* --- HEADER & TRANSLATE --- */
        .header-nav {
            display: flex;
            justify-content: flex-end;
            padding: 25px 5%;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .btn-translate {
            background: transparent;
            color: var(--gold);
            border: 1px solid var(--gold);
            padding: 8px 20px;
            font-family: 'Orbitron', sans-serif;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.4s ease;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .btn-translate:hover {
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 15px var(--gold);
        }

        /* --- TITULLI DHE KONTENTI --- */
        .main-wrapper {
            max-width: 1100px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
        }

        .luxury-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(3rem, 10vw, 6rem);
            font-weight: 700;
            color: #fff;
            letter-spacing: 15px;
            margin-bottom: 40px;
            position: relative;
            display: inline-block;
            background: linear-gradient(to bottom, #fff 40%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.3));
        }

        /* Nentitujt me Dizajn Modern */
        .info-card {
            background: var(--glass);
            border: 1px solid var(--border-glass);
            backdrop-filter: blur(15px);
            padding: 40px;
            border-radius: 2px; /* Square/Sharp Luxury Look */
            text-align: left;
            margin-bottom: 50px;
            position: relative;
            overflow: hidden;
        }

        .info-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0;
            width: 4px; height: 100%;
            background: var(--gold);
        }

        .info-list {
            list-style: none;
        }

        .info-list li {
            font-size: 1.3rem;
            margin-bottom: 20px;
            line-height: 1.6;
            display: flex;
            align-items: flex-start;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            padding-bottom: 10px;
        }

        .info-list li::before {
            content: '>';
            color: var(--gold);
            margin-right: 15px;
            font-family: 'Orbitron';
            font-weight: bold;
        }

        /* --- GALERIA --- */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
            margin-bottom: 60px;
        }

        .img-box {
            height: 350px;
            overflow: hidden;
            border: 1px solid var(--border-glass);
            position: relative;
        }

        .img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: grayscale(40%);
            transition: all 0.6s cubic-bezier(0.23, 1, 0.32, 1);
        }

        .img-box:hover img {
            filter: grayscale(0%);
            transform: scale(1.1);
        }

        /* --- RATING --- */
        .rating-container {
            background: #0a0a0a;
            border: 1px solid var(--gold);
            padding: 40px;
            margin-top: 40px;
        }

        .stars {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .star {
            cursor: pointer;
            color: #222;
            transition: 0.3s;
        }

        .star.active { color: var(--gold); text-shadow: 0 0 10px var(--gold); }

        textarea {
            width: 100%;
            padding: 15px;
            background: transparent;
            border: 1px solid var(--border-glass);
            color: white;
            font-family: inherit;
            margin-bottom: 20px;
            outline: none;
        }

        .btn-submit {
            background: var(--gold);
            color: black;
            border: none;
            padding: 15px 40px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            font-family: 'Orbitron';
        }

        /* Animacione */
        @keyframes slide {
            from { transform: translateX(100%); }
            to { transform: translateX(-100%); }
        }
    </style>
</head>
<body>

    <div id="bg-canvas"></div>

    <nav class="header-nav">
        <button class="btn-translate" onclick="toggleLanguage()">Language: English</button>
    </nav>

    <div class="main-wrapper">
        <h1 class="luxury-title">UNIKEY</h1>
        
        <div class="info-card">
            <ul class="info-list" id="content-list">
                <li data-sq="Kemi 17 vite qe meremi me kete profesion." data-en="We have 17 years of experience in this profession.">Kemi 17 vite qe meremi me kete profesion.</li>
                <li data-sq="Punojm 6 ditet e javes nga e Hena deri ne dIten e Shtune , nga ora 9:30 deri ne ora 19:00." data-en="We work 6 days a week, Monday to Saturday, 9:30 AM to 7:00 PM.">Punojm 6 ditet e javes nga e Hena deri ne dIten e Shtune , nga ora 9:30 deri ne ora 19:00.</li>
                <li data-sq="Riparojm Dyer te makinave ( Brava ), Mehanizma te dritareve te Makinave, Qelsa duplikat te makinave kodime , celsa te shtepive, Diagnostik dhe shum gjera te tjera." data-en="We repair car doors (locks), window mechanisms, duplicate keys, coding, house keys, diagnostics, and much more.">Riparojm Dyer te makinave ( Brava ), Mehanizma te dritareve te Makinave, Qelsa duplikat te makinave kodime , celsa te shtepive, Diagnostik dhe shum gjera te tjera.</li>
                <li data-sq="Me lokacion ndodhemi ne Maqedoni, Komuna Gjorce Petrov, Me lokacion mundeni te na gjeni duke kerkuar vetem ( UNIKKEY - Gjorce Petrov )." data-en="Located in Macedonia, Gjorce Petrov. Search for 'UNIKKEY - Gjorce Petrov' to find us easily.">Me lokacion ndodhemi ne Maqedoni, Komuna Gjorce Petrov, Me lokacion mundeni te na gjeni duke kerkuar vetem ( UNIKKEY - Gjorce Petrov ).</li>
                <li data-sq="Kontaktoni ne kete numer per cdo lloj problemi ne lidhje me kete problem tek makinat e juaja ( Muhamet Musliu - + 389 070 229 348 )" data-en="Contact us for any car-related issues at: ( Muhamet Musliu - + 389 070 229 348 )">Kontaktoni ne kete numer per cdo lloj problemi ne lidhje me kete problem tek makinat e juaja ( Muhamet Musliu - + 389 070 229 348 )</li>
            </ul>
        </div>

        <div class="gallery-grid">
            <div class="img-box"><img src="foto1.jpg"></div>
            <div class="img-box"><img src="foto2.jpg"></div>
            <div class="img-box"><img src="foto3.jpg"></div>
            <div class="img-box"><img src="foto4.jpg"></div>
            <div class="img-box"><img src="foto5.jpg"></div>
            <div class="img-box"><img src="foto6.jpg"></div>
        </div>

        <div class="rating-container">
            <h2 id="rate-title" style="margin-bottom:20px; font-family:'Orbitron'">VLERSONI PUNEN TONË</h2>
            <div class="stars">
                <span class="star" onclick="setRating(1)">★</span>
                <span class="star" onclick="setRating(2)">★</span>
                <span class="star" onclick="setRating(3)">★</span>
                <span class="star" onclick="setRating(4)">★</span>
                <span class="star" onclick="setRating(5)">★</span>
            </div>
            <textarea id="feedback" placeholder="Shkruani komentin tuaj këtu..."></textarea>
            <button class="btn-submit" onclick="sendFeedback()">DËRGO KOMENTIN</button>
        </div>
    </div>

    <script>
        // --- LOGO BACKGROUND ANIMATION ---
        const brands = ['LAMBORGHINI', 'FERRARI', 'PORSCHE', 'BMW', 'AUDI', 'MERCEDES', 'TOYOTA', 'VW', 'CADILLAC'];
        const canvas = document.getElementById('bg-canvas');

        function createFloatingLogo() {
            const logo = document.createElement('div');
            logo.className = 'floating-logo';
            logo.innerText = brands[Math.floor(Math.random() * brands.length)];
            
            const startPos = Math.random() * 100;
            logo.style.left = startPos + 'vw';
            logo.style.top = '110vh';
            
            // Shpejtesia fillestare (3 sekondat e para te jete e shpejte)
            const duration = 15 + Math.random() * 10; 
            logo.style.transition = `transform ${duration}s linear, opacity 2s`;
            
            canvas.appendChild(logo);

            // Animacioni i levizjes
            setTimeout(() => {
                logo.style.transform = `translateY(-120vh) rotate(${Math.random() * 360}deg)`;
            }, 100);

            // Pastrimi
            setTimeout(() => { logo.remove(); }, duration * 1000);
        }

        // Gjenero logo vazhdimisht
        setInterval(createFloatingLogo, 1500);

        // --- TRANSLATE LOGIC ---
        let isEn = false;
        function toggleLanguage() {
            const items = document.querySelectorAll('#content-list li');
            const btn = document.querySelector('.btn-translate');
            const rateH2 = document.getElementById('rate-title');
            
            isEn = !isEn;
            items.forEach(li => {
                li.innerText = isEn ? li.getAttribute('data-en') : li.getAttribute('data-sq');
            });
            btn.innerText = isEn ? "Language: Albanian" : "Language: English";
            rateH2.innerText = isEn ? "RATE OUR WORK" : "VLERSONI PUNEN TONË";
        }

        // --- RATING LOGIC ---
        function setRating(n) {
            const stars = document.querySelectorAll('.star');
            stars.forEach((s, i) => {
                s.classList.toggle('active', i < n);
            });
        }

        function sendFeedback() {
            alert("Faleminderit Muhamet! Komenti u dërgua me sukses.");
            document.getElementById('feedback').value = "";
        }
    </script>
</body>
</html>
