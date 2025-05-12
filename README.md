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
        }
        .header {
            background-color: #FFCC00;
            color: #000;
            padding: 20px;
            text-align: center;
            font-family: 'Anton', sans-serif;
            font-size: 2em;
            letter-spacing: 2px;
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 20px auto;
        }
        .card {
            background-color: #fff;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            margin: 20px 0;
            padding: 20px;
            border-radius: 12px;
        }
        .card-header {
            background-color: #FFCC00;
            color: #000;
            padding: 15px;
            border-radius: 8px;
            font-size: 1.5em;
            text-align: center;
            font-family: 'Anton', sans-serif;
        }
        .info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            font-weight: bold;
        }
        .data-usage {
            font-size: 1.2em;
            margin-top: 20px;
            display: flex;
            justify-content: space-between;
        }
        .data-bar {
            width: 100%;
            height: 30px;
            background-color: #ddd;
            border-radius: 15px;
            margin: 10px 0;
            overflow: hidden;
        }
        .data-bar-inner {
            height: 100%;
            background-color: #FFCC00;
            width: 75%;
            border-radius: 15px 0 0 15px;
            transition: width 0.5s ease;
        }
        .button {
            background-color: #FFCC00;
            color: #000;
            padding: 15px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            font-weight: bold;
            width: 100%;
            margin-top: 20px;
            transition: background-color 0.3s, transform 0.2s;
            font-family: 'Anton', sans-serif;
        }
        .button:hover {
            background-color: #e6b800;
            transform: scale(1.05);
        }
    </style>
</head>
<body>
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
            <div class="data-usage">
                <div id="used-data">Usados: 0 GB</div>
                <div id="available-data">Disponibles: 400 GB</div>
            </div>
            <div class="data-bar">
                <div class="data-bar-inner" id="data-bar"></div>
            </div>
            <div style="text-align: center;">
                <strong id="total-usage">0 GB usados de 400 GB</strong>
            </div>
        </div>
        <div class="card">
            <div class="card-header">Activar Chip Prepago</div>
            <button class="button">Activar Chip Entel</button>
        </div>
        <div class="card">
            <div class="card-header">Internet Gratis</div>
            <input type="text" placeholder="Ingresa tu código aquí" style="width: 100%; padding: 15px; border-radius: 8px; border: 1px solid #ccc; margin-bottom: 20px;">
            <button class="button">Activar Internet</button>
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
                document.getElementById('used-data').innerText = 'Usados: ' + used + ' GB';
                document.getElementById('available-data').innerText = 'Disponibles: ' + (total - used) + ' GB';
                document.getElementById('total-usage').innerText = used + ' GB usados de 400 GB';
            }
        }
        setInterval(updateUsage, 200);
    </script>
</body>
</html>
