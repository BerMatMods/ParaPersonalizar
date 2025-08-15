<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>La Magia del Barbero — Kennedy</title>
  <meta name="description" content="La Magia del Barbero - Kennedy. Cortes para hombre, mujer y niños. Diseñado por AnthZz Berrocal." />
  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&family=Rajdhani:wght@400;600&family=Poppins:wght@300;600;800&display=swap" rel="stylesheet">
  <style>
    /* ===========================
       VARIABLES & RESET
       =========================== */
    :root{
      --bg-1:#0b0b0f;
      --bg-2:#0f0810;
      --neon:#00ffe1;
      --gold:#ffd166;
      --accent:#8a2be2;
      --muted:#cfcfcf;
      --glass: rgba(255,255,255,0.03);
      --card:#0f1114;
      --radius:14px;
      --fw-heading: 'Orbitron', sans-serif;
      --fw-body: 'Rajdhani', sans-serif;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      min-height:100vh;
      font-family:var(--fw-body);
      background: radial-gradient(1200px 600px at 10% 10%, rgba(138,43,226,0.06), transparent 12%), linear-gradient(180deg, var(--bg-1) 0%, var(--bg-2) 100%);
      color:#fff;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      overflow-x:hidden;
      line-height:1.5;
    }
    a{color:inherit}
    img{display:block;max-width:100%}
    button{font-family:inherit}

    /* little background texture */
    body::before{
      content:"";
      position:fixed;inset:0;z-index:0;
      background-image:url('https://www.transparenttextures.com/patterns/cubes.png');
      opacity:0.03;
      pointer-events:none;
    }

    /* ===========================
       LAYOUT
       =========================== */
    .wrap{position:relative;z-index:2;max-width:1200px;margin:0 auto;padding:20px}
    header.top{
      position:fixed;left:20px;right:20px;top:18px;z-index:200;
      display:flex;justify-content:space-between;align-items:center;
      backdrop-filter: blur(6px);
      background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      padding:12px 18px;border-radius:12px;box-shadow:0 12px 40px rgba(0,0,0,0.6);
    }
    .brand{display:flex;align-items:center;gap:12px}
    .logo{
      width:56px;height:56px;border-radius:12px;background:linear-gradient(135deg,var(--gold),#ffb86b);
      display:flex;align-items:center;justify-content:center;font-weight:900;color:#0b0b0b;font-family:var(--fw-heading);
      box-shadow:0 10px 40px rgba(255,177,66,0.06)
    }
    nav.topnav a{margin-left:12px;padding:8px 10px;border-radius:10px;color:var(--muted);font-weight:700}
    nav.topnav a:hover{color:#fff;transform:translateY(-3px)}

    main{padding-top:120px;}

    /* ===========================
       HERO (fullscreen style)
       =========================== */
    .hero{
      min-height:88vh;display:grid;align-items:center;gap:24px;grid-template-columns:1fr 420px;padding:40px 0;
    }
    .hero-left{padding-right:18px}
    .eyebrow{
      display:inline-block;padding:8px 14px;border-radius:999px;background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));color:var(--neon);font-weight:800;margin-bottom:12px
    }
    .title{
      font-family:var(--fw-heading);font-size:46px;line-height:1.02;color:var(--gold);
      text-shadow:0 8px 40px rgba(255,209,102,0.06);
    }
    .title small{display:block;font-family:var(--fw-body);font-size:16px;color:var(--muted);margin-top:6px;font-weight:600}
    .lead{color:var(--muted);margin-top:16px;max-width:640px}
    .cta-group{display:flex;gap:12px;margin-top:18px}
    .btn{
      display:inline-flex;align-items:center;gap:10px;padding:12px 18px;border-radius:14px;font-weight:800;cursor:pointer;position:relative;overflow:hidden;background:transparent;border:1px solid rgba(255,255,255,0.04)
    }
    .btn.primary{background:linear-gradient(90deg,var(--gold),#ffc88a);color:#111;box-shadow:0 14px 40px rgba(255,177,66,0.12)}
    .btn.primary::after{content:'';position:absolute;left:-60%;top:0;width:40%;height:100%;transform:skewX(-18deg);background:linear-gradient(90deg, rgba(255,255,255,0.12), rgba(255,255,255,0.04));transition:all .6s}
    .btn.primary:hover::after{left:120%}
    .btn.ghost{border:1px solid rgba(255,255,255,0.06);color:var(--muted);background:transparent}
    .mini-info{margin-top:18px;display:flex;gap:12px;align-items:center;color:var(--muted);font-size:13px}

    /* right side: slider card */
    .slider-card{border-radius:14px;overflow:hidden;box-shadow:0 40px 80px rgba(0,0,0,0.7);height:520px;position:relative;background:#0b0b0b}
    .slides{display:flex;height:100%;transition:transform .9s cubic-bezier(.2,.9,.25,1)}
    .slide{min-width:100%;background-size:cover;background-position:center;position:relative}
    .slide .tag{position:absolute;left:16px;bottom:18px;background:linear-gradient(90deg, rgba(0,0,0,0.45), rgba(0,0,0,0.25));padding:8px 12px;border-radius:8px;font-weight:800}
    .slider-dots{position:absolute;left:14px;bottom:14px;display:flex;gap:8px}
    .dot{width:12px;height:12px;border-radius:50%;background:rgba(255,255,255,0.08);cursor:pointer}
    .dot.active{background:var(--neon)}

    /* ===========================
       BEFORE/AFTER
       =========================== */
    .ba-section{padding:36px 0}
    .ba-wrap{position:relative;height:360px;border-radius:14px;overflow:hidden;box-shadow:0 20px 60px rgba(0,0,0,0.6)}
    .ba-base{position:absolute;inset:0}
    .ba-after{position:absolute;inset:0;overflow:hidden;width:50%}
    .ba-handle{position:absolute;left:50%;top:0;bottom:0;width:4px;background:linear-gradient(180deg,var(--neon),#fff);cursor:ew-resize;display:flex;align-items:center;justify-content:center}
    .ba-handle .dot{width:30px;height:30px;border-radius:50%;background:var(--neon);box-shadow:0 8px 26px rgba(0,255,225,0.14)}

    /* ===========================
       SERVICES
       =========================== */
    section.services{padding:58px 0}
    .section-title{display:flex;align-items:center;gap:14px;margin-bottom:24px}
    .section-title h2{font-family:var(--fw-heading);font-size:28px;color:var(--neon)}
    .cards{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.18));padding:18px;border-radius:12px;box-shadow:0 20px 40px rgba(0,0,0,0.6);transition:transform .45s}
    .card:hover{transform:translateY(-12px)}
    .card h3{margin-bottom:8px;color:var(--gold)}
    .card p{color:var(--muted);font-size:14px}

    /* ===========================
       SOBRE KENNEDY
       =========================== */
    .about{display:flex;gap:24px;align-items:center;padding:60px 0}
    .about .avatar{width:320px;height:320px;border-radius:16px;overflow:hidden;border:6px solid rgba(255,255,255,0.04);box-shadow:0 14px 40px rgba(0,0,0,0.6)}
    .about .bio h3{font-size:22px;color:var(--gold)}
    .about .bio p{color:var(--muted);margin-top:12px}

    /* ===========================
       GALLERY
       =========================== */
    .gallery{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;padding:40px 0}
    .gallery figure{position:relative;border-radius:12px;overflow:hidden;cursor:pointer}
    .gallery img{width:100%;height:200px;object-fit:cover;transition:transform .6s}
    .gallery figure:hover img{transform:scale(1.06);filter:brightness(1.06)}
    .gallery figcaption{position:absolute;left:10px;bottom:10px;background:linear-gradient(90deg, rgba(0,0,0,0.6), rgba(0,0,0,0.35));padding:6px 8px;border-radius:6px;font-weight:800}

    /* ===========================
       TESTIMONIALS
       =========================== */
    .testimonials{padding:48px 0}
    .t-list{display:flex;gap:18px;overflow-x:auto;padding-bottom:6px}
    .t-item{min-width:320px;background:var(--card);padding:18px;border-radius:12px;box-shadow:0 14px 40px rgba(0,0,0,0.6)}
    .t-item p{color:var(--muted)}

    /* ===========================
       CONTACT & MAP
       =========================== */
    .contact-grid{display:grid;grid-template-columns:1fr 420px;gap:20px;padding:48px 0}
    .form input,.form textarea,.form select{width:100%;padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff;margin-bottom:12px}
    .map-box{border-radius:12px;overflow:hidden;border:1px solid rgba(255,255,255,0.04);box-shadow:0 14px 40px rgba(0,0,0,0.6)}

    /* ===========================
       WHATSAPP & GITHUB FLOAT
       =========================== */
    .float-actions{position:fixed;right:18px;bottom:18px;display:flex;flex-direction:column;gap:12px;z-index:300}
    .wa-btn{display:inline-flex;align-items:center;gap:10px;padding:12px 14px;border-radius:999px;background:linear-gradient(90deg,#25d366,#1ebe5b);color:#042106;font-weight:800;box-shadow:0 12px 40px rgba(2,99,44,0.18)}
    .git-btn{display:inline-flex;align-items:center;gap:10px;padding:10px 12px;border-radius:12px;background:linear-gradient(90deg,#6a00f4,#c300ff);color:#fff;font-weight:700;box-shadow:0 12px 40px rgba(163,0,255,0.12)}

    /* ===========================
       FOOTER
       =========================== */
    footer.site{padding:36px 0;text-align:center;color:var(--muted);border-top:1px solid rgba(255,255,255,0.02);margin-top:40px}
    .credits{display:flex;align-items:center;gap:12px;justify-content:center}
    .credits .gh{width:44px;height:44px;border-radius:10px;background:#0b0b0b;display:flex;align-items:center;justify-content:center;font-weight:900}
    .credits a img{width:30px;height:30px;filter:invert(1);transition:transform .3s}
    .credits a:hover img{transform:scale(1.1) rotate(8deg)}

    /* ===========================
       REVEAL (scroll) & RESPONSIVE
       =========================== */
    .reveal{opacity:0;transform:translateY(20px);transition:all .7s cubic-bezier(.2,.9,.25,1)}
    .reveal.visible{opacity:1;transform:none}
    @media(max-width:1024px){
      .hero{grid-template-columns:1fr;min-height:unset}
      .gallery{grid-template-columns:repeat(3,1fr)}
      .cards{grid-template-columns:repeat(2,1fr)}
      .about{flex-direction:column;align-items:flex-start}
      .contact-grid{grid-template-columns:1fr}
    }
    @media(max-width:560px){
      .gallery{grid-template-columns:repeat(2,1fr)}
      header.top{left:8px;right:8px}
    }

    /* small sparkle */
    @keyframes sparkle{0%{transform:translateY(0)}50%{transform:translateY(-6px)}100%{transform:translateY(0)}}
  </style>
</head>
<body>

  <!-- TOP NAV -->
  <header class="top">
    <div class="brand">
      <div class="logo">BM</div>
      <div>
        <div style="font-weight:900;">La Magia del Barbero</div>
        <div style="font-size:12px;color:var(--muted)">Estilo · Confianza · Familia</div>
      </div>
    </div>
    <nav class="topnav">
      <a href="#servicios">Servicios</a>
      <a href="#galeria">Galería</a>
      <a href="#sobre">Sobre</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>

  <main class="wrap">
    <!-- HERO -->
    <section class="hero">
      <div class="hero-left">
        <span class="eyebrow">Barbería Premium</span>
        <div class="title">La Magia del Barbero <small>— Kennedy</small></div>
        <small class="lead">Cortes y estilos para hombre, mujer, niño y niña. Atención personalizada por Kennedy: fades, cortes clásicos, barbas y diseños con navaja. Vive la experiencia premium.</small>

        <div class="cta-group">
          <a class="btn primary" href="#contacto">Reservar ahora</a>
          <a class="btn ghost" href="#galeria">Ver galería</a>
        </div>

        <div class="mini-info">
          <div style="background:var(--glass);padding:10px;border-radius:10px;font-weight:700">🎁 Promoción semanal — consulta por WhatsApp</div>
          <div style="color:var(--muted);font-size:13px">Horario: Lun–Sáb 9:00 – 21:00</div>
        </div>
      </div>

      <!-- SLIDER / BANNER -->
      <div class="slider-card">
        <div class="slides" id="slides">
          <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1591012911205-4f46a4b9f1f9?auto=format&fit=crop&w=1400&q=90')">
            <div class="tag">Fade moderno</div>
          </div>
          <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=1400&q=90')">
            <div class="tag">Corte clásico</div>
          </div>
          <div class="slide" style="background-image:url('https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=1400&q=90')">
            <div class="tag">Barba & Perfilado</div>
          </div>
        </div>
        <div class="slider-dots" id="dots"></div>
      </div>
    </section>

    <!-- BEFORE & AFTER -->
    <section class="ba-section reveal" id="ba">
      <div class="section-title"><h2>Antes & Después</h2></div>
      <div class="ba-wrap">
        <img class="ba-base" src="https://images.unsplash.com/photo-1603002886193-30c3b9d5b0e6?auto=format&fit=crop&w=1400&q=90" alt="Antes" style="object-fit:cover;width:100%;height:100%;">
        <div id="baAfter" class="ba-after">
          <img src="https://images.unsplash.com/photo-1591012911205-4f46a4b9f1f9?auto=format&fit=crop&w=1400&q=90" alt="Después" style="height:100%;object-fit:cover">
        </div>
        <div id="handle" class="ba-handle"><div class="dot"></div></div>
      </div>
    </section>

    <!-- SERVICES -->
    <section class="services" id="servicios">
      <div class="section-title"><h2>Servicios Destacados</h2></div>
      <div class="cards">
        <div class="card reveal">
          <h3>Corte clásico</h3>
          <p>Precisión y acabado profesional. Ideal para un look elegante y duradero.</p>
        </div>
        <div class="card reveal">
          <h3>Fade / Degradado</h3>
          <p>Transiciones limpias y estilos modernos. Fades bajos, medios y altos.</p>
        </div>
        <div class="card reveal">
          <h3>Barba & Perfilado</h3>
          <p>Afeitado preciso, perfilado y aceites de acabado recomendados.</p>
        </div>
        <div class="card reveal">
          <h3>Niños</h3>
          <p>Cortes con paciencia y estilo para los más pequeños de la casa.</p>
        </div>
        <div class="card reveal">
          <h3>Mujer</h3>
          <p>Cortes y peinados modernos o clásicos, adaptados a cada persona.</p>
        </div>
        <div class="card reveal">
          <h3>Diseños & Navaja</h3>
          <p>Diseños artísticos y trabajos con navaja para un estilo único.</p>
        </div>
      </div>
    </section>

    <!-- ABOUT KENNEDY -->
    <section id="sobre" class="reveal">
      <div class="about">
        <div class="avatar">
          <img src="https://i.postimg.cc/bvST5wCV/Mag-Pic-20250501-185936660-3.jpg" alt="Kennedy - Barbero" style="width:100%;height:100%;object-fit:cover">
        </div>
        <div class="bio">
          <h3>Conoce a Kennedy</h3>
          <p>Kennedy tiene más de 5 años de experiencia y ha perfeccionado técnicas de fades, cortes clásicos y barbería familiar. Su prioridad es la atención personalizada: escucha, asesora y deja un acabado profesional.</p>
          <p style="margin-top:12px;color:var(--muted)">Atiende a todos: hombres, mujeres, niños y niñas. Reserva por WhatsApp o ven directamente.</p>

          <div style="margin-top:16px;display:flex;gap:10px">
            <a class="btn primary" href="https://wa.me/51937556459?text=Hola%2C%20quiero%20reservar%20con%20Kennedy" target="_blank">Reservar por WhatsApp</a>
            <a class="btn ghost" href="#contacto">Contacto</a>
          </div>
        </div>
      </div>
    </section>

    <!-- GALLERY (inclusive) -->
    <section id="galeria" class="reveal">
      <div class="section-title"><h2>Galería Inclusiva</h2></div>
      <div class="gallery" id="gallery">
        <!-- Hombre -->
        <figure data-title="Hombre - Fade moderno">
          <img src="https://source.unsplash.com/800x600/?man,haircut" alt="Hombre">
          <figcaption>Hombre</figcaption>
        </figure>
        <!-- Mujer -->
        <figure data-title="Mujer - Corte elegante">
          <img src="https://source.unsplash.com/800x600/?woman,haircut" alt="Mujer">
          <figcaption>Mujer</figcaption>
        </figure>
        <!-- Niño -->
        <figure data-title="Niño - Corte divertido">
          <img src="https://source.unsplash.com/800x600/?boy,haircut" alt="Niño">
          <figcaption>Niño</figcaption>
        </figure>
        <!-- Niña -->
        <figure data-title="Niña - Estilo moderno">
          <img src="https://source.unsplash.com/800x600/?girl,haircut" alt="Niña">
          <figcaption>Niña</figcaption>
        </figure>

        <!-- More realistic images -->
        <figure data-title="Antes & Después 1">
          <img src="https://images.unsplash.com/photo-1628515174184-1b8b5a0e4b25?auto=format&fit=crop&w=1000&q=80" alt="Antes y despues 1">
          <figcaption>Antes & Después 1</figcaption>
        </figure>
        <figure data-title="Corte con textura">
          <img src="https://images.unsplash.com/photo-1519750783826-e2420f3f93e1?auto=format&fit=crop&w=1000&q=80" alt="Textura">
          <figcaption>Textura</figcaption>
        </figure>
        <figure data-title="Diseño con navaja">
          <img src="https://images.unsplash.com/photo-1545996124-3a6f8b4e2c36?auto=format&fit=crop&w=1000&q=80" alt="Diseño">
          <figcaption>Diseño con navaja</figcaption>
        </figure>
        <figure data-title="Pompadour">
          <img src="https://images.unsplash.com/photo-1545972152-4f6a6f9a5f80?auto=format&fit=crop&w=1000&q=80" alt="Pompadour">
          <figcaption>Pompadour</figcaption>
        </figure>
      </div>
    </section>

    <!-- LIGHTBOX (hidden) -->
    <div id="lightbox" style="position:fixed;inset:0;background:rgba(0,0,0,0.92);display:none;align-items:center;justify-content:center;z-index:9999;padding:20px">
      <div style="max-width:1100px;width:100%;position:relative">
        <button id="lb-close" style="position:absolute;right:-10px;top:-10px;background:#111;border-radius:50%;width:44px;height:44px;border:0;color:#fff;font-weight:800;box-shadow:0 8px 30px rgba(0,0,0,0.6);cursor:pointer">X</button>
        <img id="lb-img" src="" alt="" style="width:100%;border-radius:12px;box-shadow:0 20px 80px rgba(0,0,0,0.6)" />
        <div id="lb-caption" style="margin-top:12px;color:var(--muted);text-align:center;font-weight:700"></div>
      </div>
    </div>

    <!-- TESTIMONIALS -->
    <section class="testimonials" id="testimonios">
      <div class="section-title"><h2>Opiniones de Clientes</h2></div>
      <div class="t-list">
        <div class="t-item reveal">
          <p>"¡Increíble! Kennedy me dejó perfecto. Atención de primera."</p>
          <strong style="display:block;margin-top:8px;color:var(--gold);text-align:right">— Juan P.</strong>
        </div>
        <div class="t-item reveal">
          <p>"Mi hijo quedó feliz con su corte. Muy profesionales."</p>
          <strong style="display:block;margin-top:8px;color:var(--gold);text-align:right">— Ana S.</strong>
        </div>
        <div class="t-item reveal">
          <p>"El mejor fade de la ciudad, sin duda volveré."</p>
          <strong style="display:block;margin-top:8px;color:var(--gold);text-align:right">— Miguel R.</strong>
        </div>
      </div>
    </section>

    <!-- CONTACT & MAP -->
    <section id="contacto" class="reveal">
      <div class="section-title"><h2>Contacto & Ubicación</h2></div>
      <div class="contact-grid">
        <div class="form">
          <input placeholder="Tu nombre" />
          <input placeholder="Tu teléfono" />
          <select>
            <option>Selecciona el servicio</option>
            <option>Corte clásico</option>
            <option>
