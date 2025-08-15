<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>La Magia del Barbero</title>
  <style>
    /* ---------------- Reset & Variables ---------------- */
    * { box-sizing: border-box; margin:0; padding:0; }
    html, body { width:100%; height:100%; overflow-x:hidden; font-family: 'Poppins', sans-serif; background:#050407; color:#fff; }
    a { text-decoration:none; color:inherit; }
    img { display:block; width:100%; }

    /* ---------------- Animations ---------------- */
    @keyframes fadeIn { from {opacity:0;} to {opacity:1;} }
    @keyframes fadeUp { from { opacity:0; transform: translateY(30px);} to {opacity:1; transform:translateY(0);} }
    @keyframes shine { 0% {left:-50%;} 50% {left:150%;} 100% {left:150%;} }

    .reveal { opacity:0; transform: translateY(30px); transition: all .7s ease-in-out; }
    .reveal.visible { opacity:1; transform: none; }

    /* ---------------- Header (Hero) ---------------- */
    header { display:flex; flex-direction: column; align-items: center; justify-content:center; height:100vh; background: url('https://source.unsplash.com/1600x900/?barber-shop') center/cover no-repeat; text-align: center; position: relative; }
    header:after { content:''; position:absolute; inset:0; background: rgba(0,0,0,0.5); }
    header h1, header p, header nav { position: relative; z-index:1; }
    header h1 { font-size:3em; color:#ffd166; animation: fadeIn 1s ease forwards; }
    header p { font-size:1.5em; margin-top:10px; color:#fff; animation: fadeIn 1.5s ease forwards; }
    header nav { margin-top:20px; animation: fadeIn 2s ease forwards; }
    header nav a { margin:0 15px; font-size:1.1em; color:#fff; padding:8px 12px; border-radius:6px; transition: 0.3s; }
    header nav a:hover { background:rgba(255,255,255,0.1); }

    /* ---------------- Sección Sobre mí ---------------- */
    #sobre { padding:60px 20px; display:flex; align-items:center; gap:40px; background:#0b0b0b; }
    #sobre img { width:300px; border-radius:15px; box-shadow: 0 8px 24px rgba(255,209,102,0.5); }
    #sobre .texto { flex:1; }
    #sobre .texto h2 { font-size:2em; color:#ffd166; margin-bottom:10px; }
    #sobre .texto p { font-size:1.1em; line-height:1.6; }

    /* ---------------- Servicios ---------------- */
    #servicios { padding:60px 20px; }
    #servicios h2 { font-size:2em; color:#ffd166; text-align:center; margin-bottom:30px; }
    .servicios { display:grid; grid-template-columns: repeat(auto-fit,minmax(260px,1fr)); gap:20px; }
    .servicio { background:#111; border-radius:12px; overflow:hidden; position:relative; opacity:0; transform: translateY(30px); transition: 0.5s; }
    .servicio.visible { opacity:1; transform:none; }
    .servicio img { height:180px; object-fit:cover; }
    .servicio .info { padding:20px; }
    .servicio .info h3 { color: #ffd166; margin-bottom:8px; }
    .servicio .info p { font-size:1em;  }
    .btn { display:inline-block; padding:10px 16px; margin-top:12px; background:#ffd166; color:#111; border-radius:8px; font-weight:bold; position:relative; overflow:hidden; }
    .btn::after { content:''; position:absolute; top:0; left:-100%; width:50%; height:100%; background:rgba(255,255,255,0.4); transform: skewX(-20deg); transition:0.7s; }
    .btn:hover::after { left:200%; }

    /* ---------------- Galería con Lightbox Simulado ---------------- */
    #galeria { padding:60px 20px; background:#0b0b0b; }
    #galeria h2 { font-size:2em; color:#ffd166; text-align:center; margin-bottom:30px; }
    .galeria { display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px; }
    .galeria figure { cursor:pointer; position:relative; overflow:hidden; }
    .galeria figure img { width:100%; height:150px; object-fit:cover; filter: brightness(0.9); transition:0.5s; }
    .galeria figure:hover img { filter: brightness(1.1); transform:scale(1.05); }
    .galeria figcaption { position:absolute; bottom:8px; left:8px; background:rgba(0,0,0,0.5); padding:6px 8px; font-size:0.9em; color:#ffd166; }

    /* ---------------- Testimonios Slider Simulado ---------------- */
    #testimonios { padding:60px 20px; }
    #testimonios h2 { font-size:2em; color:#ffd166; text-align:center; margin-bottom:30px; }
    .testimonios { display:flex; overflow-x:auto; gap:20px; padding-bottom:10px; }
    .testimonio { min-width:300px; background:#111; border-radius:12px; padding:20px; box-shadow: 0 4px 16px rgba(0,0,0,0.6); flex-shrink:0; position:relative; }
    .testimonio p { font-style:italic; margin-bottom:12px; }
    .testimonio strong { display:block; color:#ffd166; text-align:right; }

    /* ---------------- Ubicación ---------------- */
    #ubicacion { padding:60px 20px; }
    #ubicacion h2 { font-size:2em; color:#ffd166; text-align:center; margin-bottom:30px; }
    .mapa { border-radius:12px; overflow:hidden; box-shadow:0 4px 16px rgba(0,0,0,0.6); }

    /* ---------------- Footer ---------------- */
    footer { background:#0b0b0b; padding:40px 20px; text-align:center; }
    footer .hora { margin-bottom:20px; font-size:1em; color:#bbb; }
    .creditos { display:inline-flex; align-items:center; gap:10px; }
    .creditos a img { width:40px; height:40px; filter: invert(1); transition:0.3s; }
    .creditos a:hover img { transform:scale(1.2) rotate(10deg); filter:drop-shadow(0 0 8px gold); }

  </style>
</head>
<body>
  <!-- Hero -->
  <header>
    <h1>La Magia del Barbero</h1>
    <p>Tu barbero de confianza: <strong>Kennedy</strong></p>
    <nav><a href="#servicios">Servicios</a><a href="#galeria">Galería</a><a href="#ubicacion">Ubicación</a></nav>
  </header>

  <!-- Sobre mí -->
  <section id="sobre" class="reveal">
    <img src="https://source.unsplash.com/400x400/?barber,portrait" alt="Kennedy - Barbero" />
    <div class="texto">
      <h2>Sobre Kennedy</h2>
      <p>Con más de 5 años de experiencia, Kennedy es un experto en cortes modernos, fades impecables y diseños con navaja. Su pasión por el estilo y atención al detalle lo convierten en uno de los barberos más recomendados de la ciudad.</p>
    </div>
  </section>

  <!-- Servicios -->
  <section id="servicios">
    <h2 class="reveal">Servicios de Kennedy</h2>
    <div class="servicios">
      <div class="servicio reveal"><img src="https://source.unsplash.com/400x300/?barber,fade" alt="Fade Moderno"><div class="info"><h3>Fade Moderno</h3><p>Transiciones limpias y acabados modernos que resaltan tu estilo.</p><a href="#ubicacion" class="btn">Agendar</a></div></div>
      <div class="servicio reveal"><img src="https://source.unsplash.com/400x300/?beard,barber" alt="Barba Perfilada"><div class="info"><h3>Barba Perfilada</h3><p>Recorte de barba preciso, perfilado y estilo impecable.</p><a href="#ubicacion" class="btn">Agendar</a></div></div>
      <div class="servicio reveal"><img src="https://source.unsplash.com/400x300/?barber,classic" alt="Corte Clásico"><div class="info"><h3>Corte Clásico</h3><p>Estilo tradicional y elegante, con un acabado profesional.</p><a href="#ubicacion" class="btn">Agendar</a></div></div>
      <div class="servicio reveal"><img src="https://source.unsplash.com/400x300/?haircut,modern" alt="Corte Moderno"><div class="info"><h3>Corte Moderno</h3><p>Diseños contemporáneos adaptados a tu personalidad.</p><a href="#ubicacion" class="btn">Agendar</a></div></div>
    </div>
  </section>

  <!-- Galería -->
  <section id="galeria">
    <h2 class="reveal">Galería de Trabajos Reales</h2>
    <div class="galeria">
      <figure class="reveal"><img src="https://images.unsplash.com/photo-1591012911205-4f46a4b9f1f9?auto=format&fit=crop&w=800" alt="Antes y Después 1"><figcaption>Antes y Después 1</figcaption></figure>
      <figure class="reveal"><img src="https://images.unsplash.com/photo-1628515174184-1b8b5a0e4b25?auto=format&fit=crop&w=800" alt="Antes y Después 2"><figcaption>Antes y Después 2</figcaption></figure>
      <figure class="reveal"><img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=800" alt="Corte Detallado"><figcaption>Corte Detallado</figcaption></figure>
      <figure class="reveal"><img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=800" alt="Fade Completo"><figcaption>Fade Completo</figcaption></figure>
    </div>
  </section>

  <!-- Testimonios -->
  <section id="testimonios">
    <h2 class="reveal">Opiniones de Clientes</h2>
    <div class="testimonios">
      <div class="testimonio reveal"><p>"¡Increíble corte! Kennedy sabe lo que hace."</p><strong>– Juan P.</strong></div>
      <div class="testimonio reveal"><p>"Profesional y detallista, siempre salgo satisfecho."</p><strong>– Carlos M.</strong></div>
      <div class="testimonio reveal"><p>"El mejor fade que he tenido."</p><strong>– Miguel L.</strong></div>
    </div>
  </section>

  <!-- Ubicación -->
  <section id="ubicacion">
    <h2 class="reveal">Ubicación</h2>
    <div class="mapa reveal">
      <iframe src="https://maps.app.goo.gl/5um9wS8RcRro1foS7?g_st=ac" allowfullscreen loading="lazy"></iframe>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="hora">Horario: Lun–Sáb 9:00 – 21:00</div>
    <div class="creditos">
      <p>Diseñado por <strong>AnthZz Berrocal</strong></p>
      <a href="https://github.com/BerMatMods" target="_blank">
        <img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" alt="GitHub" />
      </a>
    </div>
  </footer>

  <!-- Scroll Reveal Script -->
  <script>
    document.addEventListener('DOMContentLoaded', () => {
      const reveals = document.querySelectorAll('.reveal');
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.2 });
      reveals.forEach(el => observer.observe(el));
    });
  </script>
</body>
</html>
