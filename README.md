<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>La Magia del Barbero - Kennedy</title>
<style>
/* ------------------- RESET ------------------- */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
html {
    scroll-behavior: smooth;
}
body {
    font-family: 'Segoe UI', sans-serif;
    background-color: #0a0a0a;
    color: white;
    line-height: 1.6;
}

/* ------------------- COLORES ------------------- */
:root {
    --color-principal: #FFD700;
    --color-secundario: #111;
    --color-texto: #fff;
    --color-acento: #ffcc00;
}

/* ------------------- HEADER ------------------- */
header {
    position: fixed;
    width: 100%;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(5px);
    padding: 1rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 1000;
    border-bottom: 2px solid var(--color-principal);
}
header h1 {
    font-size: 1.5rem;
    color: var(--color-principal);
    text-shadow: 0 0 10px var(--color-principal);
}
nav a {
    color: var(--color-texto);
    margin-left: 20px;
    text-decoration: none;
    font-weight: bold;
    position: relative;
}
nav a::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: -5px;
    width: 0%;
    height: 2px;
    background: var(--color-principal);
    transition: 0.3s;
}
nav a:hover::after {
    width: 100%;
}

/* ------------------- HERO ------------------- */
.hero {
    height: 100vh;
    background: url('https://images.unsplash.com/photo-1598294200450-1a5e8b3c78c1?auto=format&fit=crop&w=1350&q=80') center/cover no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    position: relative;
}
.hero::after {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(0,0,0,0.6);
}
.hero-content {
    position: relative;
    z-index: 2;
    color: white;
    animation: fadeInUp 2s ease;
}
.hero-content h2 {
    font-size: 3rem;
    color: var(--color-principal);
    text-shadow: 0 0 15px var(--color-principal);
}
.hero-content p {
    font-size: 1.2rem;
    margin-top: 10px;
}
.hero-content a {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 25px;
    background: var(--color-principal);
    color: black;
    font-weight: bold;
    text-decoration: none;
    border-radius: 30px;
    box-shadow: 0 0 20px var(--color-principal);
    transition: 0.3s;
}
.hero-content a:hover {
    background: white;
    color: black;
    box-shadow: 0 0 25px white;
}

/* Animación */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(50px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ------------------- SECCIÓN SOBRE MÍ ------------------- */
section {
    padding: 5rem 2rem;
}
#about {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    align-items: center;
}
#about img {
    flex: 1 1 300px;
    border-radius: 20px;
    max-width: 400px;
    box-shadow: 0 0 15px var(--color-principal);
}
#about .text {
    flex: 1 1 300px;
}
#about h2 {
    font-size: 2rem;
    color: var(--color-principal);
    margin-bottom: 1rem;
}
#about p {
    font-size: 1rem;
}

/* ------------------- SERVICIOS ------------------- */
#services {
    background: var(--color-secundario);
    text-align: center;
}
#services h2 {
    font-size: 2rem;
    margin-bottom: 2rem;
    color: var(--color-principal);
}
.services-container {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(250px,1fr));
    gap: 2rem;
}
.service {
    background: #1a1a1a;
    padding: 1.5rem;
    border-radius: 15px;
    box-shadow: 0 0 10px #000;
    transition: transform 0.3s;
}
.service:hover {
    transform: translateY(-10px);
    box-shadow: 0 0 20px var(--color-principal);
}
.service img {
    width: 100%;
    border-radius: 10px;
    margin-bottom: 1rem;
}

/* ------------------- GALERÍA ------------------- */
#gallery h2 {
    text-align: center;
    color: var(--color-principal);
    margin-bottom: 2rem;
}
.gallery-container {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
    gap: 1rem;
}
.gallery-container img {
    width: 100%;
    border-radius: 10px;
    transition: transform 0.3s, box-shadow 0.3s;
}
.gallery-container img:hover {
    transform: scale(1.05);
    box-shadow: 0 0 15px var(--color-principal);
}

/* ------------------- TESTIMONIOS ------------------- */
#testimonials {
    background: var(--color-secundario);
    text-align: center;
}
#testimonials h2 {
    color: var(--color-principal);
    margin-bottom: 2rem;
}
.testimonial {
    max-width: 600px;
    margin: auto;
    font-style: italic;
    margin-bottom: 1.5rem;
}

/* ------------------- MAPA ------------------- */
#map {
    text-align: center;
}
#map iframe {
    width: 100%;
    height: 400px;
    border: none;
    border-radius: 15px;
}

/* ------------------- FOOTER ------------------- */
footer {
    background: #000;
    text-align: center;
    padding: 2rem 1rem;
    color: white;
    border-top: 2px solid var(--color-principal);
}
footer a {
    color: var(--color-principal);
    text-decoration: none;
}
footer .creditos {
    margin-top: 1rem;
    background: var(--color-secundario);
    display: inline-block;
    padding: 10px 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px var(--color-principal);
}

