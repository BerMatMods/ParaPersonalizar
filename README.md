<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bitel - Mi Cuenta</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
        }

        .header {
            background-color: #FFCC00; /* Color de Bitel */
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 2em;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 20px auto;
        }

        .card {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin: 20px 0;
            padding: 20px;
            border-radius: 8px;
        }

        .card-header {
            background-color: #FFCC00;
            color: white;
            padding: 10px;
            border-radius: 8px;
            font-size: 1.5em;
            text-align: center;
        }

        .card-body {
            margin-top: 20px;
        }

        .info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .info div {
            width: 45%;
        }

        .data-usage {
            font-size: 1.3em;
            margin-top: 20px;
            display: flex;
            justify-content: space-between;
        }

        .data-bar {
            width: 80%;
            height: 20px;
            background-color: #ddd;
            border-radius: 10px;
            margin: 10px 0;
            position: relative;
        }

        .data-bar-inner {
            height: 100%;
            background-color: #FFCC00;
            border-radius: 10px;
            width: 75%; /* Simulando uso de 300GB de 400GB */
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            color: #999;
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
            width: 100%;
        }

        .button:hover {
            background-color: #e6b800;
        }

        .profile-img {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin: 0 auto;
            display: block;
            background-image: url('https://via.placeholder.com/80');
            background-size: cover;
            background-position: center;
        }
    </style>
</head>
<body>

    <div class="header">
        <h1>Mi Cuenta Bitel</h1>
    </div>

    <div class="container">
        <!-- Información personal -->
        <div class="card">
            <div class="card-header">Información Personal</div>
            <div class="card-body">
                <div class="info">
                    <div><strong>Nombre:</strong> Anth'Zz Berrocal</div>
                    <div><strong>Alias:</strong> BerMatModZ</div>
                </div>
                <div class="info">
                    <div><strong>Red:</strong> Bitel</div>
                    <div><strong>Proyecto:</strong> Internet Gratis</div>
                </div>
            </div>
        </div>

        <!-- Imagen de perfil -->
        <div class="card">
            <div class="card-header">Mi Perfil</div>
            <div class="card-body">
                <div class="profile-img"></div>
                <div style="text-align: center; margin-top: 10px;">
                    <strong>¡Hola, Anth'Zz!</strong>
                </div>
            </div>
        </div>

        <!-- Consumo de datos -->
        <div class="card">
            <div class="card-header">Consumo de Datos</div>
            <div class="card-body">
                <div class="data-usage">
                    <div>Usados: 300 GB</div>
                    <div>Disponibles: 100 GB</div>
                </div>
                <div class="data-bar">
                    <div class="data-bar-inner"></div>
                </div>
                <div style="text-align: center;">
                    <strong>300 GB usados de 400 GB</strong>
                </div>
            </div>
        </div>

        <!-- Activar Chip prepago -->
        <div class="card">
            <div class="card-header">Activar Chip Prepago</div>
            <div class="card-body">
                <button class="button">Activar Chip Entel</button>
            </div>
        </div>

        <!-- Activar Internet Gratis -->
        <div class="card">
            <div class="card-header">Internet Gratis</div>
            <div class="card-body">
                <p>Ingresa tu código BerMatModZ para activar internet gratis.</p>
                <input type="text" placeholder="Código aquí" style="width: 100%; padding: 10px; border-radius: 8px; border: 1px solid #ccc;">
                <button class="button">Activar Internet</button>
            </div>
        </div>
    </div>

    <div class="footer">
        <p>Bitel - Proyecto BerMatModZ | Todos los derechos reservados.</p>
    </div>

</body>
</html>
