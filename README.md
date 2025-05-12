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
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 80px auto 20px auto;
        }
        .card {
            background-color: #fff;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            margin: 20px 0;
            padding: 20px;
            border-radius: 12px;
            border-left: 5px solid #FFCC00;
        }
        .card-header {
            background-color: #FFCC00;
            color: #000;
            padding: 15px;
            border-radius: 8px;
            font-size: 1.5em;
            text-align: center;
            font-family: 'Anton', sans-serif;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
        }
        .info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            font-weight: bold;
        }
        .data-bar {
            width: 100%;
            height: 30px;
            background-color: #ddd;
            border-radius: 15px;
            margin: 10px 0;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
        }
        .data-bar-inner {
            height: 100%;
            background-color: #FFCC00;
            width: 75%;
            border-radius: 15px 0 0 15px;
            transition: width 0.5s ease;
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
            <li><a href="#">Perfil</a></li>
            <li><a href="#">Consumo de Datos</a></li>
            <li><a href="#">Activar Chip</a></li>
            <li><a href="#">Internet Gratis</a></li>
        </ul>
    </div>
    <div class="header">Bitel - BerMatModZ</div>
    <div class="container">
        <div class="card">
            <div class="card-header">Información Personal</div>
            <div class="info">
                <div>Nombre: Anth'Zz Berrocal</div>
                <div>Alias: BerMatModZ</div>
            </div>
            <div class="info">
                <div>Red: Bitel</div>
                <div>Proyecto: Internet Gratis</div>
            </div>
        </div>
        <div class="card">
            <div class="card-header">Consumo de Datos</div>
            <div class="data-bar">
                <div class="data-bar-inner" id="data-bar"></div>
            </div>
            <div style="text-align: center;">
                <strong id="total-usage">0 GB usados de 400 GB</strong>
            </div>
        </div>
    </div>
    <script>
        let used = 0;
        let total = 400;
        function updateUsage() {
            if (used < 300) {
                used += 1;
                let percent = (used / total) * 100;
                document.getElementById('data-bar').style.width = percent + '%';
                document.getElementById('total-usage').innerText = used + ' GB usados de 400 GB';
            }
        }
        setInterval(updateUsage, 200);
        function toggleMenu() {
            document.getElementById('menu').classList.toggle('active');
        }
    </script>
</body>
</html>
