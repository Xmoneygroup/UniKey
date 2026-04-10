<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Riparime Profesionale</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

    <style>
        /* CSS STYLE */
        body, html {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0a0a0a;
            color: white;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        #loader {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        .animate-title {
            font-size: 5rem;
            letter-spacing: 20px;
            font-weight: 900;
            text-transform: uppercase;
            color: #ffcc00;
            opacity: 0;
        }

        nav {
            position: fixed;
            top: 0; width: 100%;
            display: flex; justify-content: space-between;
            align-items: center;
            padding: 15px 40px;
            box-sizing: border-box;
            z-index: 1000;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo { font-weight: bold; font-size: 1.5rem; color: #ffcc00; }

        .lang-btn {
            background: transparent;
            border: 1px solid #ffcc00;
            color: white;
            padding: 5px 15px;
            cursor: pointer;
            transition: 0.3s;
        }

        .lang-btn:hover { background: #ffcc00; color: black; }

        .section {
            height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            padding: 0 10%;
        }

        .canvas-container {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 1;
        }

        .content {
            position: relative;
            z-index: 2;
            max-width: 500px;
            background: rgba(0, 0, 0, 0.6);
            padding: 30px;
            border-left: 5px solid #ffcc00;
            backdrop-filter: blur(5px);
        }

        h2 { font-size: 2.5rem; margin-bottom: 10px; }
        p { font-size: 1.2rem; line-height: 1.6; opacity: 0.9; }

        .footer-info {
            padding: 100px 20px;
            text-align: center;
            background: #000;
            border-top: 2px solid #ffcc00;
        }

        .footer-logo { font-size: 4rem; font-weight: 900; color: #ffcc00; margin-bottom: 20px; }
        
        .contact-card {
            font-size: 1.3rem;
            line-height: 2;
        }

        a { color: #ffcc00; text-decoration: none; font-weight: bold; }
    </style>
</head>
<body>

    <div id="loader">
        <h1 class="animate-title" id="main-logo">UNIKEY</h1>
    </div>

    <nav>
        <div class="logo">UNIKEY</div>
        <div>
            <button class="lang-btn" onclick="translateTo('sq')">SQ</button>
            <button class="lang-btn" onclick="translateTo('en')">EN</button>
        </div>
    </nav>

    <section class="section" id="sec1">
        <div class="canvas-container" id="canvas-key"></div>
        <div class="content">
            <h2 id="t1">Duplikat Çelsash</h2>
            <p id="d1">Punojmë të gjithë çelsat e të gjitha makinave. Riparime dhe duplikate me saktësi maksimale.</p>
        </div>
    </section>

    <section class="section" id="sec2">
        <div class="canvas-container" id="canvas-lock"></div>
        <div class="content">
            <h2 id="t2">Bravat e Makinave</h2>
            <p id="d2">Riparim profesional i bravave të derës. Shpartallojmë problemin dhe e rregullojmë si të ri.</p>
        </div>
    </section>

    <section class="section" id="sec3">
        <div class="canvas-container" id="canvas-window"></div>
        <div class="content">
            <h2 id="t3">Mekanizmat e Dritareve</h2>
            <p id="d3">Dritarja juaj nuk hapet? Ne riparojmë çdo mekanizëm të dritareve të makinave në kohë rekord.</p>
        </div>
    </section>

    <section class="footer-info">
        <div class="footer-logo">UNIKEY</div>
        <div class="contact-card">
            <p id="exp">Punojmë gati 15 vite me këtë zanat.</p>
            <p id="hours">Orari: 09:30 - 19:00 (E hënë - E shtunë)</p>
            <p>Mjeshtri: <strong>Muhamed Musili</strong></p>
            <p>Tel: <a href="tel:+389070229348">+389 070 229 348</a></p>
        </div>
    </section>

    <script>
        // LOGJIKA E PËRKTHIMIT
        const data = {
            sq: {
                t1: "Duplikat Çelsash", d1: "Punojmë të gjithë çelsat e të gjitha makinave. Riparime dhe duplikate me saktësi maksimale.",
                t2: "Bravat e Makinave", d2: "Riparim profesional i bravave të derës. Shpartallojmë problemin dhe e rregullojmë si të ri.",
                t3: "Mekanizmat e Dritareve", d3: "Dritarja juaj nuk hapet? Ne riparojmë çdo mekanizëm të dritareve të makinave në kohë rekord.",
                exp: "Punojmë gati 15 vite me këtë zanat.", hours: "Orari: 09:30 - 19:00 (E hënë - E shtunë)"
            },
            en: {
                t1: "Key Duplication", d1: "We work on all types of car keys. High precision repairs and duplicates.",
                t2: "Car Door Locks", d2: "Professional repair of car door locks. We dismantle the problem and fix it like new.",
                t3: "Window Mechanisms", d3: "Window not opening? We repair every car window mechanism in record time.",
                exp: "Nearly 15 years of experience in this craft.", hours: "Hours: 09:30 - 19:00 (Monday - Saturday)"
            }
        };

        function translateTo(lang) {
            document.getElementById('t1').innerText = data[lang].t1;
            document.getElementById('d1').innerText = data[lang].d1;
            document.getElementById('t2').innerText = data[lang].t2;
            document.getElementById('d2').innerText = data[lang].d2;
            document.getElementById('t3').innerText = data[lang].t3;
            document.getElementById('d3').innerText = data[lang].d3;
            document.getElementById('exp').innerText = data[lang].exp;
            document.getElementById('hours').innerText = data[lang].hours;
        }

        // ANIMACIONI HYRËS
        gsap.registerPlugin(ScrollTrigger);
        window.addEventListener('load', () => {
            const tl = gsap.timeline();
            tl.to(".animate-title", { opacity: 1, letterSpacing: "5px", duration: 1.5, ease: "power4.out" })
              .to("#loader", { y: "-100%", duration: 1, delay: 0.5, ease: "expo.inOut" });
        });

        // FUNKSIONI PËR KRIJIMIN E OBJEKTEVE 3D QË SHPARTALLOHEN
        function createExploding3D(containerId, color) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            
            const container = document.getElementById(containerId);
            renderer.setSize(window.innerWidth, window.innerHeight);
            container.appendChild(renderer.domElement);

            const group = new THREE.Group();
            const pieces = [];
            const pieceCount = 30;

            // Krijojmë pjesët e "shpartalluara" (kubikë dhe cilindra si vegla)
            for (let i = 0; i < pieceCount; i++) {
                const geometry = i % 2 === 0 ? new THREE.BoxGeometry(0.4, 0.4, 0.4) : new THREE.CylinderGeometry(0.1, 0.1, 0.8);
                const material = new THREE.MeshStandardMaterial({ color: color, metalness: 0.8, roughness: 0.2 });
                const mesh = new THREE.Mesh(geometry, material);
                
                // Pozicioni fillestar (i bashkuar)
                mesh.position.set(0,0,0);
                pieces.push(mesh);
                group.add(mesh);
            }
            scene.add(group);

            const light = new THREE.DirectionalLight(0xffffff, 1);
            light.position.set(5, 5, 5);
            scene.add(light);
            scene.add(new THREE.AmbientLight(0x404040));
            camera.position.z = 6;

            // Animacioni Bumerang (Shpartallim 5 sekonda)
            gsap.to(pieces.map(p => p.position), {
                x: () => (Math.random() - 0.5) * 12,
                y: () => (Math.random() - 0.5) * 12,
                z: () => (Math.random() - 0.5) * 12,
                duration: 2.5, // 2.5 sekonda hapje
                repeat: -1, 
                yoyo: true, // 2.5 sekonda mbyllje (Totali 5s)
                ease: "power2.inOut",
                stagger: 0.01,
                scrollTrigger: {
                    trigger: `#${containerId}`,
                    start: "top center",
                }
            });

            function animate() {
                requestAnimationFrame(animate);
                group.rotation.y += 0.005;
                renderer.render(scene, camera);
            }
            animate();

            window.addEventListener('resize', () => {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
            });
        }

        // Inicializimi i 3 seksioneve me ngjyra metalike
        createExploding3D('canvas-key', 0xffcc00);  // Ngjyrë ari për çelsat
        createExploding3D('canvas-lock', 0x999999); // Ngjyrë argjendi për bravat
        createExploding3D('canvas-window', 0x4444ff); // Ngjyrë blu për mekanizmat
    </script>
</body>
</html>
