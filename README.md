<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xmoney | Private Wealth Group</title>
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Montserrat:wght@300;400;600;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #d4af37;
            --cyan: #00f2ff;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.1);
        }

        /* Base Styles */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #050505; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

        canvas { position: fixed; top: 0; left: 0; z-index: 0; pointer-events: none; }

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 100px 20px;
            background: radial-gradient(circle at center, rgba(0, 242, 255, 0.05) 0%, transparent 70%);
        }

        /* --- RANKING BADGE --- */
        .rank-badge {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--cyan);
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            backdrop-filter: blur(10px);
            animation: fadeInUp 0.8s forwards;
        }

        /* --- MAGNETIC TITLE --- */
        .title-wrapper { perspective: 1000px; margin-bottom: 40px; }
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(60px, 15vw, 200px);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -5px;
            line-height: 0.8;
            background: linear-gradient(to bottom, #fff 30%, #666 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 30px rgba(255,255,255,0.1));
            animation: titleReveal 1.5s cubic-bezier(0.2, 1, 0.3, 1);
        }

        /* --- TEXT STYLING --- */
        .manifesto-container {
            max-width: 700px;
            text-align: center;
            margin-bottom: 50px;
        }

        .manifesto-text {
            font-size: 16px;
            line-height: 1.8;
            color: rgba(255,255,255,0.8);
            margin-bottom: 20px;
            font-weight: 300;
            letter-spacing: 1px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.8s forwards;
        }

        .highlight-cyan { color: var(--cyan); font-weight: 600; }

        /* --- ELITE VIP CARD --- */
        .vip-card {
            background: var(--glass);
            border: 1px solid var(--border);
            padding: 50px;
            width: 90%;
            max-width: 500px;
            border-radius: 24px;
            backdrop-filter: blur(20px);
            position: relative;
            overflow: hidden;
            transition: 0.6s cubic-bezier(0.2, 1, 0.3, 1);
            animation: fadeInUp 1s forwards 1.5s; 
            opacity: 0;
        }

        .vip-card::before {
            content: '';
            position: absolute;
            top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: conic-gradient(transparent, var(--cyan), transparent 30%);
            animation: rotate 4s linear infinite;
            z-index: -1;
            opacity: 0.3;
        }

        .vip-card:hover {
            transform: translateY(-15px) scale(1.02);
            border-color: var(--cyan);
            box-shadow: 0 20px 50px rgba(0, 242, 255, 0.15);
        }

        .features-list { list-style: none; text-align: center; margin-bottom: 30px; }
        .features-list li {
            padding: 15px 0;
            border-bottom: 1px solid var(--border);
            font-size: 14px;
            display: block;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: white;
            font-weight: 300;
        }

        .features-list li:last-child { border-bottom: none; }

        .join-btn {
            width: 100%;
            padding: 20px;
            background: white;
            color: black;
            border: none;
            border-radius: 12px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            transition: 0.4s;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .join-btn:hover {
            background: var(--cyan);
            transform: scale(0.95);
        }

        /* --- ANIMATIONS --- */
        @keyframes titleReveal {
            0% { opacity: 0; transform: skewX(-20deg) scale(0.8); filter: blur(20px); }
            100% { opacity: 1; transform: skewX(0) scale(1); filter: blur(0); }
        }
        @keyframes fadeInUp {
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @media(max-width: 768px) {
            .title { font-size: 70px; letter-spacing: -2px; }
            .vip-card { padding: 30px; }
            .features-list li { font-size: 12px; }
            .manifesto-text { font-size: 14px; }
        }
    </style>
</head>
<body>

<canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="rank-badge">
        <span>TOP <span style="color:var(--cyan); font-weight:900;">#13</span> ON WHOP</span>
        <span style="opacity:0.3">|</span>
        <span>12,762 MEMBERS</span>
    </div>

    <div class="title-wrapper">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text" style="animation-delay: 0.5s">
            The market has <span class="highlight-cyan">zero mercy</span> for anyone. Without discipline and a clear strategy, losses are inevitable.
        </p>
        <p class="manifesto-text" style="animation-delay: 1.0s">
            Our mission is to help you build a <span class="highlight-cyan">structured approach</span> through proper risk management and a precise trading strategy.
        </p>
        <p class="manifesto-text" style="animation-delay: 1.5s">
            If you are ready to elevate your trading and join the <span class="highlight-cyan">VIP ZONE</span>, act now. Do not wait until it is too late.
        </p>
    </div>

    <div class="vip-card">
        <ul class="features-list">
            <li>Signals + Strategy</li>
            <li>57% - 60% Guaranteed Win Rate</li>
            <li>3+ Daily Signals</li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2L1 21h22L12 2zm0 3.45l8.1 14.1H3.9L12 5.45z"/></svg>
            Get Access Now
        </a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let nodes = [];
    let mouse = { x: null, y: null };

    window.addEventListener('mousemove', (e) => {
        mouse.x = e.x;
        mouse.y = e.y;
    });

    function resize() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resize);
    resize();

    class Node {
        constructor() {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.vx = (Math.random() - 0.5) * 0.8; // Slightly faster
            this.vy = (Math.random() - 0.5) * 0.8;
            this.size = Math.random() * 2 + 1;
        }
        update() {
            this.x += this.vx;
            this.y += this.vy;
            if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
            if (this.y < 0 || this.y > canvas.height) this.vy *= -1;

            let dx = mouse.x - this.x;
            let dy = mouse.y - this.y;
            let dist = Math.sqrt(dx*dx + dy*dy);
            if(dist < 250) {
                this.x -= dx/80;
                this.y -= dy/80;
            }
        }
    }

    function init() {
        nodes = [];
        for(let i=0; i<120; i++) nodes.push(new Node());
    }

    function animate() {
        // CRAZY BACKGROUND UPGRADE: 
        // We use a slight "trail" effect by not clearing the canvas fully
        ctx.fillStyle = 'rgba(5, 5, 5, 0.15)'; 
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        nodes.forEach((n, i) => {
            n.update();
            
            // Draw Glow
            ctx.shadowBlur = 10;
            ctx.shadowColor = 'rgba(0, 242, 255, 0.5)';
            
            ctx.beginPath();
            ctx.arc(n.x, n.y, n.size, 0, Math.PI*2);
            ctx.fillStyle = 'rgba(0, 242, 255, 0.8)';
            ctx.fill();
            ctx.shadowBlur = 0; // Reset for lines

            for(let j=i; j<nodes.length; j++) {
                let dx = n.x - nodes[j].x;
                let dy = n.y - nodes[j].y;
                let dist = Math.sqrt(dx*dx + dy*dy);
                
                if(dist < 180) {
                    // Create a shifting color line
                    let alpha = (1 - dist/180);
                    ctx.strokeStyle = `rgba(0, 242, 255, ${alpha * 0.4})`;
                    ctx.lineWidth = alpha * 1.5;
                    ctx.beginPath();
                    ctx.moveTo(n.x, n.y);
                    ctx.lineTo(nodes[j].x, nodes[j].y);
                    ctx.stroke();
                }
            }
        });
        requestAnimationFrame(animate);
    }

    function joinVIP() {
        document.querySelector('.vip-card').style.transform = "scale(0.95)";
    }

    init();
    animate();
</script>

</body>
</html>
