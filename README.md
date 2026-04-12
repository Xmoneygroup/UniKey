<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Domain for Sale | Elite Offering</title>
    <style>
        /* Resetimi i stileve bazë */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden; /* Ndalon rrëshqitjen e ekranit */
            font-family: 'Cinzel', serif; /* Font mbretëror/luksoz */
            background-color: #000; /* Ngjyra bazë */
        }

        /* SFONDI PREMIUM GALAXY DINAMIK */
        .galaxy-background {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            
            /* Gradient kompleks që simulon galaksitë */
            background: radial-gradient(circle at 50% 50%, #1a0033 0%, #000000 100%),
                        radial-gradient(circle at 20% 30%, #2a0052 0%, transparent 40%),
                        radial-gradient(circle at 80% 70%, #001a33 0%, transparent 40%);
            background-size: 200% 200%; /* E bëjmë më të madh për animacion */
            
            /* Animacioni i lëvizjes së sfondit */
            animation: galaxyMove 15s ease-in-out infinite alternate;
        }

        /* EFEKTI I YJEVE (Shtohet si shtresë) */
        .galaxy-background::before {
            content: "";
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background-image: 
                radial-gradient(white, rgba(255,255,255,.2) 2px, transparent 3px),
                radial-gradient(white, rgba(255,255,255,.15) 1px, transparent 2px),
                radial-gradient(white, rgba(255,255,255,.1) 2px, transparent 3px);
            background-size: 550px 550px, 350px 350px, 250px 250px;
            background-position: 0 0, 40px 60px, 130px 270px;
            opacity: 0.6;
            animation: starsTwinkle 5s linear infinite;
        }

        /* TITULLI LUXURY ME ANIMACION TË BUZUR */
        .titulli-premium {
            position: relative;
            z-index: 10; /* Siguron që teksti të jetë mbi sfondin */
            font-size: 6rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 15px;
            text-align: center;
            margin: 0;
            padding: 0 20px;
            
            /* Efekti i tekstit si "Ar i Lëngshëm" */
            background: linear-gradient(to bottom, #fff 0%, #f1c40f 50%, #b8860b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            
            /* Hije e fuqishme për dimension */
            text-shadow: 0px 5px 15px rgba(241, 196, 15, 0.4),
                         0px 10px 30px rgba(0, 0, 0, 0.7);
            
            /* Animacioni i hyrjes dhe shkëlqimit */
            animation: premiumEntrance 2.5s ease-out forwards,
                       textGlow 4s ease-in-out infinite alternate 2.5s;
        }

        /* --- ANIMACIONET --- */

        /* Lëvizja e ngadaltë e galaksisë */
        @keyframes galaxyMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Shkëlqimi i lehtë i yjeve */
        @keyframes starsTwinkle {
            0%, 100% { opacity: 0.6; }
            50% { opacity: 0.3; }
        }

        /* Hyrja dramatike e titullit (Scale + FadeIn) */
        @keyframes premiumEntrance {
            0% {
                opacity: 0;
                transform: scale(0.8);
                letter-spacing: 50px;
                filter: blur(10px);
            }
            100% {
                opacity: 1;
                transform: scale(1);
                letter-spacing: 15px;
                filter: blur(0);
            }
        }

        /* Shkëlqimi i vazhdueshëm i arit */
        @keyframes textGlow {
            0% {
                text-shadow: 0px 5px 15px rgba(241, 196, 15, 0.4),
                             0px 10px 30px rgba(0, 0, 0, 0.7);
            }
            100% {
                text-shadow: 0px 5px 30px rgba(241, 196, 15, 0.8),
                             0px 10px 50px rgba(241, 196, 15, 0.4);
            }
        }

        /* PËRSHTATJA PËR CELULAR (Responsive) */
        @media (max-width: 1024px) {
            .titulli-premium {
                font-size: 4rem;
                letter-spacing: 8px;
            }
        }

        @media (max-width: 768px) {
            .titulli-premium {
                font-size: 2.2rem;
                letter-spacing: 5px;
                line-height: 1.2;
            }
        }

        /* Importimi i fontit nga Google Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&display=swap');
    </style>
</head>
<body>

    <div class="galaxy-background">
        <h1 class="titulli-premium">Domain<br>is for Sale</h1>
    </div>

</body>
</html>
