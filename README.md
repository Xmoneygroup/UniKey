<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain | Grand Sale</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Montserrat:wght@300;600&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Montserrat', sans-serif;
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

        /* TEKSTI I RI PA PLLAKATË ME ANIMACION 5 SEKONDA */
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 4.5rem;
            color: #fff;
            letter-spacing: 20px;
            text-transform: uppercase;
            margin: 0;
            /* Shkëlqim i fortë Neon */
            text-shadow: 0 0 20px rgba(0, 210, 255, 0.8), 0 0 40px rgba(0, 210, 255, 0.4);
            
            /* Animacioni: Shfaqet, rri pak, zhduket - përsëritet çdo 5 sekonda */
            animation: breatheDisplay 5s ease-in-out infinite;
        }

        @keyframes breatheDisplay {
            0%, 100% { 
                opacity: 0; 
                transform: scale(0.9);
                filter: blur(10px);
            }
            30%, 70% { 
                opacity: 1; 
                transform: scale(1);
                filter: blur(0px);
            }
        }

        @media (max-width: 768px) {
            .title { font-size: 1.6rem; letter-spacing: 6px; }
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
                // Niset nga çdo pikë në fund të ekranit
                this.x = Math.random() * canvas.width;
                this.y = canvas.height;
                // Lartësi të ndryshme plasjeje për diversitet
                this.targetY = Math.random() * (canvas.height * 0.7) + 50;
                this.speed = 3 + Math.random() * 3;
                this.angle = -Math.PI / 2 + (Math.random() * 0.4 - 0.2);
                this.velocity = {
                    x: Math.cos(this.angle) * this.speed,
                    y: Math.sin(this.angle) * this.speed
                };
                
                // Variacioni i madhësisë së shpërthimit
                const rand = Math.random();
                if (rand > 0.85) this.explosionSize = 150; // Super i madh
                else if (rand > 0.4) this.explosionSize = 70; // Mesatar
                else this.explosionSize = 30; // I vogël
                
                this.dead = false;
                this.trail = []; // Gjurma e raketës
            }

            update() {
                this.trail.push({x: this.x, y: this.y});
                if (this.trail.length > 8) this.trail.shift();

                this.x += this.velocity.x;
                this.y += this.velocity.y;
                
                if (this.y <= this.targetY) {
                    this.explode();
                    this.dead = true;
                }
            }

            draw() {
                // Vizatojmë bishtin e raketës gjatë ngjitjes
                ctx.beginPath();
                ctx.strokeStyle = "rgba(255, 255, 255, 0.3)";
                ctx.lineWidth = 1.5;
                if(this.trail.length > 0) {
                    ctx.moveTo(this.trail[0].x, this.trail[0].y);
                    ctx.lineTo(this.x, this.y);
                    ctx.stroke();
                }

                // Koka e raketës
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = "#fff";
                ctx.fill();
            }

            explode() {
                const neonColors = ['#00f2ff', '#00ffaa', '#ff00ee', '#ffff00', '#ff3300', '#4d4dff', '#ffffff'];
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
                const force = Math.random() * 11; // Shpërthim më i fuqishëm
                this.velocity = {
                    x: Math.cos(angle) * force,
                    y: Math.sin(angle) * force
                };
                this.alpha = 1;
                this.friction = 0.94;
                this.gravity = 0.15;
                this.size = Math.random() * 3 + 1; // Grimca me madhësi të ndryshme
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                // Efekti Glow për çdo grimcë
                ctx.shadowBlur = 12;
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
                this.alpha -= 0.01; // Zhdukja graduale
            }
        }

        let fireworks = [];
        let particles = [];

        function animate() {
            // Krijojmë efektin trail në sfond
            ctx.fillStyle = 'rgba(0, 0, 0, 0.18)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Kontrolli i shpeshtësisë së raketave
            if (Math.random() < 0.07) { 
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
