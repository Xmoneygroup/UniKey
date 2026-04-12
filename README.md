<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain | Special Edition</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Montserrat:wght@100;300&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Montserrat', sans-serif;
        }

        /* SFONDI ELITE - NEBULA & 3D GRID */
        .universe {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: 
                radial-gradient(circle at 20% 30%, rgba(0, 50, 100, 0.4) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(0, 20, 50, 0.5) 0%, transparent 50%);
            animation: nebulaPulse 10s ease-in-out infinite alternate;
        }

        #bg-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .container {
            position: relative;
            z-index: 10;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* PLLAKATA SUPER STIL QË TË PËLQEU */
        .glass-panel {
            position: relative;
            padding: 80px 110px;
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(0, 255, 255, 0.3);
            backdrop-filter: blur(30px);
            text-align: center;
            box-shadow: 0 0 80px rgba(0, 150, 255, 0.15);
            animation: floatPanel 6s ease-in-out infinite;
        }

        /* Efekti i dritës lazer që kalon mbi xham */
        .glass-panel::after {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 50%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.1), transparent);
            transform: skewX(-20deg);
            animation: lightSweep 4s infinite;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 4rem;
            font-weight: 700;
            color: #fff;
            margin: 0;
            letter-spacing: 25px;
            text-transform: uppercase;
            background: linear-gradient(to right, #fff, #00d2ff, #fff);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shineText 4s linear infinite;
        }

        .subtitle {
            margin-top: 35px;
            font-size: 1rem;
            color: #00d2ff;
            letter-spacing: 12px;
            text-transform: uppercase;
            font-weight: 300;
            opacity: 0.9;
            text-shadow: 0 0 10px rgba(0, 210, 255, 0.5);
        }

        /* DEKORIMET E QOSHEVE */
        .corner {
            position: absolute;
            width: 30px;
            height: 30px;
            border: 2px solid #00d2ff;
        }
        .tl { top: -5px; left: -5px; border-right: none; border-bottom: none; }
        .br { bottom: -5px; right: -5px; border-left: none; border-top: none; }

        /* ANIMACIONET */
        @keyframes nebulaPulse {
            from { opacity: 0.6; transform: scale(1); }
            to { opacity: 1; transform: scale(1.1); }
        }

        @keyframes lightSweep {
            to { left: 200%; }
        }

        @keyframes floatPanel {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        @keyframes shineText {
            to { background-position: 200% center; }
        }

        @media (max-width: 768px) {
            .title { font-size: 1.8rem; letter-spacing: 10px; }
            .glass-panel { padding: 50px 30px; width: 80%; }
            .subtitle { font-size: 0.7rem; letter-spacing: 6px; }
        }
    </style>
</head>
<body>

    <div class="universe">
        <canvas id="bg-canvas"></canvas>
    </div>

    <div class="container">
        <div class="glass-panel">
            <div class="corner tl"></div>
            <div class="corner br"></div>
            
            <h1 class="title">DOMAIN SALE</h1>
            <p class="subtitle">This Domain is for Sale</p>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let lines = [];

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        class LaserLine {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = (Math.random() - 0.5) * canvas.width * 2;
                this.y = (Math.random() - 0.5) * canvas.height * 2;
                this.z = Math.random() * canvas.width;
                this.pz = this.z;
                this.speed = 2 + Math.random() * 5;
            }
            update() {
                this.pz = this.z;
                this.z -= this.speed;
                if (this.z < 1) {
                    this.reset();
                    this.pz = this.z;
                }
            }
            draw() {
                let sx = ((this.x / this.z) * canvas.width/2) + canvas.width/2;
                let sy = ((this.y / this.z) * canvas.height/2) + canvas.height/2;
                let px = ((this.x / this.pz) * canvas.width/2) + canvas.width/2;
                let py = ((this.y / this.pz) * canvas.height/2) + canvas.height/2;

                ctx.strokeStyle = 'rgba(0, 210, 255, ' + (1 - this.z / canvas.width) + ')';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(px, py);
                ctx.lineTo(sx, sy);
                ctx.stroke();
            }
        }

        for (let i = 0; i < 150; i++) {
            lines.push(new LaserLine());
        }

        function animate() {
            // Krijohet efekti "trail" duke mos fshirë plotësisht canvas-in
            ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            lines.forEach(line => {
                line.update();
                line.draw();
            });
            requestAnimationFrame(animate);
        }

        animate();

        window.addEventListener('resize', () => {
            canvas.width = innerWidth;
            canvas.height = innerHeight;
        });
    </script>
</body>
</html>
