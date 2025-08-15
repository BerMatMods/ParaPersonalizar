<!DOCTYPE html>
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
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background-color: var(--negro);
      color: var(--blanco);
      line-height: 1.6;
      overflow-x: hidden;
    }
    header {
      background: linear-gradient(135deg, var(--negro) 0%, var(--dorado) 100%);
      color: var(--blanco);
      padding: 30px 20px;
      text-align: center;
      position: relative;
      animation: fadeDown 1.5s ease-in-out;
    }
    header h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3.5rem;
      letter-spacing: 2px;
    }
    header p {
      font-size: 1.2rem;
      font-weight: 300;
    }
    nav {
      background-color: rgba(255, 255, 255, 0.05);
      display: flex;
      justify-content: center;
      backdrop-filter: blur(5px);
    }
    nav a {
      color: var(--blanco);
      text-decoration: none;
      padding: 15px 20px;
      display: block;
      font-weight: bold;
      letter-spacing: 1px;
      position: relative;
      transition: color 0.3s;
    }
    nav a::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 0%;
      height: 2px;
      background-color: var(--dorado);
      transition: width 0.3s;
    }
    nav a:hover::after {
      width: 100%;
    }
    nav a:hover {
      color: var(--dorado);
    }
    .hero {
      text-align: center;
      padding: 60px 20px;
      background: radial-gradient(circle at center, #222, #000);
      animation: fadeUp 1.5s ease-in-out;
    }
    .hero h2 {
      font-size: 3rem;
      font-family: 'Bebas Neue', sans-serif;
      margin-bottom: 15px;
      color: var(--dorado);
    }
    .section {
      padding: 50px 20px;
      max-width: 1100px;
      margin: auto;
    }
    .section h2 {
      text-align: center;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.5rem;
      color: var(--dorado);
      margin-bottom: 30px;
      animation: fadeUp 1s ease-in-out;
    }
    .services {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 25px;
    }
    .service {
      background: rgba(255,255,255,0.05);
      border-radius: 12px;
      padding: 20px;
      text-align: center;
      transition: transform 0.4s, box-shadow 0.4s;
      animation: fadeUp 1.2s ease-in-out;
    }
    .service:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px var(--dorado);
    }
    .service img {
      width: 100%;
      border-radius: 10px;
      height: 220px;
      object-fit: cover;
      margin-bottom: 15px;
      transition: filter 0.4s;
    }
    .service:hover img {
      filter: brightness(1.2);
    }
    .promo {
      background: linear-gradient(90deg, var(--dorado), var(--plateado));
      color: var(--negro);
      padding: 20px;
      text-align: center;
      font-size: 1.4rem;
      font-weight: bold;
      border-radius: 10px;
      animation: pulse 2s infinite;
    }
    footer {
      background: var(--negro);
      color: var(--plateado);
      text-align: center;
      padding: 15px;
      font-size: 0.9rem;
      border-top: 1px solid rgba(255,255,255,0.1);
    }
    .btn-whatsapp {
      background: #25d366;
      color: var(--blanco);
      padding: 15px 25px;
      display: inline-block;
      margin: 15px 5px;
      text-decoration: none;
      border-radius: 50px;
      font-weight: bold;
      box-shadow: 0 0 10px #25d366;
      transition: transform 0.3s;
    }
    .btn-whatsapp:hover {
      transform: scale(1.05);
    }

    /* Animaciones */
    @keyframes fadeUp {
      from {opacity: 0; transform: translateY(30px);}
      to {opacity: 1; transform: translateY(0);}
    }
    @keyframes fadeDown {
      from {opacity: 0; transform: translateY(-30px);}
      to {opacity: 1; transform: translateY(0);}
    }
    @keyframes pulse {
      0%, 100% {box-shadow: 0 0 10px var(--dorado);}
      50% {box-shadow: 0 0 20px var(--dorado);}
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
    <a href="#promocion">Promoción</a>
    <a href="#contacto">Contacto</a>
  </nav>

  <section class="hero">
    <h2>Transforma tu look</h2>
    <p>Los mejores cortes y estilos con un toque de magia</p>
  </section>

  <section id="servicios" class="section">
    <h2>Servicios</h2>
    <div class="services">
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Corte+Moderno" alt="Corte moderno">
        <h3>Corte Moderno</h3>
      </div>
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Corte+Clasico" alt="Corte clásico">
        <h3>Corte Clásico</h3>
      </div>
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Barba" alt="Arreglo de barba">
        <h3>Arreglo de Barba</h3>
      </div>
    </div>
  </section>

  <section id="promocion" class="section">
    <div class="promo">
      💈 ¡Acumula 4 cortes y el 5º es GRATIS! 💈
    </div>
  </section>

  <section id="contacto" class="section">
    <h2>Contáctanos</h2>
    <p><strong>Teléfonos:</strong> 977 355 999 | 931 538 059</p>
    <p><strong>Dirección:</strong> Jirón Alfonso Ugarte, 3er piso</p>
    <a class="btn-whatsapp" href="https://wa.me/51977355999?text=Hola%20quiero%20reservar%20un%20corte">WhatsApp 977 355 999</a>
    <a class="btn-whatsapp" href="https://wa.me/51931538059?text=Hola%20quiero%20reservar%20un%20corte">WhatsApp 931 538 059</a>
  </section>

  <footer>
    &copy; 2025 La Magia del Barbero | Diseñado por Anth'Zz Berrocal — BerMatModZ
  </footer>

</body>
</html>
