<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain | Grand Sale</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
        }

        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .content {
            position: relative;
            z-index: 10;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            pointer-events: none;
        }

        /* TEKSTI I RI PA PLLAKATË */
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 5rem;
            color: #fff;
            letter-spacing: 20px;
            text-transform: uppercase;
            margin: 0;
            /* Efekti i shkëlqimit neon */
            text-shadow: 0 0 20px rgba(0, 210, 255, 0.7), 0 0 40px rgba(0, 210, 255, 0.4);
            
            /* Animacioni 5 sekonda (shfaqet dhe zhduket) */
            animation: breatheDisplay 5s ease-in-out infinite;
        }

        /* ANIMACIONI QË SHFAQET DHE ZHDUKET */
        @keyframes breatheDisplay {
            0%, 100% { 
                opacity: 0; 
                transform: scale(0.9);
                filter: blur(10px);
            }
            50% { 
                opacity: 1; 
                transform: scale(1.1);
                filter: blur(0px);
            }
        }

        @media (max-width: 768px) {
            .title { 
                font-size: 1.8rem; 
                letter-spacing: 8px; 
            }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="content">
        <h1 class="title">Domain for Sale</h1>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        class Firework {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = canvas.height;
                this.targetY = Math.random() * (canvas.height * 0.6);
                this.speed = 2 + Math.random() * 4;
                this.angle = -Math.PI / 2 + (Math.random() * 0.4 - 0.2);
                this.velocity = {
                    x: Math.cos(this.angle) * this.speed,
                    y: Math.sin(this.angle) * this.speed
                };
                this.explosionSize = Math.random() > 0.8 ? 100 : 40 + Math.random() * 40;
                this.dead = false;
            }

            update() {
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                if (this.y <= this.targetY) {
                    this.explode();
                    this.dead = true;
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = "#fff";
                ctx.fill();
            }

            explode() {
                const neonColors = ['#00f2ff', '#00ffaa', '#ff00ee', '#ffff00', '#ff3300', '#4d4dff'];
                const color = neonColors[Math.floor(Math.random() * neonColors.length)];
                for (let i = 0; i < this.explosionSize; i++) {
                    particles.push(new Particle(this.x, this.y, color));
                }
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                const angle = Math.random() * Math.PI * 2;
                const force = Math.random() * 10;
                this.velocity = {
                    x: Math.cos(angle) * force,
                    y: Math.sin(angle) * force
                };
                this.alpha = 1;
                this.friction = 0.94;
                this.gravity = 0.15;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2.5, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 15;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.restore();
            }

            update() {
                this.velocity.x *= this.friction;
                this.velocity.y *= this.friction;
                this.velocity.y += this.gravity;
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                this.alpha -= 0.012;
            }
        }

        let fireworks = [];
        let particles = [];

        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            if (Math.random() < 0.08) {
                fireworks.push(new Firework());
            }

            fireworks.forEach((fw, index) => {
                fw.update();
                fw.draw();
                if (fw.dead) fireworks.splice(index, 1);
            });

            particles.forEach((p, index) => {
                p.update();
                p.draw();
                if (p.alpha <= 0) particles.splice(index, 1);
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
