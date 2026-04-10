<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY | Auto Tech Specialists</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Inter:wght@300;900&display=swap" rel="stylesheet">

    <style>
        :root {
            --accent: #ffcc00;
            --dark-grey: #111111;
        }

        body, html {
            margin: 0; padding: 0;
            background: #000;
            color: #fff;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
        }

        /* 1. SUPER INTRO ANIMATION */
        #loader {
            position: fixed; inset: 0;
            background: #000;
            display: flex; justify-content: center; align-items: center;
            z-index: 9999;
        }

        .unikey-glitch {
            font-family: 'Syncopate', sans-serif;
            font-size: 10vw;
            font-weight: 700;
            letter-spacing: 2vw;
            color: var(--accent);
            position: relative;
        }

        /* 2. BACKGROUND MESH (SHTRESA E PARË) */
        #bg-canvas {
            position: fixed; top: 0; left: 0;
            z-index: -1;
            opacity: 0.4;
        }

        /* 3. NAVIGATION */
        nav {
            position: fixed; top: 0; width: 100%;
            padding: 40px; display: flex; justify-content: space-between;
            z-index: 1000;
        }

        .lang-toggle {
            display: flex; gap: 10px;
        }

        .lang-toggle button {
            background: none; border: 1px solid rgba(255,255,255,0.2);
            color: #fff; padding: 5px 15px; cursor: pointer;
            font-family: 'Syncopate'; font-size: 10px;
        }

        .lang-toggle button:hover { border-color: var(--accent); color: var(--accent); }

        /* 4. MAIN CONTENT */
        .hero {
            height: 100vh;
            display: flex; flex-direction: column;
            justify-content: center; padding: 0 10%;
        }

        .hero h1 {
            font-family: 'Syncopate'; font-size: 8vw; line-height: 1;
            margin: 0; text-transform: uppercase;
        }

        .hero .highlight { color: var(--accent); }

        section {
            min-height: 100vh;
            display: flex; align-items: center;
            padding: 100px 10%;
            position: relative;
        }

        .service-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 60px;
            max-width: 600px;
            position: relative;
            z-index: 10;
        }

        .service-card h2 {
            font-family: 'Syncopate'; font-size: 3rem; margin-bottom: 20px;
            color: var(--accent);
        }

        .service-card p {
            font-size: 1.2rem; line-height: 1.8; opacity: 0.7; font-weight: 300;
        }

        /* 5. 3D CONTAINER FOR EACH SECTION */
        .three-container {
            position: absolute; right: 0; top: 0;
            width: 50vw; height: 100%;
            z-index: 1;
        }

        /* 6. CONTACT FOOTER */
        footer {
            padding: 100px 10%;
            background: var(--dark-grey);
            border-top: 1px solid var(--accent);
        }

        .footer-grid {
            display: grid; grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        .contact-number {
            font-family: 'Syncopate'; font-size: 3vw;
            color: var(--accent); text-decoration: none;
        }

        .info-txt { font-size: 1.5rem; opacity: 0.8; margin: 10px 0; }
    </style>
</head>
<body>

    <div id="loader">
        <div class="unikey-glitch" id="intro-text">UNIKEY</div>
    </div>

    <canvas id="bg-canvas"></canvas>

    <nav>
        <div style="font-family: 'Syncopate'; font-weight: 700; font-size: 1.5rem;">UK // 2026</div>
        <div class="lang-toggle">
            <button onclick="changeLang('sq')">ALB</button>
            <button onclick="changeLang('en')">ENG</button>
        </div>
    </nav>

    <main>
        <div class="hero">
            <h1 id="h-title">TEKNOLOGJIA <br><span class="highlight">E ÇELSAVE</span></h1>
            <p style="font-size: 1.5rem; max-width: 600px; margin-top: 20px;" id="h-sub">
                Lider në riparimin dhe kodimin e avancuar të të gjitha markave të makinave.
            </p>
        </div>

        <section id="s1">
            <div class="service-card">
                <h2 id="t1">ÇELSA DUPLIKAT</h2>
                <p id="d1">Nuk mbeteni kurrë jashtë. Ne krijojmë kopje perfekte për çdo lloj çelësi inteligjent ose mekanik me garanci të plotë.</p>
            </div>
            <div class="three-container" id="c1"></div>
        </section>

        <section id="s2">
            <div class="three-container" style="left: 0;" id="c2"></div>
            <div class="service-card" style="margin-left: auto;">
                <h2 id="t2">BRAVA & XHAMA</h2>
                <p id="d2">Riparojmë bravat e bllokuara dhe mekanizmat elektronikë të dritareve. Siguri që nuk njeh kompromis.</p>
            </div>
        </section>

        <section id="s3">
            <div class="service-card">
                <h2 id="t3">DIAGNOSTIKË</h2>
                <p id="d3">Skanim i moduleve elektronike të makinës, fshirje e gabimeve dhe përditësim i sistemeve qendrore.</p>
            </div>
            <div class="three-container" id="c3"></div>
        </section>
    </main>

    <footer>
        <div class="footer-grid">
            <div>
                <h2 style="font-family: 'Syncopate'; color: var(--accent);">UNIKEY</h2>
                <p class="info-txt" id="f1">Përvojë mbi 15 vite në riparimin e sistemeve të sigurisë auto.</p>
                <p class="info-txt" id="f2">Hapur: 09:30 - 19:00 (Hënë - Shtunë)</p>
            </div>
            <div style="text-align: right;">
                <p>TELEFONONI MJESHTRIN:</p>
                <a href="tel:+389070229348" class="contact-number">+389 070 229 348</a>
            </div>
        </div>
    </footer>

    <script>
        // DATA PËR GJUHËT
        const langData = {
            sq: {
                h_title: "TEKNOLOGJIA <br><span class='highlight'>E ÇELSAVE</span>",
                h_sub: "Lider në riparimin dhe kodimin e avancuar të të gjitha markave të makinave.",
                t1: "ÇELSA DUPLIKAT", d1: "Nuk mbeteni kurrë jashtë. Ne krijojmë kopje perfekte për çdo lloj çelësi inteligjent ose mekanik me garanci të plotë.",
                t2: "BRAVA & XHAMA", d2: "Riparojmë bravat e bllokuara dhe mekanizmat elektronikë të dritareve. Siguri që nuk njeh kompromis.",
                t3: "DIAGNOSTIKË", d3: "Skanim i moduleve elektronike të makinës, fshirje e gabimeve dhe përditësim i sistemeve qendrore.",
                f1: "Përvojë mbi 15 vite në riparimin e sistemeve të sigurisë auto.", f2: "Hapur: 09:30 - 19:00 (Hënë - Shtunë)"
            },
            en: {
                h_title: "CAR KEY <br><span class='highlight'>TECHNOLOGY</span>",
                h_sub: "Leader in advanced repair and coding for all car brands.",
                t1: "KEY DUPLICATION", d1: "Never get locked out. We create perfect copies for every smart or mechanical key with full warranty.",
                t2: "LOCKS & WINDOWS", d2: "We repair jammed locks and electronic window mechanisms. Uncompromising security.",
                t3: "DIAGNOSTICS", d3: "Scanning car electronic modules, clearing errors, and updating central systems.",
                f1: "Over 15 years of experience in auto security systems.", f2: "Open: 09:30 - 19:00 (Mon - Sat)"
            }
        };

        function changeLang(l) {
            Object.keys(langData[l]).forEach(id => {
                document.getElementById(id).innerHTML = langData[l][id];
            });
        }

        // 1. INTRO ANIMATION
        gsap.registerPlugin(ScrollTrigger);
        const tl = gsap.timeline();
        tl.from("#intro-text", { letterSpacing: "-10vw", opacity: 0, duration: 2, ease: "power4.out" })
          .to("#loader", { clipPath: "polygon(0 0, 100% 0, 100% 0, 0 0)", duration: 1.2, ease: "expo.inOut" });

        // 2. BACKGROUND PARTICLES (Three.js)
        const bgScene = new THREE.Scene();
        const bgCam = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
        const bgRenderer = new THREE.WebGLRenderer({ canvas: document.getElementById('bg-canvas'), alpha: true });
        bgRenderer.setSize(window.innerWidth, window.innerHeight);

        const starGeo = new THREE.BufferGeometry();
        const starCount = 2000;
        const posArray = new Float32Array(starCount * 3);
        for(let i=0; i<starCount*3; i++) posArray[i] = (Math.random() - 0.5) * 10;
        starGeo.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
        const starMat = new THREE.PointsMaterial({ size: 0.005, color: 0xffcc00 });
        const starMesh = new THREE.Points(starGeo, starMat);
        bgScene.add(starMesh);
        bgCam.position.z = 2;

        function animateBg() {
            requestAnimationFrame(animateBg);
            starMesh.rotation.y += 0.001;
            bgRenderer.render(bgScene, bgCam);
        }
        animateBg();

        // 3. SECTION ANIMATIONS (BUMERANG)
        function createService3D(containerId, color) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, 1, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            const container = document.getElementById(containerId);
            renderer.setSize(container.offsetWidth, container.offsetHeight);
            container.appendChild(renderer.domElement);

            const group = new THREE.Group();
            const pieces = [];
            // Krijo "pjesë mekanike"
            for(let i=0; i<50; i++) {
                const geo = new THREE.BoxGeometry(Math.random()*0.5, 0.05, 0.1);
                const mat = new THREE.MeshStandardMaterial({ color: color, metalness: 1, roughness: 0.3 });
                const mesh = new THREE.Mesh(geo, mat);
                group.add(mesh);
                pieces.push(mesh);
            }
            scene.add(group);
            scene.add(new THREE.AmbientLight(0xffffff, 0.5));
            const pLight = new THREE.PointLight(0xffffff, 1);
            pLight.position.set(5,5,5);
            scene.add(pLight);
            camera.position.z = 5;

            // Bumerang 5 sekonda (Hapje 2.5s, Mbyllje 2.5s)
            gsap.to(pieces.map(p => p.position), {
                x: () => (Math.random() - 0.5) * 10,
                y: () => (Math.random() - 0.5) * 10,
                z: () => (Math.random() - 0.5) * 10,
                rotationX: () => Math.random() * 5,
                duration: 2.5,
                repeat: -1,
                yoyo: true,
                ease: "power2.inOut",
                stagger: 0.01,
                scrollTrigger: {
                    trigger: `#${containerId}`,
                    start: "top center"
                }
            });

            function animate() {
                requestAnimationFrame(animate);
                group.rotation.y += 0.005;
                renderer.render(scene, camera);
            }
            animate();
        }

        createService3D('c1', 0xffcc00); // Gold
        createService3D('c2', 0x555555); // Silver
        createService3D('c3', 0xff0000); // Red (Alert/Diag)

    </script>
</body>
</html>
