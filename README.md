<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bitel - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&family=Anton&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }
        .header {
            background-color: #FFCC00;
            color: #000;
            padding: 20px;
            text-align: center;
            font-family: 'Anton', sans-serif;
            font-size: 2em;
            letter-spacing: 2px;
            position: relative;
            z-index: 10;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
        }
        .main-screen {
            background-image: url('https://i.imgur.com/UhCxskT.jpg');
            background-size: cover;
            background-position: center;
            color: #fff;
            padding: 50px 20px;
            text-align: center;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .main-screen h1 {
            font-family: 'Anton', sans-serif;
            font-size: 4em;
            letter-spacing: 2px;
            margin: 0;
            text-shadow: 2px 4px 10px rgba(0,0,0,0.8);
        }
        .main-screen p {
            font-size: 1.5em;
            margin-top: 20px;
            font-weight: bold;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.8);
        }
        .menu {
            position: fixed;
            top: 0;
            left: 0;
            width: 250px;
            height: 100%;
            background-color: #333;
            color: #fff;
            padding: 20px;
            transform: translateX(-260px);
            transition: transform 0.4s ease;
            box-shadow: 5px 0 15px rgba(0,0,0,0.3);
            z-index: 20;
        }
        .menu.active {
            transform: translateX(0);
        }
        .menu h2 {
            color: #FFCC00;
            margin-bottom: 20px;
            font-family: 'Anton', sans-serif;
        }
        .menu ul {
            list-style: none;
            padding: 0;
        }
        .menu ul li {
            margin-bottom: 15px;
        }
        .menu ul li a {
            color: #fff;
            text-decoration: none;
            font-size: 1.2em;
        }
        .menu ul li a:hover {
            color: #FFCC00;
        }
        .burger {
            position: absolute;
            top: 10px;
            left: 20px;
            width: 30px;
            cursor: pointer;
            z-index: 30;
        }
        .burger div {
            width: 30px;
            height: 4px;
            background-color: #000;
            margin: 5px 0;
            transition: 0.3s;
        }
    </style>
</head>
<body>
    <div class="burger" onclick="toggleMenu()">
        <div></div>
        <div></div>
        <div></div>
    </div>
    <div class="menu" id="menu">
        <h2>Menú</h2>
        <ul>
            <li><a href="#" onclick="showSection('profile')">Perfil</a></li>
            <li><a href="#" onclick="showSection('data')">Consumo de Datos</a></li>
            <li><a href="#" onclick="showSection('chip')">Activar Chip</a></li>
            <li><a href="#" onclick="showSection('internet')">Internet Gratis</a></li>
            <li><a href="#" onclick="showSection('info')">Info</a></li>
        </ul>
    </div>
    <div class="main-screen">
        <h1>BerMatModZ</h1>
        <p>Agente Principal de Bitel - Programador y Activador</p>
    </div>
    <script>
        function toggleMenu() {
            document.getElementById('menu').classList.toggle('active');
        }
        function showSection(id) {
            const sections = document.querySelectorAll('.info-section');
            sections.forEach(section => section.classList.remove('active'));
            document.getElementById(id).classList.add('active');
        }
    </script>
</body>
</html>
