<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Domain Offering</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Montserrat:wght@100;300&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: radial-gradient(circle at center, #0a1118 0%, #000000 100%);
            font-family: 'Montserrat', sans-serif;
        }

        /* SFONDI ME GRIMCA PLUHURI DRITE */
        #star-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .container {
            position: relative;
            z-index: 10;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* PLLAKATA "OBSIDIAN GLASS" */
        .glass-panel {
            position: relative;
            padding: 80px 100px;
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(0, 195, 255, 0.2);
            border-radius: 0px; /* Stil arkitektural, pa kthesa */
            backdrop-filter: blur(25px);
            text-align: center;
            overflow: hidden;
            box-shadow: 0 40px 100px rgba(0, 0, 0, 0.8);
        }

        /* EFEKTI I DRITËS QË KALON MBI XHAM */
        .glass-panel::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 255, 0.05), transparent);
            transform: rotate(45deg);
            animation: lightSweep 6s infinite;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 3.5rem;
            font-weight: 700;
            color: #fff;
            margin: 0;
            letter-spacing: 20px;
            text-transform: uppercase;
            background: linear-gradient(to right, #fff 20%, #00d2ff 50%, #fff 80%);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shineText 5s linear infinite;
        }

        .subtitle {
            margin-top: 40px;
            font-size: 0.9rem;
            color: #00d2ff;
            letter-spacing: 15px;
            text-transform: uppercase;
            font-weight: 300;
            opacity: 0.8;
        }

        /* ANIMACIONET */
        @keyframes lightSweep {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }

        @keyframes shineText {
            to { background-position: 200% center; }
        }

        /* LINJAT DEKORATIVE VIP */
        .corner-line {
            position: absolute;
            width: 40px;
            height: 40px;
            border: 2px solid #00d2ff;
        }
        .tl { top: 0; left: 0; border-right: none; border-bottom: none; }
        .br { bottom: 0; right: 0; border-left: none; border-top: none; }

        @media (max-width: 768px) {
            .title { font-size: 1.5rem; letter-spacing: 10px; }
            .glass-panel { padding: 40px 20px; width: 85%; }
            .subtitle { font-size: 0.7rem; letter-spacing: 5px; }
        }
    </style>
</head>
<body>

    <canvas id="star-canvas"></canvas>

    <div class="container">
        <div class="glass-panel">
            <div class="corner-line tl"></div>
            <div class="corner-line br"></div>
            
            <h1 class="title">DOMAIN SALE</h1>
            <p class="subtitle">This Domain is for Sale</p>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('star-canvas');
        const ctx = canvas.getContext('2d');
        let stars = [];

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        class Star {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 1.5;
                this.speed = Math.random() * 0.2;
                this.opacity = Math.random();
            }
            draw() {
                ctx.fillStyle = `rgba(0, 210, 255, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
            update() {
                this.y -= this.speed;
                if (this.y < 0) this.y = canvas.height;
                this.draw();
            }
        }

        function init() {
            for (let i = 0; i < 150; i++) {
                stars.push(new Star());
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            stars.forEach(star => star.update());
            requestAnimationFrame(animate);
        }

        init();
        animate();

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            stars = [];
            init();
        });
    </script>
</body>
</html>
