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
        }
        .intro {
            font-size: 28px;
            margin-bottom: 20px;
            color: #c2185b;
            font-family: 'Pacifico', cursive;
            text-align: center;
        }
        .card-container {
            position: relative;
            width: 350px;
            height: 250px;
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
            overflow: hidden;
            transition: all 0.8s ease-in-out;
        }
        .card-container .cover {
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: #f8bbd0;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            transition: transform 0.8s ease-in-out;
        }
        .card-container.opened .cover {
            transform: translateY(-300px);
        }
        .card-container .paper {
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: #ffffff;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.1);
            opacity: 0;
            transform: translateY(100%);
            transition: all 0.8s ease-in-out;
            font-family: 'Pacifico', cursive;
            color: #c2185b;
            text-align: center;
            line-height: 1.6;
        }
        .card-container.opened .paper {
            opacity: 1;
            transform: translateY(0);
        }
        .button {
            background-color: #c2185b;
            color: #ffffff;
            padding: 10px 20px;
            border: none;
            border-radius: 20px;
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
    <div class="card-container" id="card">
        <div class="cover">
            💌 Para Mi Reina Briyidth 💖
        </div>
        <div class="paper">
            <h2>Te Amo Muchísimo</h2>
            <p>Gracias por llegar a mi vida, eres lo más valioso que tengo y siempre te voy a amar en las buenas y en las malas. Sé que juntos vamos a salir adelante. ¡Te amo muchísimo, mi mami! 💕</p>
            <p>Tu siempre, Anth'Zz</p>
        </div>
    </div>
    <button class="button" onclick="document.getElementById('card').classList.toggle('opened')">Abrir la Carta</button>
</body>
</html>
