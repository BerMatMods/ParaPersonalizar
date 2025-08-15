<!doctype html>

<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>La Magia del Barbero</title>
  <meta name="description" content="La Magia del Barbero - Estilo, calidad y confianza. Reserva ahora." />
  <style>
    /* ------------------- VARIABLES ------------------- */
    :root{
      --bg:#0b0b0b;
      --card:#0f0f10;
      --accent:#ffd166; /* dorado */
      --accent-2:#ff4d4d; /* rojo brillante */
      --muted:#bdbdbd;
      --glass: rgba(255,255,255,0.04);
      --glass-2: rgba(0,0,0,0.35);
      --radius:18px;
      --ff-sans: 'Poppins', system-ui, Arial, sans-serif;
      --ff-serif: 'Playfair Display', Georgia, serif;
    }
    /* ------------------- RESET ------------------- */n
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family:var(--ff-sans);
      background:linear-gradient(180deg,#060606 0%,#0b0b0b 100%);
      color:#fff; -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale; line-height:1.4;
    }
    a{color:inherit;text-decoration:none}
    img{max-width:100%;display:block}
    /* ------------------- CONTAINER ------------------- */
    .container{max-width:1200px;margin:0 auto;padding:28px}/* ------------------- NAV ------------------- */
header{position:fixed;top:18px;left:0;right:0;z-index:60;backdrop-filter: blur(6px);}
.topbar{display:flex;align-items:center;justify-content:space-between;gap:16px;padding:12px 24px;margin:0 auto;max-width:1200px;background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:12px;box-shadow:0 6px 20px rgba(0,0,0,0.6)}
.brand{display:flex;align-items:center;gap:12px}
.logo{width:56px;height:56px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#ffb86b);display:flex;align-items:center;justify-content:center;font-weight:800;color:#0b0b0b;font-family:var(--ff-serif);box-shadow:0 6px 18px rgba(0,0,0,0.6)}
nav a{margin-left:14px;padding:8px 12px;border-radius:10px;font-weight:600}
nav a:hover{background:rgba(255,255,255,0.03)}

/* ------------------- HERO ------------------- */
.hero{min-height:78vh;display:grid;grid-template-columns:1fr 420px;align-items:center;padding:120px 0}
.hero-left{padding:8px 18px}
.eyebrow{display:inline-block;padding:6px 12px;border-radius:999px;background:linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));color:var(--accent);font-weight:700;margin-bottom:12px}
h1{font-family:var(--ff-serif);font-size:48px;line-height:1.02;margin-bottom:10px;color:linear-gradient(90deg,var(--accent),#fff)}
h1 .neon{color:var(--accent);text-shadow:0 6px 28px rgba(255,209,102,0.08),0 0 18px rgba(255,209,102,0.12)}
p.lead{color:var(--muted);max-width:560px;margin-bottom:18px}
.hero-cta{display:flex;gap:12px;align-items:center}
.btn{display:inline-flex;align-items:center;gap:10px;padding:12px 18px;border-radius:14px;font-weight:700;cursor:pointer}
.btn-primary{background:linear-gradient(90deg,var(--accent),#ffc88a);color:#111;box-shadow:0 12px 30px rgba(255,177,66,0.12);transform:translateY(0);transition:transform .2s}
.btn-primary:hover{transform:translateY(-4px)}
.btn-ghost{border:1px solid rgba(255,255,255,0.06);background:transparent;color:var(--muted)}

/* ------------------- BANNER SLIDER (IMAGENES) ------------------- */
.slider{position:relative;border-radius:14px;overflow:hidden;box-shadow:0 20px 60px rgba(0,0,0,0.7);height:520px}
.slides{display:flex;height:100%;transition:transform .8s cubic-bezier(.22,.9,.24,1)}
.slide{min-width:100%;position:relative;background-size:cover;background-position:center}
.slide::after{content:"";position:absolute;inset:0;background:linear-gradient(180deg, rgba(11,11,11,0.2) 0%, rgba(6,6,6,0.7) 60%)}
.slider-indicators{position:absolute;left:12px;bottom:12px;display:flex;gap:8px}
.dot{width:10px;height:10px;border-radius:50%;background:rgba(255,255,255,0.12);cursor:pointer}
.dot.active{background:var(--accent)}

/* ------------------- SECTIONS ------------------- */
section{padding:72px 0}
.section-title{display:flex;align-items:center;gap:14px;margin-bottom:24px}
.section-title h2{font-family:var(--ff-serif);font-size:26px}
.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
.card{background:linear-gradient(180deg,var(--glass), rgba(255,255,255,0.02));padding:22px;border-radius:16px;box-shadow:0 20px 40px rgba(0,0,0,0.6);transform-style:preserve-3d;transition:transform .5s, box-shadow .5s}
.card:hover{transform:translateY(-10px) rotateX(4deg);box-shadow:0 40px 80px rgba(0,0,0,0.7)}
.card h3{margin-bottom:8px}
.price{font-weight:800;color:var(--accent-2)}

/* ------------------- BEFORE & AFTER SLIDER ------------------- */
.before-after{position:relative;height:360px;border-radius:16px;overflow:hidden}
.before-after img{height:100%;object-fit:cover}
.ba-handle{position:absolute;left:50%;top:0;bottom:0;width:3px;background:linear-gradient(180deg,var(--accent),#fff);cursor:ew-resize;display:flex;align-items:center;justify-content:center}
.ba-handle .dot{width:28px;height:28px;border-radius:50%;background:var(--accent);box-shadow:0 8px 22px rgba(255,209,102,0.14)}

/* ------------------- GALLERY ------------------- */
.gallery{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}

/* ------------------- TEAM ------------------- */
.team{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.member{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.2));padding:16px;border-radius:14px;text-align:center}
.avatar{width:120px;height:120px;border-radius:50%;margin:0 auto 12px;overflow:hidden;border:6px solid var(--glass-2);display:flex;align-items:center;justify-content:center}

/* ------------------- OFFERS & REVIEWS ------------------- */
.offers{display:flex;gap:18px}
.offer{flex:1;padding:20px;border-radius:14px;background:linear-gradient(90deg, rgba(255,77,77,0.06), rgba(255,209,102,0.04))}
.reviews{display:flex;flex-direction:column;gap:12px}
.review{background:var(--card);padding:16px;border-radius:12px}

/* ------------------- CONTACT ------------------- */
.contact-grid{display:grid;grid-template-columns:1fr 380px;gap:22px}
.form input,.form textarea{width:100%;padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff;margin-bottom:12px}
.map{border-radius:14px;overflow:hidden}

/* ------------------- WHATSAPP FLOAT ------------------- */
.whatsapp{position:fixed;right:18px;bottom:18px;z-index:200}
.wa-btn{display:inline-flex;align-items:center;gap:10px;padding:12px 14px;border-radius:999px;background:linear-gradient(90deg,#25d366,#1ebe5b);color:#042106;font-weight:800;box-shadow:0 12px 40px rgba(2,99,44,0.18)}

/* ------------------- FOOTER ------------------- */
footer{padding:36px 0;text-align:center;color:var(--muted)}

/* ------------------- RESPONSIVE ------------------- */
@media(max-width:1024px){
  .hero{grid-template-columns:1fr;gap:18px}
  .cards{grid-template-columns:repeat(2,1fr)}
  .gallery{grid-template-columns:repeat(3,1fr)}
  .team{grid-template-columns:repeat(2,1fr)}
  .contact-grid{grid-template-columns:1fr}
}
@media(max-width:560px){
  .container{padding:14px}
  h1{font-size:34px}
  .cards{grid-template-columns:1fr}
  .gallery{grid-template-columns:repeat(2,1fr)}
}

/* small sparkle animation */
@keyframes sparkle{0%{transform:translateY(0) rotate(0)}50%{transform:translateY(-6px) rotate(4deg)}100%{transform:translateY(0) rotate(0)}}

  </style>
</head>
<body>
  <header>
    <div class="topbar container">
      <div class="brand">
        <div class="logo">BM</div>
        <div>
          <div style="font-weight:800">La Magia del Barbero</div>
          <div style="font-size:12px;color:var(--muted)">Estilo · Confianza · Tradición</div>
        </div>
      </div>
      <nav>
        <a href="#servicios">Servicios</a>
        <a href="#galeria">Galería</a>
        <a href="#equipo">Equipo</a>
        <a href="#resenas">Reseñas</a>
        <a href="#contacto">Contacto</a>
      </nav>
    </div>
  </header>  <main>
    <div class="container">
      <section class="hero">
        <div class="hero-left">
          <span class="eyebrow">Barbería Premium</span>
          <h1><span class="neon">La Magia del Barbero</span><br><small style="font-size:18px;color:var(--muted);font-weight:600">Donde el estilo cobra vida</small></h1>
          <p class="lead">Cortes modernos y clásicos, arreglos de barba y diseños con navaja. Ambiente cómodo y productos premium. Reserva en segundos y luce impecable.</p>
          <div class="hero-cta">
            <a class="btn btn-primary" href="#contacto">Reservar ahora</a>
            <a class="btn btn-ghost" href="#galeria">Ver galería</a>
          </div><div style="margin-top:18px;display:flex;gap:10px;align-items:center">
        <div style="background:var(--glass);padding:10px;border-radius:12px;font-weight:700">🎁 Promoción: Corte + Barba S/25</div>
        <div style="color:var(--muted);font-size:13px">Horario: Lun-Sáb 9:00 - 21:00</div>
      </div>
    </div>

    <!-- SLIDER -->
    <div class="slider" aria-hidden="false">
      <div class="slides" id="slides">
        <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1591012911205-4f46a4b9f1f9?auto=format&fit=crop&w=1400&q=80')"></div>
        <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1628515174184-1b8b5a0e4b25?auto=format&fit=crop&w=1400&q=80')"></div>
        <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=1400&q=80')"></div>
      </div>
      <div class="slider-indicators" id="dots"></div>
    </div>
  </section>

  <!-- BEFORE & AFTER -->
  <section id="servicios">
    <div class="section-title">
      <h2>Mira el Antes & Después</h2>
    </div>
    <div class="before-after" id="ba">
      <img src="https://images.unsplash.com/photo-1603002886193-30c3b9d5b0e6?auto=format&fit=crop&w=1400&q=80" alt="Antes" style="position:absolute;left:0;top:0;bottom:0;width:100%;height:100%;object-fit:cover"/>
      <div id="baAfter" style="position:absolute;left:0;top:0;height:100%;overflow:hidden;width:50%;">
        <img src="https://images.unsplash.com/photo-1591012911205-4f46a4b9f1f9?auto=format&fit=crop&w=1400&q=80" alt="Después" style="height:100%;object-fit:cover;"/>
      </div>
      <div class="ba-handle" id="handle"><div class="dot"></div></div>
    </div>
  </section>

  <!-- SERVICES -->
  <section>
    <div class="section-title"><h2>Servicios Destacados</h2></div>
    <div class="cards">
      <div class="card">
        <h3>Corte Clásico</h3>
        <p class="muted">Corte preciso con estilo tradicional.</p>
        <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center"><div class="price">S/15</div><a class="btn btn-primary" href="#contacto">Agendar</a></div>
      </div>
      <div class="card">
        <h3>Degradado / Fade</h3>
        <p class="muted">Transiciones limpias y definidas.</p>
        <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center"><div class="price">S/20</div><a class="btn btn-primary" href="#contacto">Agendar</a></div>
      </div>
      <div class="card">
        <h3>Barba & Bigote</h3>
        <p class="muted">Recorte, perfilado y aceite de acabado.</p>
        <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center"><div class="price">S/12</div><a class="btn btn-primary" href="#contacto">Agendar</a></div>
      </div>
    </div>
  </section>

  <!-- GALLERY -->
  <section id="galeria">
    <div class="section-title"><h2>Galería de Estilos</h2></div>
    <div class="gallery">
      <img src="https://images.unsplash.com/photo-1581579181545-6e8f7f5b0b5a?auto=format&fit=crop&w=800&q=60" alt="corte1"/>
      <img src="https://images.unsplash.com/photo-1559526324-593bc073d938?auto=format&fit=crop&w=800&q=60" alt="corte2"/>
      <img src="https://images.unsplash.com/photo-1598970434795-0c54fe7c0642?auto=format&fit=crop&w=800&q=60" alt="corte3"/>
      <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=800&q=60" alt="corte4"/>
    </div>
  </section>

  <!-- TEAM -->
  <section id="equipo">
    <div class="section-title"><h2>Conoce a Nuestros Barberos</h2></div>
    <div class="team">
      <div class="member">
        <div class="avatar"><img src="https://images.unsplash.com/photo-1547425260-76bcadfb4f2c?auto=format&fit=crop&w=400&q=60" alt="Luis"/></div>
        <h4>Luis</h4>
        <div style="color:var(--muted);font-size:13px">Especialista en fades</div>
      </div>
      <div class="member">
        <div class="avatar"><img src="https://images.unsplash.com/photo-1544723795-3fb6469f5b39?auto=format&fit=crop&w=400&q=60" alt="Mario"/></div>
        <h4>Mario</h4>
        <div style="color:var(--muted);font-size:13px">Diseños con navaja</div>
      </div>
      <div class="member">
        <div class="avatar"><img src="https://images.unsplash.com/photo-1545996124-3a6f8b4e2c36?auto=format&fit=crop&w=400&q=60" alt="Jorge"/></div>
        <h4>Jorge</h4>
        <div style="color:var(--muted);font-size:13px">Barba & Estilos clásicos</div>
      </div>
    </div>
  </section>

  <!-- OFFERS & REVIEWS -->
  <section id="resenas">
    <div class="section-title"><h2>Ofertas y Reseñas</h2></div>
    <div style="display:grid;grid-template-columns:1fr 420px;gap:20px">
      <div class="offers">
        <div class="offer">
          <h3>Promoción semanal</h3>
          <p>Corte + Barba a S/25. Solo por tiempo limitado.</p>
          <div style="margin-top:12px;font-weight:800">Termina en <span id="countdown">03:12:45</span></div>
        </div>
        <div class="offer">
          <h3>Descuento nuevos clientes</h3>
          <p>10% de descuento en tu primera visita.</p>
        </div>
      </div>
      <div class="reviews">
        <div class="review"><strong>Juan P.</strong><div style="color:var(--muted);font-size:13px">"Me dejaron impecable, ambiente relajado. 5/5"</div></div>
        <div class="review"><strong>Carlos M.</strong><div style="color:var(--muted);font-size:13px">"Los mejores fades de la ciudad"</div></div>
        <div class="review"><strong>Mauro L.</strong><div style="color:var(--muted);font-size:13px">"Buena atención y precios justos"</div></div>
      </div>
    </div>
  </section>

  <!-- SHOP (simulado) -->
  <section>
    <div class="section-title"><h2>Tienda Recomendada</h2></div>
    <div style="display:flex;gap:16px;flex-wrap:wrap">
      <div class="card" style="min-width:220px;max-width:260px">
        <h4>Pomada Premium</h4>
        <div style="color:var(--muted);font-size:13px">Fijación media, acabado brillante</div>
        <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center"><div class="price">S/35</div><a class="btn btn-primary" href="#contacto">Comprar</a></div>
      </div>
      <div class="card" style="min-width:220px;max-width:260px">
        <h4>Aceite para barba</h4>
        <div style="color:var(--muted);font-size:13px">Hidratación y brillo natural</div>
        <div style="margin-top:12px;display:flex;justify-content:space-between;align-items:center"><div class="price">S/28</div><a class="btn btn-primary" href="#contacto">Comprar</a></div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contacto">
    <div class="section-title"><h2>Contacto & Reserva</h2></div>
    <div class="contact-grid">
      <div class="form">
        <input placeholder="Tu nombre" />
        <input placeholder="Tu teléfono" />
        <select style="width:100%;padding:12px;border-radius:10px;background:transparent;color:#fff;margin-bottom:12px;border:1px solid rgba(255,255,255,0.04)"><option>Corte clásico</option><option>Degradado</option><option>Barba</option></select>
        <input type="datetime-local" />
        <textarea placeholder="Mensaje (opcional)" rows="4"></textarea>
        <div style="display:flex;gap:10px"><a class="btn btn-primary" href="#">Enviar</a><a class="btn btn-ghost" href="tel:+51977355999">Llamar</a></div>
      </div>
      <div>
        <div class="map">
          <!-- Usa tu iframe de Google Maps aquí -->
          <iframe width="100%" height="280" frameborder="0" style="border:0" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3900.0000000000005!2d-77.00000000000001!3d-12.000000000000001!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMTLCsDAwJzAwLjAiUyA3N8KwMDAnMDAuMCJX!5e0!3m2!1ses!2spe!4v1620000000000!5m2!1ses!2spe"></iframe>
        </div>
        <div style="margin-top:12px;color:var(--muted);font-size:13px">
          <div>Dirección: Jirón Alfonso Ugarte, 3er piso</div>
          <div>Tel: <a href="tel:+51977355999">977 355 999</a></div>
          <div>Horario: Lun-Sáb 9:00 - 21:00</div>
        </div>
      </div>
    </div>
  </section>

  <footer>
    <div style="margin-top:22px;color:var(--muted);font-size:14px">© La Magia del Barbero · Creado con ❤️</div>
  </footer>
</div>

  </main>  <!-- WHATSAPP FLOAT -->  <div class="whatsapp">
    <a class="wa-btn" href="https://wa.me/51977355999?text=Hola%2C%20quiero%20reservar%20un%20corte" target="_blank">💬 Reservar</a>
  </div>  <script>
    /* ------------------- SLIDER LOGIC ------------------- */
    (function(){
      const slides=document.getElementById('slides');
      const dots=document.getElementById('dots');
      const total=slides.children.length;let idx=0;
      for(let i=0;i<total;i++){const d=document.createElement('div');d.className='dot';d.addEventListener('click',()=>go(i));dots.appendChild(d)}
      const dotEls=[...dots.children];dotEls[0].classList.add('active');
      function go(i){idx=i;slides.style.transform=`translateX(-${100*i}%)`;dotEls.forEach(x=>x.classList.remove('active'));dotEls[i].classList.add('active')}
      let auto=setInterval(()=>{idx=(idx+1)%total;go(idx)},4200);
      // pause on hover
      document.querySelector('.slider').addEventListener('mouseenter',()=>clearInterval(auto));
      document.querySelector('.slider').addEventListener('mouseleave',()=>auto=setInterval(()=>{idx=(idx+1)%total;go(idx)},4200));
    })();

    /* ------------------- BEFORE/AFTER HANDLE ------------------- */
    (function(){
      const baAfter=document.getElementById('baAfter');
      const handle=document.getElementById('handle');
      let dragging=false;const container=document.getElementById('ba');
      function setPos(x){const rect=container.getBoundingClientRect();let pct=(x-rect.left)/rect.width; if(pct<0)pct=0;if(pct>1)pct=1;baAfter.style.width=(pct*100)+'%';handle.style.left=(pct*100)+'%'}
      handle.addEventListener('mousedown',()=>dragging=true);window.addEventListener('mouseup',()=>dragging=false);window.addEventListener('mousemove',(e)=>{if(dragging)setPos(e.clientX)});
      // touch
      handle.addEventListener('touchstart',()=>dragging=true);window.addEventListener('touchend',()=>dragging=false);window.addEventListener('touchmove',(e)=>{if(dragging)setPos(e.touches[0].clientX)});
    })();

    /* ------------------- COUNTDOWN SIMPLE ------------------- */
    (function(){
      const el=document.getElementById('countdown');
      // ejemplo: cuenta regresiva 3 horas desde ahora
      let t=3*60*60;function fmt(s){const h=Math.floor(s/3600);const m=Math.floor((s%3600)/60);const ss=s%60;return `${String(h).padStart(2,'0')}:${String(m).padStart(2,'0')}:${String(ss).padStart(2,'0')}`} 
      el.textContent=fmt(t);setInterval(()=>{if(t>0){t--;el.textContent=fmt(t)}},1000);
    })();

    /* ------------------- SMALL TOUCH: make avatars circular images fit ------------------- */
    document.querySelectorAll('.avatar img').forEach(img=>{img.style.width='100%';img.style.height='100%';img.style.objectFit='cover'});
  </script></body>
</html>
