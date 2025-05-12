<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta para Briyidth - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Raleway:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #fdf6e3;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            font-family: 'Raleway', sans-serif;
            margin: 0;
            overflow: hidden;
        }
        .intro {
            font-size: 30px;
            margin-bottom: 20px;
            color: #c2185b;
            font-family: 'Pacifico', cursive;
            text-align: center;
            animation: fadeIn 1.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .envelope {
            position: relative;
            width: 320px;
            height: 250px;
            background-color: #ffffff;
            border-radius: 8px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.15);
            overflow: hidden;
            cursor: pointer;
        }
        .envelope .flap {
            position: absolute;
            top: -160px;
            left: 0;
            width: 100%;
            height: 160px;
            background-color: #c2185b;
            border-radius: 0 0 320px 320px;
            transform-origin: bottom center;
            transition: transform 0.6s ease-in-out;
            z-index: 2;
        }
        .envelope.opened .flap {
            transform: rotateX(-180deg);
        }
        .message {
            padding: 30px 20px;
            font-family: 'Pacifico', cursive;
            color: #c2185b;
            opacity: 0;
            transform: translateY(200px);
            transition: opacity 0.8s ease-in-out 0.4s, transform 0.8s ease-in-out 0.4s;
            z-index: 1;
        }
        .envelope.opened .message {
            opacity: 1;
            transform: translateY(0);
        }
        .button {
            background-color: #c2185b;
            color: #ffffff;
            padding: 10px 30px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            margin-top: 20px;
            font-family: 'Raleway', sans-serif;
            font-weight: bold;
            transition: background-color 0.3s ease;
        }
        .button:hover {
            background-color: #b71c1c;
        }
    </style>
</head>
<body>
    <div class="intro">Esto es para la niña más hermosa del mundo 💖</div>
    <div class="envelope" id="envelope" onclick="this.classList.toggle('opened')">
        <div class="flap"></div>
        <div class="message">
            <h2>Te Amo Muchísimo</h2>
            <p>Gracias por llegar a mi vida, eres lo más valioso que tengo y siempre te voy a amar en las buenas y en las malas. Sé que juntos vamos a salir adelante. ¡Te amo muchísimo, mi mami! 💕</p>
            <p>Tu siempre, Anth'Zz</p>
        </div>
    </div>
    <button class="button" onclick="document.getElementById('envelope').classList.toggle('opened')">Abrir la Carta</button>
</body>
</html>
