<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Libro de Amor - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Raleway:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #fff0f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            font-family: 'Raleway', sans-serif;
            margin: 0;
        }
        .book {
            width: 600px;
            height: 400px;
            background-color: #fff;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
            border-radius: 15px;
            overflow: hidden;
            position: relative;
            perspective: 1500px;
        }
        .pages {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: row;
            transition: transform 1s ease-in-out;
            transform-origin: left center;
        }
        .page {
            width: 100%;
            padding: 40px;
            background-color: #ffe4e1;
            border-radius: 15px;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.1);
            font-family: 'Pacifico', cursive;
            color: #c2185b;
            line-height: 1.8;
            overflow-y: auto;
            text-align: center;
        }
        .button {
            background-color: #c2185b;
            color: #ffffff;
            padding: 10px 30px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            margin: 20px 10px;
            font-family: 'Raleway', sans-serif;
            font-weight: bold;
            transition: background-color 0.3s ease;
        }
        .button:hover {
            background-color: #b71c1c;
        }
        .controls {
            display: flex;
            justify-content: center;
        }
    </style>
</head>
<body>
    <div class="book">
        <div class="pages" id="pages">
            <div class="page">Eres lo más hermoso que ha llegado a mi vida. 💖</div>
            <div class="page">Gracias por ser mi razón para sonreír cada día. 😘</div>
            <div class="page">Te amo más de lo que las palabras pueden expresar. 💞</div>
            <div class="page">Siempre estaré a tu lado, en las buenas y en las malas. ❤️</div>
            <div class="page">Eres mi mundo, mi vida, mi todo. Te amo infinitamente. 🌹</div>
        </div>
    </div>
    <div class="controls">
        <button class="button" onclick="previousPage()">⬅️ Anterior</button>
        <button class="button" onclick="nextPage()">➡️ Siguiente</button>
    </div>
    <script>
        let currentPage = 0;
        const pages = document.getElementById('pages');
        function nextPage() {
            if (currentPage < pages.children.length - 1) {
                currentPage++;
                pages.style.transform = `translateX(-${currentPage * 100}%)`;
            }
        }
        function previousPage() {
            if (currentPage > 0) {
                currentPage--;
                pages.style.transform = `translateX(-${currentPage * 100}%)`;
            }
        }
    </script>
</body>
</html>
