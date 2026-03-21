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

        /* --- MARKET TICKER --- */
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

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 60px 20px;
        }

        /* --- NEW ANIMATED TITLE --- */
        .title-wrapper { 
            perspective: 1000px; 
            margin-bottom: 20px; 
            text-align: center;
            transition: transform 0.1s ease-out;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(60px, 15vw, 180px);
            font-weight: 700;
            text-transform: uppercase;
            line-height: 0.9;
            letter-spacing: -5px;
            position: relative;
            background: linear-gradient(180deg, #fff 30%, #444 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px rgba(255,255,255,0.1));
            animation: titleReveal 1.5s cubic-bezier(0.77, 0, 0.175, 1) forwards;
        }

        .title::after {
            content: 'Xmoney';
            position: absolute;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            -webkit-text-stroke: 1px rgba(255,255,255,0.2);
            -webkit-text-fill-color: transparent;
            transform: translate(8px, 8px);
        }

        @keyframes titleReveal {
            0% { opacity: 0; transform: translateY(50px) rotateX(-30deg); letter-spacing: 20px; filter: blur(10px); }
            100% { opacity: 1; transform: translateY(0) rotateX(0deg); letter-spacing: -5px; filter: blur(0); }
        }

        .manifesto-container { max-width: 750px; text-align: center; margin-bottom: 50px; }
        .manifesto-text {
            font-size: 14px;
            line-height: 1.6;
            color: rgba(255,255,255,0.4);
            margin-bottom: 24px;
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: 3px;
            opacity: 0;
            animation: fadeIn 1s forwards 1.2s;
        }

        .highlight-cyan { color: var(--cyan); text-shadow: 0 0 10px var(--cyan); }

        /* --- VIP CARD --- */
        .vip-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.05) 0%, rgba(0,0,0,0.9) 100%);
            border: 1px solid var(--border);
            padding: 40px;
            width: 100%;
            max-width: 450px;
            border-radius: 24px;
            backdrop-filter: blur(30px);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeIn 1s forwards 1.5s;
            box-shadow: 0 40px 80px rgba(0,0,0,0.8);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .vip-card:hover { border-color: var(--cyan); transform: translateY(-5px); }

        .verified-badge {
            position: absolute;
            top: -12px;
            right: 30px;
            background: #fff;
            color: #000;
            font-size: 10px;
            font-weight: 800;
            padding: 4px 15px;
            border-radius: 4px;
            text-transform: uppercase;
        }

        .features-list { list-style: none; margin-bottom: 30px; }
        .features-list li {
            padding: 18px 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            justify-content: space-between;
        }

        .join-btn {
            width: 100%;
            padding: 22px;
            background: #fff;
            color: #000;
            border-radius: 12px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 3px;
            cursor: pointer;
            text-decoration: none;
            display: block;
            text-align: center;
            transition: 0.3s ease;
        }

        .join-btn:hover { background: var(--cyan); transform: scale(1.02); box-shadow: 0 0 40px rgba(0, 242, 255, 0.3); }

        @keyframes fadeIn { to { opacity: 1; transform: translateY(0); } }

        @media(max-width: 768px) { .title { font-size: 70px; letter-spacing: -2px; } }
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
    <div class="title-wrapper" id="titleMove">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text">
            Institutional Grade <span class="highlight-cyan">Intelligence</span>
        </p>
    </div>

    <div class="vip-card" id="vipCard">
        <div class="verified-badge">Access Level: VIP</div>
        <ul class="features-list">
            <li><span>Daily Signals</span> <span class="highlight-cyan">3+</span></li>
            <li><span>Avg Accuracy</span> <span class="highlight-cyan">88.4%</span></li>
            <li><span>Network</span> <span class="highlight-cyan">PRIVATE</span></li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Enter Terminal</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let w, h;
    let stars = [];
    let speedMult = 1.2; 
    let targetSpeed = 1.2;
    
    function resize() {
        w = canvas.width = window.innerWidth;
        h = canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resize);
    resize();

    // Mouse tilt for Title
    const title = document.getElementById('titleMove');
    document.addEventListener('mousemove', (e) => {
        let x = (window.innerWidth / 2 - e.pageX) / 25;
        let y = (window.innerHeight / 2 - e.pageY) / 25;
        title.style.transform = `rotateY(${x}deg) rotateX(${y}deg)`;
    });

    class Star {
        constructor() { this.reset(); }
        reset() {
            this.x = (Math.random() - 0.5) * w * 2.5;
            this.y = (Math.random() - 0.5) * h * 2.5;
            this.z = Math.random() * w; 
            this.pz = this.z; 
            this.color = Math.random() > 0.5 ? 'rgba(0, 242, 255,' : 'rgba(212, 175, 55,';
        }
        update() {
            this.pz = this.z;
            this.z -= speedMult;
            if (this.z < 1) { this.reset(); this.pz = this.z; }
        }
        draw() {
            let sx = ((this.x / this.z) * w) + w / 2;
            let sy = ((this.y / this.z) * h) + h / 2;
            let px = ((this.x / this.pz) * w) + w / 2;
            let py = ((this.y / this.pz) * h) + h / 2;
            ctx.beginPath();
            let alpha = 1 - (this.z / w);
            ctx.strokeStyle = this.color + alpha + ')';
            ctx.lineWidth = alpha * 2;
            ctx.moveTo(px, py);
            ctx.lineTo(sx, sy);
            ctx.stroke();
        }
    }

    function init() {
        stars = [];
        for (let i = 0; i < 350; i++) stars.push(new Star());
    }

    function animate() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.08)";
        ctx.fillRect(0, 0, w, h);
        if (Math.abs(speedMult - targetSpeed) > 0.01) {
            speedMult += (targetSpeed - speedMult) * 0.02;
        }
        stars.forEach(s => { s.update(); s.draw(); });
        requestAnimationFrame(animate);
    }

    const card = document.getElementById('vipCard');
    card.addEventListener('mouseenter', () => targetSpeed = 0.2);
    card.addEventListener('mouseleave', () => targetSpeed = 1.2);

    function joinVIP() { 
        targetSpeed = 0.05; 
        setTimeout(() => { targetSpeed = 1.2; }, 3000);
    }

    init();
    animate();
</script>

</body>
</html>
