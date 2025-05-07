<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>⚡ BerMatModZ Social 🔥</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f0f2f5;
            margin: 0;
            color: #333;
            transition: background-color 0.3s ease;
        }

        /* Navbar */
        .navbar {
            background-color: #4267B2;
            color: #fff;
            padding: 15px 30px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: background-color 0.3s ease;
        }

        .navbar h1 {
            margin: 0;
            font-size: 30px;
            font-weight: bold;
            color: #fff;
            transition: font-size 0.3s ease;
        }

        .navbar input {
            padding: 8px;
            border-radius: 25px;
            border: none;
            width: 300px;
            font-size: 14px;
        }

        .navbar input:focus {
            border: 2px solid #365899;
            outline: none;
        }

        /* Sidebar */
        .sidebar {
            width: 350px;
            background-color: #fff;
            padding: 20px;
            box-shadow: 0 0 25px rgba(0, 0, 0, 0.1);
            height: 100vh;
            position: fixed;
            top: 60px;
            overflow-y: auto;
            z-index: 900;
            transition: all 0.3s ease;
        }

        .sidebar h2 {
            color: #4267B2;
            font-size: 28px;
            margin-bottom: 20px;
        }

        .sidebar ul {
            list-style: none;
            padding: 0;
        }

        .sidebar li {
            margin: 15px 0;
            font-weight: bold;
            font-size: 18px;
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .sidebar li:hover {
            color: #365899;
        }

        .sidebar .social-icons {
            display: flex;
            gap: 15px;
            margin-top: 30px;
        }

        .sidebar .social-icons a {
            width: 55px;
            height: 55px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #4267B2;
            color: #fff;
            border-radius: 50%;
            text-decoration: none;
            font-size: 20px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .sidebar .social-icons a:hover {
            transform: scale(1.2);
        }

        /* Feed */
        .feed {
            margin-left: 370px;
            padding: 100px 30px 30px;
            max-width: 900px;
        }

        .post {
            background-color: #fff;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }

        .post:hover {
            transform: translateY(-8px);
        }

        .post h3 {
            color: #4267B2;
            margin-bottom: 15px;
            font-size: 22px;
            font-weight: 600;
        }

        .post textarea {
            width: 100%;
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            font-size: 16px;
            resize: none;
        }

        .post button {
            background-color: #4267B2;
            border: none;
            padding: 15px 30px;
            border-radius: 30px;
            color: #fff;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .post button:hover {
            background-color: #365899;
        }

        /* Profile Card */
        .profile-card {
            background-color: #fff;
            border-radius: 12px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 0 25px rgba(0,0,0,0.1);
            text-align: center;
            transition: all 0.3s ease;
        }

        .profile-card img {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            margin-bottom: 20px;
            transition: transform 0.3s ease;
        }

        .profile-card img:hover {
            transform: scale(1.15);
        }

        .profile-card h2 {
            margin: 0;
            font-size: 28px;
            font-weight: bold;
            color: #333;
        }

        .profile-card p {
            color: #777;
            margin: 12px 0;
        }

        .profile-card .details {
            font-size: 18px;
            color: #555;
            margin-top: 25px;
        }

        .profile-card .details span {
            font-weight: bold;
        }

        .contact-info {
            font-size: 16px;
            margin-top: 30px;
            color: #4267B2;
        }

        .contact-info a {
            text-decoration: none;
            color: #4267B2;
            font-weight: bold;
        }

        /* Footer */
        .footer {
            background-color: #4267B2;
            color: #fff;
            padding: 20px 30px;
            text-align: center;
            position: fixed;
            bottom: 0;
            width: 100%;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
        }

        /* Animations */
        @keyframes fadeIn {
            0% { opacity: 0; transform: translateY(50px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .animate {
            animation: fadeIn 1s ease-out;
        }

        /* Additional content sections */
        .additional-content {
            background-color: #fff;
            padding: 30px;
            border-radius: 12px;
            margin-top: 30px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }

        .additional-content h3 {
            color: #4267B2;
            font-size: 26px;
            margin-bottom: 20px;
        }

        .additional-content p {
            font-size: 16px;
            color: #555;
        }

        .additional-content .links {
            display: flex;
            gap: 20px;
            margin-top: 30px;
        }

        .additional-content .links a {
            text-decoration: none;
            color: #4267B2;
            font-size: 18px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="navbar animate">
        <h1>⚡ BerMatModZ Social 🔥</h1>
        <input type="text" placeholder="Buscar en BerMatModZ">
    </div>
    <div class="sidebar animate">
        <h2>Menú</h2>
        <ul>
            <li>Perfil de Anth'Zz Berrocal</li>
            <li>Amigos</li>
            <li>Mensajes</li>
            <li>Notificaciones</li>
            <li>Proyectos (⚡BerMat-Bot MD🔥, BerMat_Mods, FAMA)</li>
            <li>Configuración</li>
        </ul>
        <div class="social-icons">
            <a href="https://www.facebook.com/anthzberrocal" target="_blank">F</a>
            <a href="https://www.instagram.com/anthzberrocal" target="_blank">I</a>
            <a href="https://www.github.com/anthzberrocal" target="_blank">G</a>
            <a href="https://www.tiktok.com/@anthzberrocal" target="_blank">T</a>
        </div>
    </div>
    <div class="feed">
        <div class="profile-card animate">
            <img src="https://via.placeholder.com/180" alt="Anth'Zz Berrocal">
            <h2>Anth'Zz Berrocal</h2>
            <p>Desarrollador, programador y creador de BerMatModZ</p>
            <div class="details">
                <p><span>Ubicación:</span> Andahuaylas, Perú</p>
                <p><span>Proyectos destacados:</span> ⚡ BerMat-Bot MD🔥, BerMat_Mods, FAMA</p>
                <p><span>Habilidades:</span> Python, Ciberseguridad, Desarrollo de Bots</p>
                <p><span>Pasión:</span> Tecnología y hacking ético</p>
            </div>
            <div class="contact-info">
                <p>Contáctame:</p>
                <p><a href="https://www.facebook.com/anthzberrocal" target="_blank">Facebook</a> | <a href="https://www.instagram.com/anthzberrocal" target="_blank
