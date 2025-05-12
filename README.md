<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interfaz Bitel - BerMatModZ</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        .header {
            background-color: #FFCC00; /* Color de Bitel */
            color: white;
            padding: 20px;
            text-align: center;
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 20px auto;
        }
        .card {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin: 10px 0;
            padding: 20px;
            border-radius: 8px;
        }
        .card-header {
            background-color: #FFCC00;
            color: white;
            padding: 10px;
            border-radius: 8px;
            font-size: 1.2em;
        }
        .content {
            margin-top: 20px;
        }
        .info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        .info div {
            width: 45%;
        }
        .button {
            background-color: #FFCC00;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            margin-top: 20px;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #e6b800;
        }
        .footer {
            text-align: center;
            margin-top: 40px;
            color: #999;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>Bienvenido a Bitel - BerMatModZ</h1>
    </div>

    <div class="container">
        <div class="card">
            <div class="card-header">
                Mi Información
            </div>
            <div class="content">
                <div class="info">
                    <div><strong>Nombre:</strong> Anth'Zz Berrocal</div>
                    <div><strong>Alias:</strong> BerMatModZ</div>
                </div>
                <div class="info">
                    <div><strong>Red de Datos:</strong> Bitel</div>
                    <div><strong>Proyecto:</strong> Internet Gratis con Código</div>
                </div>
            </div>
        </div>

        <div class="card">
            <div class="card-header">
                Activar Chip Prepago Entel
            </div>
            <div class="content">
                <p>Aquí puedes activar un chip de prepago de Entel. Introduce los detalles y confirma.</p>
                <button class="button">Activar Chip</button>
            </div>
        </div>

        <div class="card">
            <div class="card-header">
                Dar Internet Gratis
            </div>
            <div class="content">
                <p>Introduce tu código de BerMatModZ para activar internet gratis en tu cuenta.</p>
                <input type="text" placeholder="Ingresa tu código aquí" style="width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #ccc;">
                <button class="button">Activar Internet Gratis</button>
            </div>
        </div>
    </div>

    <div class="footer">
        <p>Bitel - Proyecto BerMatModZ | Todos los derechos reservados.</p>
    </div>

</body>
</html>
