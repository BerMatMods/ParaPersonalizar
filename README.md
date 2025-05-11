<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flores para Briyidth</title>
    <style>
        body {
            background-color: #111;
            color: #fff;
            font-family: Arial, sans-serif;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
        }
        .flower {
            position: relative;
            width: 60px;
            height: 60px;
            background-color: #f00;
            border-radius: 50%;
            animation: grow 3s ease-in-out forwards;
            margin-bottom: 100px;
            filter: drop-shadow(0 0 10px #f00);
        }
        .flower::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 80px;
            height: 80px;
            background-color: #f0f;
            border-radius: 50%;
            transform: translate(-50%, -50%);
            filter: blur(10px) brightness(1.5);
        }
        @keyframes grow {
            from { transform: scale(0) translateY(300px); }
            to { transform: scale(1) translateY(0); }
        }
        .message {
            margin-top: 20px;
            font-size: 24px;
            text-align: center;
            color: #ff6;
            filter: drop-shadow(0 0 10px #ff6);
            animation: fadeIn 4s ease-in-out 2s forwards;
            opacity: 0;
        }
        @keyframes fadeIn {
            to { opacity: 1; }
        }
        .heart {
            color: #f06;
            font-size: 32px;
            filter: drop-shadow(0 0 10px #f06);
            animation: pulse 2s infinite alternate;
        }
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.3); }
        }
    </style>
</head>
<body>
    <div class="flower"></div>
    <div class="message">
        <span class="heart">❤️</span> Te amo mucho mi amor, Briyidth <span class="heart">❤️</span><br>
        Eres lo más hermoso que tengo en la vida 🌹<br>
        Gracias por hacerme feliz cada día 💖<br>
        Siempre juntos, mi amor eterno 💕
    </div>
</body>
</html>
