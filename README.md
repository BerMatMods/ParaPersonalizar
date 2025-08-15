
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>La Magia del Barbero | Barber Shop</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --negro: #0d0d0d;
      --dorado: #d4af37;
      --plateado: #c0c0c0;
      --blanco: #fff;
    }
    * {margin: 0; padding: 0; box-sizing: border-box;}
    body {
      font-family: 'Roboto', sans-serif;
      background-color: var(--negro);
      color: var(--blanco);
      overflow-x: hidden;
    }
    header {
      background: linear-gradient(135deg, var(--negro), var(--dorado));
      text-align: center;
      padding: 40px 20px;
      animation: fadeDown 1.5s ease-in-out;
    }
    header h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3.5rem;
      letter-spacing: 2px;
    }
    header p {
      font-size: 1.2rem;
    }
    nav {
      display: flex;
      justify-content: center;
      background: rgba(255,255,255,0.05);
      backdrop-filter: blur(6px);
    }
    nav a {
      color: var(--blanco);
      padding: 15px 20px;
      text-decoration: none;
      font-weight: bold;
      position: relative;
    }
    nav a::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0;
      width: 0; height: 2px;
      background: var(--dorado);
      transition: width 0.3s;
    }
    nav a:hover::after { width: 100%; }

    section {
      padding: 50px 20px;
      max-width: 1200px;
      margin: auto;
    }
    h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.5rem;
      color: var(--dorado);
      text-align: center;
      margin-bottom: 40px;
    }

    /* Tarjetas 3D */
    .cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
    }
    .card {
      background: rgba(255,255,255,0.05);
      border-radius: 12px;
      overflow: hidden;
      perspective: 1000px;
      transform-style: preserve-3d;
      transition: transform 0.6s ease, box-shadow 0.6s ease;
    }
    .card:hover {
      transform: rotateY(8deg) rotateX(4deg) scale(1.02);
      box-shadow: 0 10px 30px rgba(212,175,55,0.5);
    }
    .card img {
      width: 100%;
      display: block;
      height: 200px;
      object-fit: cover;
    }
    .card h3 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.6rem;
      margin: 15px;
      color: var(--dorado);
    }
    .card p {
      margin: 0 15px 15px;
      font-size: 0.95rem;
      color: var(--plateado);
    }

    /* Galería */
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
    }
    .gallery img {
      width: 100%;
      border-radius: 8px;
      transition: transform 0.4s, box-shadow 0.4s;
    }
    .gallery img:hover {
      transform: scale(1.05);
      box-shadow: 0 0 15px var(--dorado);
    }

    /* Reseñas */
    .review {
      background: rgba(255,255,255,0.05);
      border-left: 4px solid var(--dorado);
      padding: 20px;
      margin-bottom: 15px;
      font-style: italic;
      color: var(--plateado);
    }

    /* Promo */
    .promo {
      background: linear-gradient(90deg, var(--dorado), var(--plateado));
      color: var(--negro);
      padding: 20px;
      text-align: center;
      font-weight: bold;
      border-radius: 8px;
      animation: pulse 2s infinite;
    }

    /* Contacto */
    .btn-whatsapp {
      background: #25d366;
      color: var(--blanco);
      padding: 12px 20px;
      border-radius: 50px;
      text-decoration: none;
      font-weight: bold;
      display: inline-block;
      margin: 5px;
      box-shadow: 0 0 10px #25d366;
      transition: transform 0.3s;
    }
    .btn-whatsapp:hover {
      transform: scale(1.05);
    }

    footer {
      background: var(--negro);
      color: var(--plateado);
      text-align: center;
      padding: 15px;
      font-size: 0.9rem;
      border-top: 1px solid rgba(255,255,255,0.1);
    }

    /* Animaciones */
    @keyframes fadeDown { from {opacity:0; transform: translateY(-20px);} to {opacity:1; transform: translateY(0);} }
    @keyframes pulse { 0%, 100% {box-shadow: 0 0 10px var(--dorado);} 50% {box-shadow: 0 0 20px var(--dorado);} }

    /* Responsive */
    @media(max-width: 768px) {
      header h1 { font-size: 2.5rem; }
      .card img { height: 180px; }
    }
  </style>
