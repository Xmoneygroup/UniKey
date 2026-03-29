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
            color: rgba(255, 215, 0, 0.1);
            pointer-events: none;
            white-space: nowrap;
            text-transform: uppercase;
        }

        .header-nav {
            display: flex;
            justify-content: flex-end;
            padding: 25px 5%;
        }

        .btn-translate {
            background: transparent;
            color: var(--gold);
            border: 1px solid var(--gold);
            padding: 10px 25px;
            font-family: 'Orbitron', sans-serif;
            cursor: pointer;
            transition: 0.4s;
            letter-spacing: 2px;
        }

        .btn-translate:hover {
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 20px var(--gold);
        }

        .main-wrapper {
            max-width: 1100px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
        }

        .luxury-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(3rem, 10vw, 6rem);
            color: #fff;
            letter-spacing: 15px;
            margin-bottom: 40px;
            background: linear-gradient(to bottom, #fff 40%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .info-card {
            background: var(--glass);
            border: 1px solid var(--border-glass);
            backdrop-filter: blur(15px);
            padding: 40px;
            text-align: left;
            margin-bottom: 50px;
            border-left: 5px solid var(--gold);
        }

        .info-list { list-style: none; }
        .info-list li {
            font-size: 1.3rem;
            margin-bottom: 20px;
            display: flex;
            align-items: flex-start;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            padding-bottom: 10px;
        }

        .info-list li::before {
            content: '>';
            color: var(--gold);
            margin-right: 15px;
            font-weight: bold;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 60px;
        }

        .img-box {
            height: 400px;
            background: #111;
            border: 1px solid var(--border-glass);
            overflow: hidden;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.6s ease;
        }

        .img-box:hover {
            border: 1px solid var(--gold);
        }

        .img-box:hover img {
            transform: scale(1.05);
        }

        .rating-container {
            background: #0a0a0a;
            border: 1px solid var(--gold);
            padding: 40px;
        }

        .star { cursor: pointer; font-size: 2.5rem; color: #222; }
        .star.active { color: var(--gold); text-shadow: 0 0 10px var(--gold); }

        textarea {
            width: 100%;
            padding: 15px;
            background: transparent;
            border: 1px solid var(--border-glass);
            color: white;
            margin-top: 20px;
            font-family: 'Rajdhani';
        }

        .btn-submit {
            background: var(--gold);
            border: none;
            padding: 15px 40px;
            font-weight: bold;
            cursor: pointer;
            font-family: 'Orbitron';
            margin-top: 20px;
        }
    </style>
</head>
<body>

<div id="bg-canvas"></div>

<nav class="header-nav">
    <button class="btn-translate" onclick="toggleLanguage()">Translate to English</button>
</nav>

<div class="main-wrapper">
    <h1 class="luxury-title">UNIKEY</h1>

    <div class="info-card">
        <ul class="info-list" id="content-list">
            <li data-sq="Kemi 17 vite qe meremi me kete profesion." data-en="17 years of professional experience in this field.">Kemi 17 vite qe meremi me kete profesion.</li>
            <li data-sq="Punojm 6 ditet e javes (E Hënë - E Shtunë), 09:30 - 19:00." data-en="Open 6 days a week (Mon - Sat), 09:30 - 19:00.">Punojm 6 ditet e javes (E Hënë - E Shtunë), 09:30 - 19:00.</li>
            <li data-sq="Riparojm Brava makinash, Mekanizma dritaresh, Qelsa duplikat, Kodime, Diagnostikë." data-en="Car locks, window mechanisms, duplicate keys, coding, and diagnostics.">Riparojm Brava makinash, Mekanizma dritaresh, Qelsa duplikat, Kodime, Diagnostikë.</li>
            <li data-sq="Lokacioni: Gjorce Petrov, Maqedoni (UNIKKEY - Gjorce Petrov)." data-en="Location: Gjorce Petrov, Macedonia (Search: UNIKKEY - Gjorce Petrov).">Lokacioni: Gjorce Petrov, Maqedoni (UNIKKEY - Gjorce Petrov).</li>
            <li data-sq="Muhamet Musliu - + 389 070 229 348" data-en="Contact: Muhamet Musliu - + 389 070 229 348">Muhamet Musliu - + 389 070 229 348</li>
        </ul>
    </div>

    <div class="gallery-grid">
        <div class="img-box"><img src="IMG_0534.jpg" alt="Unikey Workshop"></div>
        <div class="img-box"><img src="IMG_0535.jpg" alt="BMW Key Coding"></div>
        <div class="img-box"><img src="IMG_0537.jpg" alt="Unikey Storefront"></div>
        <div class="img-box"><img src="IMG_0536.jpg" alt="Unikey Service 4"></div>
        <div class="img-box"><img src="IMG_0539.jpg" alt="VW Golf Service"></div> <div class="img-box"><img src="IMG_0540.jpg" alt="Mercedes Diagnosis"></div>
        <div class="img-box"><img src="IMG_0541.jpg" alt="BMW Lock Service"></div>
        <div class="img-box"><img src="IMG_0542.jpg" alt="Car Key Collection"></div>
        <div class="img-box"><img src="IMG_0543.jpg" alt="Seat Key Duplicate"></div>
    </div>

    <div class="rating-container">
        <h2 id="rate-title" style="font-family:'Orbitron'">VLERSONI PUNEN TONË</h2>
        <div class="stars">
            <span class="star" onclick="setStar(1)">★</span>
            <span class="star" onclick="setStar(2)">★</span>
            <span class="star" onclick="setStar(3)">★</span>
            <span class="star" onclick="setStar(4)">★</span>
            <span class="star" onclick="setStar(5)">★</span>
        </div>
        <textarea id="feedback" placeholder="Shkruani mendimin tuaj këtu..."></textarea>
        <button class="btn-submit" onclick="alert('Faleminderit!')">DËRGO KOMENTIN</button>
    </div>
</div>

<script>
const brands = ['LAMBORGHINI','FERRARI','PORSCHE','BMW','AUDI','MERCEDES','TOYOTA','VW','CADILLAC'];
const canvas = document.getElementById('bg-canvas');

function createLogo() {
    const logo = document.createElement('div');
    logo.className = 'floating-logo';
    logo.innerText = brands[Math.floor(Math.random() * brands.length)];
    logo.style.left = Math.random() * 100 + 'vw';
    logo.style.top = '110vh';
    const duration = 12 + Math.random() * 10;
    logo.style.transition = `transform ${duration}s linear, opacity 1s`;
    canvas.appendChild(logo);
    setTimeout(() => { logo.style.transform = `translateY(-120vh) rotate(360deg)`; }, 100);
    setTimeout(() => { logo.remove(); }, duration * 1000);
}
setInterval(createLogo, 1800);

let isEn = false;
function toggleLanguage() {
    isEn = !isEn;
    document.querySelectorAll('#content-list li').forEach(li => {
        li.innerText = isEn ? li.getAttribute('data-en') : li.getAttribute('data-sq');
    });
    document.querySelector('.btn-translate').innerText = isEn ? "Kthe ne Shqip" : "Translate to English";
}

function setStar(n) {
    document.querySelectorAll('.star').forEach((s, i) => {
        s.classList.toggle('active', i < n);
    });
}
</script>

</body>
</html>
