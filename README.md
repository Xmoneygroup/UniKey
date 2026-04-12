
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Domaini është në Shitje</title>
    <style>
        /* CSS i integruar */
        body {
            margin: 0;
            padding: 0;
            font-family: 'Playfair Display', serif; /* Font luksoz */
            background-color: #1a1a1a; /* Ngjyrë e errët për sfondin */
        }

        .sfondi-luksoz {
            /* Këtu vendosni linkun e fotos tuaj premium */
            background-image: url('imazhi-sfondit-luksoz.jpg'); 
            background-size: cover;
            background-position: center;
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden; /* Fsheh skajet e animacionit */
            position: relative;
        }

        /* Shtojmë një overlay të errët që teksti të duket më "Elite" */
        .sfondi-luksoz::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0, 0, 0, 0.4);
        }

        .titulli-animuar {
            position: relative;
            z-index: 1;
            font-size: 5rem;
            color: #f1c40f; /* Ngjyrë ari */
            text-transform: uppercase;
            letter-spacing: 5px;
            animation: fadeInSlideIn 3s ease-in-out forwards; /* Emri i animacionit */
            text-shadow: 0px 10px 20px rgba(0, 0, 0, 0.8); /* Hije e rëndë luksoze */
            text-align: center;
        }

        /* Animacioni Fade In dhe Slide In */
        @keyframes fadeInSlideIn {
            0% {
                opacity: 0;
                transform: translateY(50px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Përshtatja për celular */
        @media (max-width: 768px) {
            .titulli-animuar {
                font-size: 2.5rem;
                letter-spacing: 2px;
            }
        }
    </style>
</head>
<body>

    <div class="sfondi-luksoz">
        <h1 class="titulli-animuar">Domain is for Sale</h1>
    </div>

</body>
</html>
