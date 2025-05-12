<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta para Briyidth - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Raleway:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #ff00aa;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            font-family: 'Raleway', sans-serif;
            overflow: hidden;
            color: #ffffff;
            text-align: center;
            padding: 20px;
        }
        .intro {
            font-size: 28px;
            margin-bottom: 20px;
            color: #ffd700;
            text-shadow: 2px 2px 10px #ff007f;
            font-family: 'Pacifico', cursive;
        }
        .card-container {
            position: relative;
            width: 300px;
            height: 200px;
            background-color: #ff4d94;
            border-radius: 15px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.8s ease-in-out;
        }
        .card-container.opened {
            transform: scale(1.1) rotateX(180deg);
        }
        .card-container .paper {
            position: absolute;
            width: 100%;
            height: 200%;
            background-color: #ffffff;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
            font-family: 'Pacifico', cursive;
            font-size: 18px;
            color: #ff007f;
            line-height: 1.5;
            transform: translateY(100%);
            transition: transform 1s ease-in-out;
        }
        .card-container.opened .paper {
            transform: translateY(0);
        }
        .heart {
            position: absolute;
            top: -30px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 50px;
            color: #ffd700;
            animation: bounce 2s infinite;
            text-shadow: 0 0 10px #ff007f;
        }
        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-20px); }
        }
        .banner {
            margin-top: 20px;
            font-family: 'Raleway', sans-serif;
            color: #ffffff;
            text-align: center;
            font-size: 24px;
            text-shadow: 2px 2px 10px #ff007f;
        }
    </style>
</head>
<body>
    <div class="intro">Esto es para la niña más hermosa del mundo 💖</div>
    <div class="card-container" onclick="this.classList.toggle('opened')">
        <div class="heart">💖</div>
        <div class="paper">
            <h2>Te Amo Muchísimo</h2>
            <p>Gracias por llegar a mi vida, eres lo más valioso que tengo y siempre te voy a amar en las buenas y en las malas. Sé que juntos vamos a salir adelante. ¡Te amo muchísimo, mi mami! 💕</p>
            <p>Tu siempre, Anth'Zz</p>
        </div>
    </div>
    <div class="banner">⚡ BerMatModZ ⚡</div>
</body>
</html>
