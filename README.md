
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Professional Auto Locksmith</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #FFD700;
            --gold-glow: rgba(255, 215, 0, 0.4);
            --dark-bg: #020202;
            --glass: rgba(255, 255, 255, 0.03);
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

        /* NEON FALLING KEYS BACKGROUND */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at 50% 50%, #0a0a0a 0%, #000 100%);
            overflow: hidden;
        }

        .falling-key {
            position: absolute;
            color: var(--gold);
            font-size: 25px;
            filter: drop-shadow(0 0 8px var(--gold));
            user-select: none;
            pointer-events: none;
            opacity: 0.6;
            animation: fallAndRotate linear forwards;
        }

        @keyframes fallAndRotate {
            0% { transform: translateY(-100px) rotate(0deg); opacity: 0; }
            10% { opacity: 0.6; }
            90% { opacity: 0.6; }
            100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
        }

        /* ANIMACIONI I HYRJES (2 SEKONDA) */
        @keyframes fadeInUp {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .animate-entry {
            animation: fadeInUp 2s ease-out forwards;
        }

        .header-nav {
            display: flex;
            justify-content: flex-end;
            padding: 25px 5%;
            position: relative;
            z-index: 10;
        }

        .btn-translate {
            background: rgba(0,0,0,0.5);
            color: var(--gold);
            border: 1px solid var(--gold);
            padding: 10px 25px;
            font-family: 'Orbitron', sans-serif;
            cursor: pointer;
            transition: 0.4s;
            letter-spacing: 2px;
            backdrop-filter: blur(5px);
        }

        .btn-translate:hover {
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 30px var(--gold-glow);
        }

        .main-wrapper {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
            position: relative;
        }

        /* TITULLI LUXURY PA CELLESAT POSHTE */
        .luxury-title {
            display: flex;
            justify-content: center;
            gap: 10px;
            perspective: 1000px;
            margin-bottom: 50px;
        }

        .key-letter {
            display: inline-block;
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(3rem, 10vw, 6.5rem);
            color: var(--gold);
            position: relative;
            animation: letterReveal 1s cubic-bezier(0.17, 0.67, 0.83, 0.67) forwards;
            opacity: 0;
            transform: rotateY(-90deg);
            text-shadow: 0 0 15px var(--gold-glow);
        }

        @keyframes letterReveal {
            0% { opacity: 0; transform: rotateY(-90deg) scale(0.5); filter: brightness(5); }
            100% { opacity: 1; transform: rotateY(0deg) scale(1); filter: brightness(1); }
        }

        .key-letter:nth-child(1) { animation-delay: 0.1s; }
        .key-letter:nth-child(2) { animation-delay: 0.2s; }
        .key-letter:nth-child(3) { animation-delay: 0.3s; }
        .key-letter:nth-child(4) { animation-delay: 0.4s; }
        .key-letter:nth-child(5) { animation-delay: 0.5s; }
        .key-letter:nth-child(6) { animation-delay: 0.6s; }

        .info-card {
            background: var(--glass);
            border: 1px solid var(--border-glass);
            backdrop-filter: blur(20px);
            padding: 40px;
            text-align: left;
            margin-bottom: 50px;
            border-left: 5px solid var(--gold);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .info-list { list-style: none; }
        .info-list li {
            font-size: 1.3rem;
            margin-bottom: 25px;
            display: flex;
            align-items: flex-start;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            padding-bottom: 12px;
        }

        .info-list li::before {
            content: '✦';
            color: var(--gold);
            margin-right: 15px;
            text-shadow: 0 0 10px var(--gold);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr); 
            gap: 20px;
            margin-bottom: 60px;
        }

        @media (max-width: 768px) {
            .gallery-grid { grid-template-columns: 1fr; }
            .key-letter { font-size: 3.5rem; }
        }

        .img-box {
            height: 350px;
            background: #000;
            border: 1px solid var(--border-glass);
            overflow: hidden;
            position: relative;
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
        }

        .img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 1.2s cubic-bezier(0.2, 1, 0.3, 1);
            filter: grayscale(20%);
        }

        .img-box:hover img {
            transform: scale(1.1);
            filter: grayscale(0%);
        }

        .rating-container {
            background: rgba(10,10,10,0.8);
            border: 1px solid var(--border-glass);
            padding: 50px;
            backdrop-filter: blur(10px);
            border-top: 3px solid var(--gold);
        }

        .star { cursor: pointer; font-size: 3rem; color: #1a1a1a; transition: 0.3s; }
        .star.active { color: var(--gold); text-shadow: 0 0 20px var(--gold); }

        textarea {
            width: 100%;
            padding: 20px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-glass);
            color: white;
            margin-top: 25px;
            font-family: 'Rajdhani';
            font-size: 1.1rem;
            resize: none;
        }

        .btn-submit {
            background: linear-gradient(45deg, #B8860B, var(--gold));
            border: none;
            padding: 18px 50px;
            font-weight: bold;
            cursor: pointer;
            font-family: 'Orbitron';
            margin-top: 30px;
            letter-spacing: 3px;
            color: #000;
        }
    </style>
</head>
<body>

<div id="bg-canvas"></div>

<nav class="header-nav">
    <button class="btn-translate" onclick="toggleLanguage()">Translate English</button>
</nav>

<div class="main-wrapper">
    <div class="luxury-title">
        <span class="key-letter">U</span>
        <span class="key-letter">N</span>
        <span class="key-letter">I</span>
        <span class="key-letter">K</span>
        <span class="key-letter">E</span>
        <span class="key-letter">Y</span>
    </div>

    <!-- PLlakata DHE FOTOT ME ANIMACION HYRJEJE -->
    <div class="animate-entry">
        <div class="info-card">
            <ul class="info-list" id="content-list">
                <li data-sq="17 vite eksperiencë profesionale." data-en="17 years of professional experience.">17 vite eksperiencë profesionale.</li>
                <li data-sq="E Hënë - E Shtunë | 09:30 - 19:00" data-en="Monday - Saturday | 09:30 - 19:00">E Hënë - E Shtunë | 09:30 - 19:00</li>
                <li data-sq="Brava makinash • Qelsa duplikat • Kodime • Diagnostikë" data-en="Car locks • Duplicate keys • Coding • Diagnostics">Brava makinash • Qelsa duplikat • Kodime • Diagnostikë</li>
                <li data-sq="Lokacioni: Gjorce Petrov, Maqedoni" data-en="Location: Gjorce Petrov, Macedonia">Lokacioni: Gjorce Petrov, Maqedoni</li>
                <li data-sq="Kontakt: Muhamed Musli - +389 70 229 348" data-en="Contact: Muhamed Musli  +389 70 229 348">Kontakt: Muhamed Musli - +389 70 229 348</li>
            </ul>
        </div>

        <div class="gallery-grid">
            <div class="img-box"><img src="IMG_0534.jpg" alt="Unikey 1"></div>
            <div class="img-box"><img src="IMG_0535.jpg" alt="Unikey 2"></div>
            <div class="img-box"><img src="IMG_0537.jpg" alt="Unikey 3"></div>
            <div class="img-box"><img src="IMG_0536.jpg" alt="Unikey 4"></div>
            <div class="img-box"><img src="IMG_0539.jpg" alt="Unikey 5"></div>
            <div class="img-box"><img src="IMG_0540.jpg" alt="Unikey 6"></div>
            <div class="img-box"><img src="IMG_0541.jpg" alt="Unikey 7"></div>
            <div class="img-box"><img src="IMG_0542.jpg" alt="Unikey 8"></div>
            <div class="img-box"><img src="IMG_0543.jpg" alt="Unikey 9"></div>
        </div>

        <div class="rating-container">
            <h2 id="rate-title" style="font-family:'Orbitron'; color: var(--gold); letter-spacing: 3px;">VLERSONI SHERBIMIN TONË</h2>
            <div class="stars">
                <span class="star" onclick="setStar(1)">★</span>
                <span class="star" onclick="setStar(2)">★</span>
                <span class="star" onclick="setStar(3)">★</span>
                <span class="star" onclick="setStar(4)">★</span>
                <span class="star" onclick="setStar(5)">★</span>
            </div>
            <textarea id="feedback" rows="4" placeholder="Lini mbresat tuaja..."></textarea>
            <button class="btn-submit" onclick="alert('Faleminderit Muhamed!')">DËRGO</button>
        </div>
    </div>
</div>

<script>
const canvas = document.getElementById('bg-canvas');
const keyIcons = ['🔑', '🗝️', '🏠', '🔓'];

function createFallingKey() {
    const key = document.createElement('div');
    key.className = 'falling-key';
    key.innerText = keyIcons[Math.floor(Math.random() * keyIcons.length)];
    
    const startX = Math.random() * 100;
    const duration = Math.random() * 5 + 7;
    const size = Math.random() * 15 + 20;
    
    key.style.left = startX + 'vw';
    key.style.fontSize = size + 'px';
    key.style.animationDuration = duration + 's';
    
    canvas.appendChild(key);
    
    setTimeout(() => {
        key.remove();
    }, duration * 1000);
}

setInterval(createFallingKey, 600);

let isEn = false;
function toggleLanguage() {
    isEn = !isEn;
    document.querySelectorAll('#content-list li').forEach(li => {
        li.innerText = isEn ? li.getAttribute('data-en') : li.getAttribute('data-sq');
    });
    document.querySelector('.btn-translate').innerText = isEn ? "Translate Shqip" : "Translate English";
}

function setStar(n) {
    document.querySelectorAll('.star').forEach((s, i) => {
        s.classList.toggle('active', i < n);
    });
}
</script>

</body>
</html>