</head>
<body>

  <header>
    <h1>La Magia del Barbero</h1>
    <p>Barber Shop | Estilo Moderno y Clásico</p>
  </header>

  <nav>
    <a href="#servicios">Servicios</a>
    <a href="#galeria">Galería</a>
    <a href="#equipo">Equipo</a>
    <a href="#reseñas">Reseñas</a>
    <a href="#contacto">Contacto</a>
  </nav>

  <section id="servicios">
    <h2>Servicios</h2>
    <div class="cards">
      <div class="card">
        <img src="https://images.unsplash.com/photo-1582095133179-298c8729f480" alt="Corte moderno">
        <h3>Corte Moderno</h3>
        <p>Estilos actualizados para lucir siempre a la moda.</p>
      </div>
      <div class="card">
        <img src="https://images.unsplash.com/photo-1599351430501-00c34fd10928" alt="Corte clásico">
        <h3>Corte Clásico</h3>
        <p>El estilo atemporal que nunca pasa de moda.</p>
      </div>
      <div class="card">
        <img src="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f" alt="Arreglo barba">
        <h3>Arreglo de Barba</h3>
        <p>Perfilado perfecto y cuidado premium para tu barba.</p>
      </div>
    </div>
  </section>

  <section id="galeria">
    <h2>Galería</h2>
    <div class="gallery">
      <img src="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f" alt="Trabajo 1">
      <img src="https://images.unsplash.com/photo-1599351430501-00c34fd10928" alt="Trabajo 2">
      <img src="https://images.unsplash.com/photo-1582095133179-298c8729f480" alt="Trabajo 3">
      <img src="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f" alt="Trabajo 4">
    </div>
  </section>

  <section id="equipo">
    <h2>Nuestro Equipo</h2>
    <div class="cards">
      <div class="card">
        <img src="https://images.unsplash.com/photo-1582095133179-298c8729f480" alt="Barbero 1">
        <h3>Juan</h3>
        <p>Especialista en cortes modernos y fades.</p>
      </div>
      <div class="card">
        <img src="https://images.unsplash.com/photo-1599351430501-00c34fd10928" alt="Barbero 2">
        <h3>Carlos</h3>
        <p>Experto en cortes clásicos y barba tradicional.</p>
      </div>
    </div>
  </section>

  <section id="reseñas">
    <h2>Reseñas de Clientes</h2>
    <div class="review">"Excelente servicio, muy profesionales." - Pedro</div>
    <div class="review">"Mi corte favorito, siempre salgo feliz." - Luis</div>
    <div class="review">"Atención de primera, 100% recomendados." - Jorge</div>
  </section>

  <section id="promocion">
    <div class="promo">
      💈 Acumula 4 cortes y el 5º es GRATIS 💈
    </div>
  </section>

  <section id="contacto">
    <h2>Contáctanos</h2>
    <p><strong>Teléfonos:</strong> 977 355 999 | 931 538 059</p>
    <p><strong>Dirección:</strong> Jirón Alfonso Ugarte, 3er piso</p>
    <a class="btn-whatsapp" href="https://wa.me/51977355999?text=Hola%20quiero%20reservar%20un%20corte">WhatsApp 977 355 999</a>
    <a class="btn-whatsapp" href="https://wa.me/51931538059?text=Hola%20quiero%20reservar%20un%20corte">WhatsApp 931 538 059</a>
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!..." width="100%" height="250" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
  </section>

  <footer>
    &copy; 2025 La Magia del Barbero | Diseñado por Anth'Zz Berrocal — BerMatModZ
  </footer>

</body>
</html>
