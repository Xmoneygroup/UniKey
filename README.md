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
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: radial-gradient(circle at center, rgba(0, 242, 255, 0.05) 0%, transparent 70%);
    }

    /* --- MAGNETIC TITLE --- */
    .title-wrapper { perspective: 1000px; }
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

    .subtitle-group {
        margin-top: 30px;
        text-align: center;
    }

    .subtitle {
        font-size: 14px;
        letter-spacing: 8px;
        text-transform: uppercase;
        color: var(--cyan);
        margin-bottom: 10px;
        opacity: 0;
        animation: fadeInUp 1s forwards 0.8s;
    }

    /* --- ELITE VIP CARD --- */
    .vip-card {
        margin-top: 50px;
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
        animation: fadeInUp 1s forwards 1.2s;
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
        display: block;
        text-align: center;
    }

    .join-btn:hover {
        background: var(--cyan);
        transform: scale(0.95);
    }

    #memberCounter {
        margin-top: 25px;
        font-family: 'Syncopate', sans-serif;
        font-size: 16px;
        color: rgba(255,255,255,0.4);
        letter-spacing: 2px;
        text-align: center;
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
    }
</style>
