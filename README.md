<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain Sales | dubrent.com</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Space+Grotesk:wght@300;400;600;700&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Space Grotesk', sans-serif;
        }

        /* Canvas tani është mbi gjithçka (z-index i lartë) */
        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 999; 
            pointer-events: none; /* Lejon klikimin e butonave poshtë tij */
        }

        .main-wrapper {
            position: relative;
            z-index: 10;
            width: 100%;
            height: 100vh;
            display: flex;
            flex-direction: row;
            justify-content: center; 
            align-items: center;     
            gap: 60px;                
            padding: 20px;
            padding-bottom: 180px;
            box-sizing: border-box;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.05); 
            backdrop-filter: blur(8px); 
            -webkit-backdrop-filter: blur(8px);
            width: 570px; 
            padding: 60px; 
            border-radius: 40px;
            text-align: left;
            box-shadow: 0 30px 60px rgba(0,0,0,0.3);
            pointer-events: auto;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .badge-container { display: flex; gap: 12px; margin-bottom: 20px; }
        .badge { display: flex; align-items: center; gap: 6px; padding: 6px 14px; border-radius: 100px; font-size: 0.75rem; font-weight: 700; text-transform: uppercase; letter-spacing: 1px; }
        .verified-badge { background: rgba(0, 242, 255, 0.15); color: #00f2ff; border: 1px solid rgba(0, 242, 255, 0.3); }
        .premium-badge { background: rgba(255, 215, 0, 0.15); color: #ffd700; border: 1px solid rgba(255, 215, 0, 0.3); }

        .glass-card h2 { color: #fff; font-size: 2rem; margin: 0 0 15px 0; font-weight: 600; }
        .next-btn {
            display: block; width: 100%; padding: 20px; background: #fff; color: #000;
            text-decoration: none; font-weight: 600; border-radius: 20px; text-align: center; font-size: 1.1rem;
        }

        .info-panel { text-align: left; color: #fff; }
        .info-domain { font-family: 'Syncopate', sans-serif; font-size: 3.5rem; margin: 0; text-transform: lowercase; }
        .info-status { font-size: 1.6rem; font-weight: 300; opacity: 0.8; margin-bottom: 40px; text-transform: uppercase; letter-spacing: 3px; }

        @media (max-width: 1000px) {
            .main-wrapper { flex-direction: column; gap: 40px; }
            .glass-card { width: 90%; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="main-wrapper">
        <div class="glass-card" id="card-target">
            <div class="badge-container">
                <div class="badge verified-badge"><span class="material-icons">verified</span> verified</div>
                <div class="badge premium-badge"><span class="material-icons">stars</span> premium domain</div>
            </div>

            <h2>Buy Now</h2>
            <div class="domain-line">
                <p class="domain-name" id="text-target">dubinv.com is for sale now</p>
                <p class="price">20,000 USD</p>
            </div>
            
            <a href="#" class="next-btn" id="btn-target">Next</a>
            
            <div class="contact-info">
                Need help? Give us a call<br>
                <a href="tel:+389XXXXXXXXX" class="phone-link" style="color:#fff; text-decoration:none; font-size:1.4rem; font-weight:600;">+389 XX XXX XXX</a> 
            </div>
        </div>

        <div class="info-panel">
            <div class="info-domain">dubinv.com</div>
            <div class="info-status">is for sale!</div>
        </div>
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

        class Person {
            constructor() {
                this.init();
            }
            init() {
                this.x = Math.random() < 0.5 ? -50 : canvas.width + 50;
                this.y = canvas.height * 0.8;
                this.color = `hsl(${Math.random() * 360}, 100%, 75%)`;
                this.state = 'walking'; // walking, sitting, falling
                this.waitStart = 0;
                this.legAngle = 0;
                this.armAngle = 0;
                this.fallSpeed = 0;
                this.target = Math.random() > 0.5 ? 'btn' : 'text';
            }
            draw() {
                ctx.save();
                ctx.strokeStyle = this.color;
                ctx.lineWidth = 2.5;
                ctx.lineCap = 'round';

                // Koka
                ctx.beginPath();
                ctx.arc(this.x, this.y - 25, 6, 0, Math.PI * 2);
                ctx.stroke();

                // Trupi
                ctx.beginPath();
                ctx.moveTo(this.x, this.y - 19);
                ctx.lineTo(this.x, this.y);
                ctx.stroke();

                // Duart (nxitja avash)
                let armMove = Math.sin(this.armAngle) * 10;
                ctx.beginPath();
                ctx.moveTo(this.x, this.y - 15);
                ctx.lineTo(this.x - 12, this.y - 10 + armMove); // Dora majtas
                ctx.moveTo(this.x, this.y - 15);
                ctx.lineTo(this.x + 12, this.y - 10 - armMove); // Dora djathtas
                ctx.stroke();

                // Këmbët
                if (this.state === 'sitting') {
                    ctx.beginPath();
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x + 8, this.y + 6);
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x - 8, this.y + 6);
                    ctx.stroke();
                } else {
                    let legMove = Math.sin(this.legAngle) * 12;
                    ctx.beginPath();
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x - legMove, this.y + 15);
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x + legMove, this.y + 15);
                    ctx.stroke();
                }
                ctx.restore();
            }
            update() {
                const targetEl = document.getElementById(this.target === 'btn' ? 'btn-target' : 'text-target');
                const rect = targetEl.getBoundingClientRect();
                const tx = rect.left + rect.width / 2;
                const ty = rect.top;

                if (this.state === 'walking') {
                    this.legAngle += 0.05; // Më avash
                    this.armAngle += 0.05;
                    this.x += (tx - this.x) * 0.01;
                    this.y += (ty - this.y) * 0.01;
                    if (Math.abs(this.x - tx) < 10 && Math.abs(this.y - ty) < 10) {
                        this.state = 'sitting';
                        this.waitStart = Date.now();
                    }
                } else if (this.state === 'sitting') {
                    if (Date.now() - this.waitStart > 3000) this.state = 'falling';
                } else if (this.state === 'falling') {
                    this.fallSpeed += 0.2;
                    this.y += this.fallSpeed;
                    if (this.y > canvas.height + 50) this.init();
                }
            }
        }

        class Firework {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = canvas.height;
                this.targetY = Math.random() * (canvas.height * 0.6);
                this.speed = 4;
                this.dead = false;
            }
            update() {
                this.y -= this.speed;
                if (this.y <= this.targetY) { this.explode(); this.dead = true; }
            }
            draw() {
                ctx.beginPath(); ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = "#fff"; ctx.fill();
            }
            explode() {
                const colors = ['#00f2ff', '#00ffaa', '#ff00ee', '#ffff00'];
                const color = colors[Math.floor(Math.random() * colors.length)];
                for (let i = 0; i < 40; i++) { particles.push(new Particle(this.x, this.y, color)); }
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x; this.y = y; this.color = color;
                const angle = Math.random() * Math.PI * 2;
                const force = Math.random() * 8;
                this.velocity = { x: Math.cos(angle) * force, y: Math.sin(angle) * force };
                this.alpha = 1;
            }
            draw() {
                ctx.save(); ctx.globalAlpha = this.alpha; ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2); ctx.fillStyle = this.color;
                ctx.fill(); ctx.restore();
            }
            update() {
                this.x += this.velocity.x; this.y += this.velocity.y;
                this.velocity.y += 0.1; // Graviteti
                this.alpha -= 0.01;
            }
        }

        let people = [new Person(), new Person(), new Person()];
        let fireworks = [];
        let particles = [];

        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.2)'; 
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Raketat shfaqen gjatë gjithë kohës
            if (Math.random() < 0.05) fireworks.push(new Firework());

            fireworks.forEach((fw, i) => { fw.update(); fw.draw(); if (fw.dead) fireworks.splice(i, 1); });
            particles.forEach((p, i) => { p.update(); p.draw(); if (p.alpha <= 0) particles.splice(i, 1); });
            people.forEach(p => { p.update(); p.draw(); });

            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