/* ------------------- RESPONSIVE ------------------- */
@media (max-width: 768px) {
    #about {
        flex-direction: column;
    }
}
</style>
</head>
<body>

<!-- HEADER -->
<header>
    <h1>La Magia del Barbero</h1>
    <nav>
        <a href="#about">Sobre mí</a>
        <a href="#services">Servicios</a>
        <a href="#gallery">Galería</a>
        <a href="#testimonials">Testimonios</a>
        <a href="#map">Ubicación</a>
    </nav>
</header>

<!-- HERO -->
<section class="hero">
    <div class="hero-content">
        <h2>Bienvenido a La Magia del Barbero</h2>
        <p>Donde Kennedy transforma tu estilo</p>
        <a href="#services">Ver servicios</a>
    </div>
</section>

<!-- SOBRE MÍ -->
<section id="about">
    <img src="https://images.unsplash.com/photo-1598550880863-9e75e2645a80?auto=format&fit=crop&w=800&q=80" alt="Kennedy el barbero">
    <div class="text">
        <h2>Sobre mí</h2>
        <p>Hola, soy Kennedy, barbero profesional con más de 10 años de experiencia en cortes y estilos para hombres, mujeres, niños y niñas. En "La Magia del Barbero" me apasiona brindar un servicio personalizado, asegurando que cada cliente se sienta seguro y satisfecho con su nuevo look.</p>
    </div>
</section>

<!-- SERVICIOS -->
<section id="services">
    <h2>Servicios</h2>
    <div class="services-container">
        <div class="service">
            <img src="https://images.unsplash.com/photo-1598281351390-0b14a7dbb33a?auto=format&fit=crop&w=800&q=80" alt="Corte masculino">
            <h3>Corte Masculino</h3>
            <p>Estilos clásicos y modernos para resaltar tu personalidad.</p>
        </div>
        <div class="service">
            <img src="https://images.unsplash.com/photo-1621605811364-3ef674e7dc86?auto=format&fit=crop&w=800&q=80" alt="Corte femenino">
            <h3>Corte Femenino</h3>
            <p>Cortes y peinados para cada ocasión, resaltando tu belleza.</p>
        </div>
        <div class="service">
            <img src="https://images.unsplash.com/photo-1601084881623-cdfb1eec60f5?auto=format&fit=crop&w=800&q=80" alt="Corte para niños">
            <h3>Corte Infantil</h3>
            <p>Cómodo y divertido para los más pequeños.</p>
        </div>
        <div class="service">
            <img src="https://images.unsplash.com/photo-1612322327993-fb1ba627d7d1?auto=format&fit=crop&w=800&q=80" alt="Afeitado y barba">
            <h3>Afeitado y Barba</h3>
            <p>Arreglo de barba y afeitado tradicional con toalla caliente.</p>
        </div>
    </div>
</section>

<!-- GALERÍA -->
<section id="gallery">
    <h2>Galería</h2>
    <div class="gallery-container">
        <img src="https://images.unsplash.com/photo-1598294200450-1a5e8b3c78c1?auto=format&fit=crop&w=800&q=80" alt="Corte 1">
        <img src="https://images.unsplash.com/photo-1571171637578-41bc2dd41cd2?auto=format&fit=crop&w=800&q=80" alt="Corte 2">
        <img src="https://images.unsplash.com/photo-1622295022195-2fc90d92c1e1?auto=format&fit=crop&w=800&q=80" alt="Corte 3">
        <img src="https://images.unsplash.com/photo-1606335543042-17e74af9c4b2?auto=format&fit=crop&w=800&q=80" alt="Corte 4">
    </div>
</section>

<!-- TESTIMONIOS -->
<section id="testimonials">
    <h2>Testimonios</h2>
    <div class="testimonial">"Kennedy es un maestro del estilo. Siempre salgo con una sonrisa." – Carlos M.</div>
    <div class="testimonial">"La mejor barbería de la ciudad, ambiente agradable y servicio impecable." – Laura G.</div>
    <div class="testimonial">"Mi hijo siempre sale feliz con su corte nuevo." – Andrés P.</div>
</section>

<!-- MAPA -->
<section id="map">
    <h2>Ubicación</h2>
    <iframe src="https://maps.google.com/maps?q=5um9wS8RcRro1foS7&output=embed"></iframe>
</section>

<!-- FOOTER -->
<footer>
    <p>© 2025 La Magia del Barbero - Todos los derechos reservados</p>
    <div class="creditos">
        Diseñado por <strong>AnthZz Berrocal</strong> | 
        <a href="https://github.com/BerMatMods" target="_blank">Mi GitHub</a>
    </div>
</footer>

</body>
</html>
