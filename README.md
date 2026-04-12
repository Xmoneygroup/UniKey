<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain Asset | Model 2</title>
    <style>
        /* --- SFONDI "MËNDAFSH I LËNGSHËM" (CSS ONLY) --- */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000; /* Baza e zezë */
            font-family: 'Poppins', sans-serif; /* Font modern, pastër */
        }

        .liquid-background {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            
            /* SHTRESËZIMI I GRADIENTËVE (Sekreti i dizajnit) */
            /* Krijon re ngjyrash premium (Vjollcë e thellë, Blu mbretërore, Pak Ar) */
            background: 
                radial-gradient(circle at 10% 20%, rgba(26, 0, 77, 0.8) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(0, 51, 102, 0.8) 0%, transparent 40%),
                radial-gradient(circle at 50% 50%, rgba(13, 13, 13, 1) 0%, rgba(0, 0, 0, 1) 100%);
            background-size: 200% 200%; /* E bëjmë më të madh për animacion */
            
            /* Animacioni i lëvizjes së ngadaltë si lëng */
            animation: liquidMove 15s ease-in-out infinite alternate;
        }

        /* Shtojmë një efekt shkëlqimi (Glow) të shpërndarë */
        .liquid-background::after {
            content: "";
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: radial-gradient(circle at 70% 30%, rgba(212, 175, 55, 0.1) 0%, transparent 50%);
            filter: blur(50px);
        }

        /* --- TITULLI PREMIUM --- */
        .premium-content {
            position: relative;
            z-index: 10;
            text-align: center;
        }

        .title {
            font-size: 5rem;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 15px;
            margin: 0;
            
            /* Efekti i tekstit si Ar i shkrirë */
            background: linear-gradient(to bottom, #ffffff 0%, #f1c40f 50%, #b8860b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            
            /* Shkëlqim i pastër i arit */
            filter: drop-shadow(0 0 10px rgba(241, 196, 15, 0.4));
            
            /* Animacioni i hyrjes */
            animation: fadeInScale 2s ease-out forwards;
        }

        .sub-title {
            color: rgba(255, 255, 255, 0.5);
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 8px;
            margin-top: 15px;
            opacity: 0;
            animation: fadeIn 2s ease-out forwards 1.5s; /* Del me vonesë */
        }

        /* --- ANIMACIONET --- */

        /* Lëvizja e ngadaltë dhe e lëngshme e sfondit */
        @keyframes liquidMove {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Hyrja me shkallëzim dhe zbehtje */
        @keyframes fadeInScale {
            0% {
                opacity: 0;
                transform: scale(0.9);
                filter: blur(10px);
            }
            100% {
                opacity: 1;
                transform: scale(1);
                filter: blur(0);
            }
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        /* PËRSHTATJA PËR CELULAR (Responsive) */
        @media (max-width: 1024px) {
            .title { font-size: 3.5rem; letter-spacing: 8px; }
        }

        @media (max-width: 768px) {
            .title { font-size: 2.2rem; letter-spacing: 4px; }
            .sub-title { font-size: 0.8rem; letter-spacing: 4px; }
        }

        /* Importimi i fontit */
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@900&display=swap');
    </style>
</head>
<body>

    <div class="liquid-background">
        <div class="premium-content">
            <h1 class="title">This Domain<br>is for Sale</h1>
            <p class="sub-title">Elite Digital Real Estate</p>
        </div>
    </div>

</body>
</html>
