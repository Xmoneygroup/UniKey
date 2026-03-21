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

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #000; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

        canvas { position: fixed; top: 0; left: 0; z-index: 0; pointer-events: none; }

        /* --- FAKE MARKET TICKER --- */
        .ticker-wrap {
            position: fixed;
            top: 0;
            width: 100%;
            overflow: hidden;
            height: 35px;
            background: rgba(0, 0, 0, 0.8);
            border-bottom: 1px solid var(--border);
            z-index: 999;
            display: flex;
            align-items: center;
        }

        .ticker {
            display: flex;
            white-space: nowrap;
            animation: ticker 30s linear infinite;
        }

        .ticker-item {
            padding: 0 30px;
            font-size: 10px;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: 600;
        }

        .up { color: #00ff88; }
        .down { color: #ff3e3e; }

        @keyframes ticker {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* --- LIVE STATUS BADGE --- */
        .status-container {
            position: absolute;
            top: 60px;
            display: flex;
            gap: 20px;
            animation: fadeInUp 1s forwards;
        }

        .status-pill {
            background: rgba(255,255,255,0.05);
            border: 1px solid var(--border);
            padding: 6px 15px;
            border-radius: 50px;
            font-size: 9px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .dot { width: 6px; height: 6px; background: #00ff88; border-radius: 50%; box-shadow: 0 0 10px #00ff88; animation: pulse 1.5s infinite; }

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 100px 20px;
        }

        .title-wrapper { perspective: 1000px; margin-bottom: 30px; text-align: center; }
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(50px, 12vw, 150px);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -2px;
            background: linear-gradient(to bottom, #fff 40%, #555 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: titleEntrance 1.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .manifesto-container { max-width: 750px; text-align: center; margin-bottom: 50px; }
        .manifesto-text {
            font-size: 16px;
            line-height: 1.6;
            color: rgba(255,255,255,0.6);
            margin-bottom: 24px;
            font-weight: 300;
            letter-spacing: 1px;
            opacity: 0;
            animation: textReveal 1.2s forwards;
        }

        .highlight-cyan { color: var(--cyan); font-weight: 600; }

        /* --- VIP CARD --- */
        .vip-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.05) 0%, rgba(0,0,0,0.8) 100%);
            border: 1px solid var(--border);
            padding: 40px;
            width: 100%;
            max-width: 450px;
            border-radius: 20px;
            backdrop-filter: blur(20px);
            opacity: 0;
            transform: translateY(40px);
            animation: cardEntrance 1.5s forwards 0.8s;
            box-shadow: 0 50px 100px rgba(0,0,0,0.5);
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .verified-badge {
            position: absolute;
            top: -15px;
            right: 20px;
            background: var(--cyan);
            color: black;
            font-size: 9px;
            font-weight: 900;
            padding: 5px 12px;
            border-radius: 4px;
            text-transform: uppercase;
        }

        .features-list { list-style: none; margin-bottom: 30px; }
        .features-list li {
            padding: 15px 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            justify-content: space-between;
        }

        .join-btn {
            width: 100%;
            padding: 20px;
            background: white;
            color: black;
            border: none;
            border-radius: 10px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            text-decoration: none;
            display: block;
            text-align: center;
            transition: 0.3s;
        }

        .join-btn:hover { background: var(--cyan); box-shadow: 0 0 30px rgba(0, 242, 255, 0.4); }

        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }
        @keyframes textReveal { to { opacity: 1; transform: translateY(0); } }
        @keyframes cardEntrance { to { opacity: 1; transform: translateY(0); } }

        @media(max-width: 768px) { .title { font-size: 60px; } }
    </style>
</head>
<body>

<div class="ticker-wrap">
    <div class="ticker">
        <span class="ticker-item">BTC/USD <span class="up">$64,231.12 (+2.4%)</span></span>
        <span class="ticker-item">ETH/USD <span class="up">$3,452.10 (+1.8%)</span></span>
        <span class="ticker-item">XAU/USD <span class="down">$2,341.05 (-0.4%)</span></span>
        <span class="ticker-item">EUR/USD <span class="up">1.0842 (+0.1%)</span></span>
        <span class="ticker-item">BTC/USD <span class="up">$64,231.12 (+2.4%)</span></span>
        <span class="ticker-item">ETH/USD <span class="up">$3,452.10 (+1.8%)</span></span>
        <span class="ticker-item">XAU/USD <span class="down">$2,341.05 (-0.4%)</span></span>
        <span class="ticker-item">EUR/USD <span class="up">1.0842 (+0.1%)</span></span>
    </div>
</div>

<canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="status-container">
        <div class="status-pill"><div class="dot"></div> SERVER: OPERATIONAL</div>
        <div class="status-pill">MEMBERS: 12,762</div>
    </div>

    <div class="title-wrapper">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text" style="animation-delay: 0.4s">
            The market has <span class="highlight-cyan">zero mercy</span> for anyone. Without discipline, losses are inevitable.
        </p>
        <p class="manifesto-text" style="animation-delay: 0.6s">
            Join the <span class="highlight-cyan">Elite 1%</span>. We provide the tools, the strategy, and the signals.
        </p>
    </div>

    <div class="vip-card" id="vipCard">
        <div class="verified-badge">Verified Group</div>
        <ul class="features-list">
            <li><span>Daily Signals</span> <span class="highlight-cyan">3+</span></li>
            <li><span>Win Rate</span> <span class="highlight-cyan">60% AVG</span></li>
            <li><span>Community</span> <span class="highlight-cyan">VIP CHAT</span></li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Join Private Group</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let w, h;
    let stars = [];
    let speedMult = 18; // Crazy high speed
    let targetSpeed = 18;
    
    function resize() {
        w = canvas.width = window.innerWidth;
        h = canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resize);
    resize();

    // 3D Perspective Warp Speed Model
    class Star {
        constructor() {
            this.reset();
        }

        reset() {
            this.x = (Math.random() - 0.5) * w * 2;
            this.y = (Math.random() - 0.5) * h * 2;
            this.z = Math.random() * w; 
            this.pz = this.z; 
            this.color = Math.random() > 0.5 ? '#00f2ff' : '#d4af37';
        }

        update() {
            this.pz = this.z;
            this.z -= speedMult;

            if (this.z < 1) {
                this.reset();
                this.pz = this.z;
            }
        }

        draw() {
            // Perspective Projection logic
            let sx = ((this.x / this.z) * w) + w / 2;
            let sy = ((this.y / this.z) * h) + h / 2;
            
            let px = ((this.x / this.pz) * w) + w / 2;
            let py = ((this.y / this.pz) * h) + h / 2;

            ctx.beginPath();
            ctx.strokeStyle = this.color;
            // Lines get thicker as they approach the camera
            ctx.lineWidth = (1 - this.z / w) * 3;
            ctx.lineCap = 'round';
            ctx.moveTo(px, py);
            ctx.lineTo(sx, sy);
            ctx.stroke();
        }
    }

    function init() {
        stars = [];
        for (let i = 0; i < 800; i++) stars.push(new Star());
    }

    function animate() {
        // Creates the "ghosting" trail effect
        ctx.fillStyle = "rgba(0, 0, 0, 0.25)";
        ctx.fillRect(0, 0, w, h);

        // Smooth speed transition logic
        if (Math.abs(speedMult - targetSpeed) > 0.1) {
            speedMult += (targetSpeed - speedMult) * 0.05;
        }

        stars.forEach(s => {
            s.update();
            s.draw();
        });

        requestAnimationFrame(animate);
    }

    // INTERACTION: Hover Slowdown
    const card = document.getElementById('vipCard');
    card.addEventListener('mouseenter', () => targetSpeed = 0.8);
    card.addEventListener('mouseleave', () => targetSpeed = 18);

    // INTERACTION: Click "Special" Slowdown (3 Seconds)
    function joinVIP() { 
        document.getElementById('vipCard').style.transform = "scale(0.95)"; 
        
        targetSpeed = 0.1; // Sudden cinematic brake
        
        setTimeout(() => {
            targetSpeed = 18; // Warp back to high speed
        }, 3000);
    }

    init();
    animate();
</script>

</body>
</html>
