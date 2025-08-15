<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>La Magia del Barbero | Barber Shop</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --rojo: #d62828;
      --azul: #003049;
      --blanco: #fff;
      --gris: #f8f9fa;
      --negro: #111;
    }
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Poppins', sans-serif;
      background-color: var(--gris);
      color: var(--negro);
      line-height: 1.6;
    }
    header {
      background: linear-gradient(90deg, var(--azul), var(--rojo));
      color: var(--blanco);
      padding: 20px;
      text-align: center;
    }
    header h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3rem;
    }
    nav {
      background-color: var(--negro);
      display: flex;
      justify-content: center;
    }
    nav a {
      color: var(--blanco);
      text-decoration: none;
      padding: 15px 20px;
      display: block;
      transition: background 0.3s;
    }
    nav a:hover {
      background: var(--rojo);
    }
    .hero {
      text-align: center;
      padding: 40px 20px;
      background: var(--azul);
      color: var(--blanco);
    }
    .hero h2 {
      font-size: 2.5rem;
      font-family: 'Bebas Neue', sans-serif;
      margin-bottom: 15px;
    }
    .section {
      padding: 40px 20px;
      max-width: 1100px;
      margin: auto;
    }
    .section h2 {
      text-align: center;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2rem;
      color: var(--azul);
      margin-bottom: 20px;
    }
    .services {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
    .service {
      background: var(--blanco);
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      text-align: center;
    }
    .service img {
      width: 100%;
      border-radius: 10px;
      height: 200px;
      object-fit: cover;
    }
    .promo {
      background: var(--rojo);
      color: var(--blanco);
      padding: 20px;
      text-align: center;
      font-size: 1.3rem;
      font-weight: bold;
      border-radius: 10px;
    }
    footer {
      background: var(--negro);
      color: var(--blanco);
      text-align: center;
      padding: 15px;
      font-size: 0.9rem;
    }
    .btn-whatsapp {
      background: #25d366;
      color: var(--blanco);
      padding: 15px 25px;
      display: inline-block;
      margin: 15px 5px;
      text-decoration: none;
      border-radius: 5px;
      font-weight: bold;
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
    <h2>Transforma tu estilo con nosotros</h2>
    <p>Cortes modernos, clásicos, arreglo de barba y más</p>
  </section>

  <section id="servicios" class="section">
    <h2>Servicios</h2>
    <div class="services">
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Corte+Moderno" alt="Corte moderno">
        <h3>Corte Moderno</h3>
        <p>Desde S/ 25</p>
      </div>
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Corte+Clasico" alt="Corte clásico">
        <h3>Corte Clásico</h3>
        <p>Desde S/ 20</p>
      </div>
      <div class="service">
        <img src="https://via.placeholder.com/400x300?text=Barba" alt="Arreglo de barba">
        <h3>Arreglo de Barba</h3>
        <p>S/ 15</p>
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
