<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Libro de Amor - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Raleway:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #fff0f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: 'Raleway', sans-serif;
            margin: 0;
        }
        .book {
            width: 400px;
            height: 600px;
            perspective: 1500px;
            background-color: #fff;
            display: flex;
            flex-direction: column;
        }
        .pages {
            display: flex;
            flex-direction: row;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 1s ease-in-out;
        }
        .page {
            width: 100%;
            height: 100%;
            background-color: #ffe4e1;
            border: 2px solid #c2185b;
            border-radius: 10px;
            padding: 40px;
            font-family: 'Pacifico', cursive;
            color: #c2185b;
            line-height: 1.8;
            text-align: center;
            position: absolute;
            transform-origin: left center;
            transform: rotateY(0deg);
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.1);
            opacity: 0;
            visibility: hidden;
        }
        .page.show {
            opacity: 1;
            visibility: visible;
            transform: rotateY(0deg);
        }
        .page.previous {
            transform: rotateY(-180deg);
            opacity: 0;
        }
        .button {
            background-color: #c2185b;
            color: white;
            padding: 10px 30px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: bold;
            transition: background-color 0.3s ease;
            margin-top: 20px;
        }
        .button:hover {
            background-color: #b71c1c;
        }
    </style>
</head>
<body>
    <div class="book" id="book">
        <div class="pages" id="pages">
            <div class="page">Eres lo más hermoso que ha llegado a mi vida. 💖</div>
            <div class="page">Gracias por ser mi razón para sonreír cada día. 😘</div>
            <div class="page">Te amo más de lo que las palabras pueden expresar. 💞</div>
            <div class="page">Siempre estaré a tu lado, en las buenas y en las malas. ❤️</div>
            <div class="page">Eres mi mundo, mi vida, mi todo. Te amo infinitamente. 🌹</div>
        </div>
    </div>
    <button class="button" onclick="nextPage()">Siguiente Página</button>
    <button class="button" onclick="previousPage()">Página Anterior</button>

    <script>
        let currentPage = 0;
        const pages = document.querySelectorAll('.page');
        pages[currentPage].classList.add('show');

        function nextPage() {
            if (currentPage < pages.length - 1) {
                pages[currentPage].classList.remove('show');
                currentPage++;
                pages[currentPage].classList.add('show');
            }
        }

        function previousPage() {
            if (currentPage > 0) {
                pages[currentPage].classList.remove('show');
                currentPage--;
                pages[currentPage].classList.add('show');
            }
        }
    </script>
</body>
</html>
