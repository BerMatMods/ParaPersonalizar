
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>La Magia del Barbero | Barber Shop — Premium 3D</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#070708;
    --panel:#0f1011;
    --gold:#d4af37;
    --silver:#bfc7cc;
    --muted:#9aa4ad;
    --glass: rgba(255,255,255,0.04);
    --accent: linear-gradient(90deg,var(--gold),#ffd56b);
  }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:"Roboto",sans-serif;background:
    radial-gradient(800px 400px at 10% 10%, rgba(212,175,55,0.04), transparent 15%),
    radial-gradient(800px 400px at 90% 90%, rgba(191,199,204,0.02), transparent 15%),
    var(--bg);color:#e6e7e8;-webkit-font-smoothing:antialiased}
  a{color:inherit;text-decoration:none}
  .container{max-width:1200px;margin:0 auto;padding:28px}

  /* HEADER */
  header{display:flex;align-items:center;justify-content:space-between;gap:16px;padding:18px;border-radius:14px;background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);backdrop-filter:blur(6px);box-shadow:0 10px 30px rgba(0,0,0,0.6);border:1px solid rgba(255,255,255,0.03)}
  .brand{display:flex;align-items:center;gap:14px}
  .logo{
    width:72px;height:72px;border-radius:12px;display:grid;place-items:center;
    background:linear-gradient(135deg,#0b0b0c, #151617);
    border:2px solid rgba(255,255,255,0.04);box-shadow:0 8px 18px rgba(212,175,55,0.06);
    transform-style:preserve-3d; perspective:800px;
  }
  .logo svg{width:54px;height:54px;transform:translateZ(12px)}
  h1{font-family:"Bebas Neue",sans-serif;font-size:26px;margin:0;color:var(--gold);letter-spacing:1px}
  .tag{font-size:12px;color:var(--muted)}

  /* NAV */
  .nav{display:flex;gap:10px;align-items:center}
  .nav a{padding:10px 14px;border-radius:10px;font-weight:700;color:var(--silver);background:transparent;border:1px solid transparent;transition:all .25s}
  .nav a:hover{color:#070708;background:var(--gold);transform:translateY(-3px);box-shadow:0 10px 30px rgba(212,175,55,0.12)}
  .cta-whatsapp{background:#25d366;color:#04240b;padding:10px 14px;border-radius:10px;font-weight:700;box-shadow:0 8px 24px rgba(37,211,102,0.12)}

  /* LAYOUT: hero + side card */
  .hero-wrap{display:grid;grid-template-columns:1.2fr .8fr;gap:22px;margin-top:26px}
  @media (max-width:980px){.hero-wrap{grid-template-columns:1fr}.nav{flex-wrap:wrap;justify-content:center}}

  /* HERO */
  .hero{
    padding:36px;border-radius:16px;background:
      linear-gradient(180deg, rgba(212,175,55,0.03), rgba(255,255,255,0.01));
    border:1px solid rgba(255,255,255,0.03);position:relative;overflow:hidden;
  }
  .hero::after{
    content:"";position:absolute;inset:0;background:
    linear-gradient(120deg, rgba(212,175,55,0.02), rgba(191,199,204,0.01));
    pointer-events:none;
    mix-blend-mode:overlay;
  }
  .hero h2{font-family:"Bebas Neue";font-size:48px;color:var(--gold);margin:0 0 8px;letter-spacing:1px;text-shadow:0 6px 30px rgba(212,175,55,0.08)}
  .hero p{color:var(--silver);margin-bottom:18px}
  .hero .actions{display:flex;gap:12px;flex-wrap:wrap}
  .btn{padding:12px 18px;border-radius:12px;font-weight:700;border:none;cursor:pointer}
  .btn-primary{background:var(--gold);color:#070707;box-shadow:0 10px 30px rgba(212,175,55,0.12)}
  .btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--silver)}

  /* 3D CARD (tilt) */
  .card-3d{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);border-radius:18px;padding:18px;border:1px solid rgba(255,255,255,0.04);
    transform-style:preserve-3d;transition:transform .18s ease,box-shadow .18s;will-change:transform;box-shadow:0 10px 30px rgba(0,0,0,0.5)}
  .card-3d .inner{transform-style:preserve-3d;transition:transform .2s}
  .card-3d h3{margin:0 0 6px;color:var(--gold);font-family:"Bebas Neue"}
  .card-3d p{color:var(--silver);font-size:14px}

  /* HERO ART: big 3D mock */
  .hero-art{height:320px;border-radius:12px;overflow:hidden;background:
    radial-gradient(400px 200px at 10% 20%, rgba(212,175,55,0.04), transparent),
    linear-gradient(180deg,#0d1112,#070708);display:grid;place-items:center;border:1px solid rgba(255,255,255,0.03)}
  .shiny{position:absolute;left:-30%;top:-30%;width:60%;height:60%;background:linear-gradient(120deg, rgba(255,255,255,0.12), rgba(255,255,255,0));transform:rotate(-20deg);filter:blur(40px);opacity:.4;animation:shimmer 5s linear infinite}
  @keyframes shimmer{0%{transform:translateX(-10%) rotate(-20deg)}50%{transform:translateX(20%) rotate(-20deg)}100%{transform:translateX(-10%) rotate(-20deg)}}

  /* SERVICES grid with 3D cards */
  .services-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:22px}
  @media(max-width:980px){.services-grid{grid-template-columns:repeat(1,1fr)}}
  .service-card{height:280px;padding:18px;border-radius:14px;display:flex;flex-direction:column;gap:12px;align-items:flex-start;justify-content:space-between;background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));border:1px solid rgba(255,255,255,0.03)}
  .service-media{width:100%;height:140px;border-radius:10px;overflow:hidden;background:#0c0c0d;display:grid;place-items:center;border:1px solid rgba(255,255,255,0.02)}
  .service-media svg{width:80%;height:100%}
  .service-card h4{margin:0;color:var(--gold);font-family:"Bebas Neue"}
  .service-card p{margin:0;color:var(--silver);font-size:13px}

  /* GALLERY 3D carousel (simple) */
  .gallery{margin-top:28px;display:flex;gap:18px;align-items:center;justify-content:center;overflow:hidden;padding:10px}
  .gallery .tile{width:220px;height:300px;border-radius:12px;background:#0b0b0c;border:1px solid rgba(255,255,255,0.03);display:grid;place-items:center;transform-style:preserve-3d;transition:transform .35s;box-shadow:0 20px 40px rgba(0,0,0,0.6)}
  .gallery .tile:hover{transform:translateY(-12px) rotateX(6deg) rotateY(6deg);box-shadow:0 30px 60px rgba(0,0,0,0.7)}
  .tile svg{width:70%;height:70%}

  /* LOYALTY horizontal */
  .loyalty{margin-top:28px;display:flex;gap:12px;align-items:center}
  .stamp{width:64px;height:64px;border-radius:12px;border:2px dashed rgba(255,255,255,0.06);display:grid;place-items:center;font-weight:800;color:var(--silver);background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent)}
  .stamp.filled{background:linear-gradient(180deg, rgba(212,175,55,0.12), rgba(212,175,55,0.04));border-style:solid;color:#070707}

  /* TEAM & TESTIMONIALS */
  .two-col{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-top:24px}
  @media(max-width:980px){.two-col{grid-template-columns:1fr}}
  .person{display:flex;gap:12px;align-items:center}
  .avatar{width:68px;height:68px;border-radius:12px;border:2px solid rgba(255,255,255,0.04);display:grid;place-items:center;background:#0c0c0d}
  .quote{background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);padding:16px;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}

  /* FAQ */
  .faq{margin-top:22px;display:grid;gap:12px}
  .faq-item{padding:14px;border-radius:12px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03)}
  .faq-item summary{font-weight:700;color:var(--gold);cursor:pointer}
  .faq-item p{color:var(--silver);margin-top:8px}

  /* RESERVA (form) */
  .reserva{margin-top:22px;padding:18px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);border:1px solid rgba(255,255,255,0.03)}
  .fields{display:grid;grid-template-columns:1fr 1fr;gap:12px}
  @media(max-width:640px){.fields{grid-template-columns:1fr}}
  input,textarea,select{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:12px;border-radius:10px;color:var(--silver);outline:none}
  textarea{min-height:80px}

  /* Footer */
  footer{margin-top:34px;padding:20px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);display:flex;justify-content:space-between;align-items:center;gap:12px;border:1px solid rgba(255,255,255,0.03)}
  footer .left{color:var(--muted)} footer .right{color:var(--silver);font-weight:700}

  /* small utilities */
  .muted{color:var(--muted);font-size:13px}
  .center{display:grid;place-items:center}
</style>
</head>
<body>
  <div class="container">

    <!-- HEADER -->
    <header>
      <div class="brand">
        <div class="logo" id="logo-tilt">
          <!-- simple barber icon -->
          <svg viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
            <rect width="64" height="64" rx="10" fill="#0b0b0c"/>
            <path d="M18 42c10 6 28 6 36 0" stroke="#ffd56b" stroke-width="2" stroke-linecap="round"/>
            <path d="M28 12c4-2 12-2 16 0" stroke="#ffd56b" stroke-width="2" stroke-linecap="round"/>
            <circle cx="20" cy="24" r="2.5" fill="#ffd56b"/>
            <circle cx="44" cy="24" r="2.5" fill="#ffd56b"/>
          </svg>
        </div>
        <div>
          <h1>La Magia del Barbero</h1>
          <div class="tag">Jirón Alfonso Ugarte, 3er piso — Atención premium</div>
        </div>
      </div>

      <nav class="nav">
        <a href="#servicios">Servicios</a>
        <a href="#galeria">Galería</a>
        <a href="#reserva">Reservar</a>
        <a class="cta-whatsapp" href="https://wa.me/51977355999?text=Hola%20La%20Magia%20del%20Barbero%2C%20quiero%20reservar" target="_blank">WhatsApp</a>
      </nav>
    </header>

    <!-- HERO + SIDE -->
    <div class="hero-wrap">
      <section class="hero card-3d" id="inicio" data-tilt>
        <div class="inner">
          <div style="display:flex;align-items:center;justify-content:space-between;gap:12px">
            <div>
              <h2>Precisión, estilo y actitud — <span style="font-size:18px;color:var(--silver)">tu look al siguiente nivel</span></h2>
              <p>Especialistas en fades, cortes clásicos y los mejores acabados con navaja. Ambiente premium y atención personalizada.</p>
              <div class="actions" style="margin-top:14px">
                <button class="btn btn-primary" onclick="location.href='#reserva'">Reservar ahora</button>
                <button class="btn btn-ghost" onclick="document.getElementById('faq').scrollIntoView({behavior:'smooth'})">Preguntas frecuentes</button>
              </div>
              <div style="margin-top:14px" class="muted">Tel: <strong>977 355 999</strong> • <strong>931 538 059</strong></div>
            </div>
            <div style="width:44%;display:grid;gap:12px">
              <div class="hero-art center" data-tilt>
                <!-- stylized barber svg mock -->
                <svg viewBox="0 0 320 240" xmlns="http://www.w3.org/2000/svg" aria-hidden>
                  <defs>
                    <linearGradient id="g" x1="0" x2="1"><stop offset="0" stop-color="#111"/><stop offset="1" stop-color="#222"/></linearGradient>
                  </defs>
                  <rect width="100%" height="100%" rx="12" fill="url(#g)"/>
                  <g transform="translate(40,30)">
                    <rect x="0" y="0" width="240" height="160" rx="10" fill="#0b0b0c"/>
                    <text x="22" y="90" fill="#ffd56b" font-family="Bebas Neue" font-size="36">FADES</text>
                  </g>
                </svg>
                <div class="shiny" aria-hidden="true"></div>
              </div>
              <div class="card-3d" style="padding:10px">
                <div class="inner">
                  <h3>Promoción de fidelidad</h3>
                  <p class="muted">Acumula tus cortes: al juntar 4 sellos el 5.º es gratis. Pide tu tarjeta digital en recepción.</p>
                  <div class="loyalty" style="margin-top:10px">
                    <div class="stamp filled">1</div>
                    <div class="stamp filled">2</div>
                    <div class="stamp filled">3</div>
                    <div class="stamp filled">4</div>
                    <div class="stamp">5</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <aside class="card-3d" data-tilt>
        <div class="inner">
          <h3>Servicios destacados</h3>
          <p class="muted">Explora nuestros estilos y pide recomendación personalizada.</p>
          <div style="margin-top:12px;display:grid;gap:10px">
            <div style="display:flex;gap:10px;align-items:center">
              <div style="width:44px;height:44px;border-radius:8px;background:#0b0b0c;display:grid;place-items:center;border:1px solid rgba(255,255,255,0.03)">✂️</div>
              <div><strong>Fades & Degradados</strong><div class="muted" style="font-size:13px">Finesse y contornos precisos</div></div>
            </div>
            <div style="display:flex;gap:10px;align-items:center">
              <div style="width:44px;height:44px;border-radius:8px;background:#0b0b0c;display:grid;place-items:center;border:1px solid rgba(255,255,255,0.03)">🪒</div>
              <div><strong>Barba y Navaja</strong><div class="muted" style="font-size:13px">Perfilado con acabado tradicional</div></div>
            </div>
            <div style="display:flex;gap:10px;align-items:center">
              <div style="width:44px;height:44px;border-radius:8px;background:#0b0b0c;display:grid;place-items:center;border:1px solid rgba(255,255,255,0.03)">🎨</div>
              <div><strong>Diseños & Líneas</strong><div class="muted" style="font-size:13px">Figuras a pedido</div></div>
            </div>
          </div>
          <div style="margin-top:18px">
            <button class="btn btn-primary" onclick="location.href='#galeria'">Ver galería</button>
          </div>
        </div>
      </aside>
    </div>

    <!-- SERVICIOS 3D GRID -->
    <section id="servicios" class="services-grid" aria-label="Servicios">
      <article class="service-card" data-tilt>
        <div class="service-media">
          <!-- svg placeholder -->
          <svg viewBox="0 0 200 140" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" fill="#061012"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="22">FADE</text></svg>
        </div>
        <div>
          <h4>Fade moderno</h4>
          <p>Transiciones suaves, textura y contornos precisos para un look urbano.</p>
        </div>
      </article>

      <article class="service-card" data-tilt>
        <div class="service-media">
          <svg viewBox="0 0 200 140" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" fill="#071015"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="20">CLÁSICO</text></svg>
        </div>
        <div>
          <h4>Corte clásico</h4>
          <p>Estilos a tijera con acabado elegante, ideal para ocasiones formales.</p>
        </div>
      </article>

      <article class="service-card" data-tilt>
        <div class="service-media">
          <svg viewBox="0 0 200 140" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" fill="#061015"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="20">BARBA</text></svg>
        </div>
        <div>
          <h4>Barba & Perfilado</h4>
          <p>Navaja caliente, toalla y productos de acabado para un perfil definido.</p>
        </div>
      </article>
    </section>

    <!-- GALLERY 3D -->
    <section id="galeria">
      <h2 style="margin-top:28px;font-family:'Bebas Neue';color:var(--gold);text-align:center">Galería — Inspiración</h2>
      <div class="gallery" aria-hidden="false" role="region" aria-label="Galería de estilos">
        <div class="tile" data-tilt><svg viewBox="0 0 120 160" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" rx="12" fill="#071015"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="18">F1</text></svg></div>
        <div class="tile" data-tilt><svg viewBox="0 0 120 160" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" rx="12" fill="#071015"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="18">F2</text></svg></div>
        <div class="tile" data-tilt><svg viewBox="0 0 120 160" xmlns="http://www.w3.org/2000/svg"><rect width="100%" height="100%" rx="12" fill="#071015"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="#ffd56b" font-family="Bebas Neue" font-size="18">F3</text></svg></div>
      </div>
    </section>

    <!-- TWO COLUMNS: TEAM + TESTIMONIALS -->
    <section class="two-col">
      <div class="card-3d" data-tilt>
        <h3>Nuestro equipo</h3>
        <div style="margin-top:12px;display:flex;flex-direction:column;gap:12px">
          <div class="person">
            <div class="avatar"><svg width="44" height="44" viewBox="0 0 64 64"><rect width="64" height="64" rx="10" fill="#09090a"/><circle cx="32" cy="26" r="10" fill="#ffd56b"/></svg></div>
            <div><strong>Jorge — Maestro Barbero</strong><div class="muted">10 años de experiencia en fades</div></div>
          </div>
          <div class="person">
            <div class="avatar"><svg width="44" height="44" viewBox="0 0 64 64"><rect width="64" height="64" rx="10" fill="#09090a"/><circle cx="32" cy="26" r="10" fill="#ffd56b"/></svg></div>
            <div><strong>Marcos — Perfilista</strong><div class="muted">Especialista en navaja y barba</div></div>
          </div>
        </div>
      </div>

      <div class="card-3d" data-tilt>
        <h3>Testimonios</h3>
        <div style="margin-top:12px;display:flex;flex-direction:column;gap:12px">
          <div class="quote">
            <strong>“Excelencia en cada detalle. Mi fade nunca quedó tan perfecto.”</strong>
            <div class="muted" style="margin-top:8px">— Carlos M.</div>
          </div>
          <div class="quote">
            <strong>“Ambiente premium y atención excelente. Recomendado 100%.”</strong>
            <div class="muted" style="margin-top:8px">— Luis R.</div>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ -->
    <section id="faq" style="margin-top:28px">
      <h2 style="font-family:'Bebas Neue';color:var(--gold);text-align:center">Preguntas frecuentes</h2>
      <div class="faq" style="max-width:1000px;margin:16px auto">
        <details class="faq-item"><summary>¿Atienden con cita?</summary><p>Sí, recomendamos reservar por WhatsApp para asegurar tu horario, aunque atendemos según disponibilidad.</p></details>
        <details class="faq-item"><summary>¿Aceptan tarjetas?</summary><p>Sí: Efectivo, Yape, Plin y tarjetas de débito/crédito.</p></details>
        <details class="faq-item"><summary>¿Cuánto dura un corte promedio?</summary><p>Un corte estándar puede tomar entre 25 y 45 minutos, dependiendo del servicio.</p></details>
      </div>
    </section>

    <!-- RESERVA -->
    <section id="reserva" class="reserva">
      <h2 style="font-family:'Bebas Neue';color:var(--gold)">Reserva rápida</h2>
      <p class="muted">Envíanos tu solicitud y te confirmamos por WhatsApp.</p>
      <div style="margin-top:12px;display:grid;gap:12px">
        <div class="fields">
          <input id="name" placeholder="Nombre" />
          <input id="phone" placeholder="Teléfono" />
          <select id="service">
            <option value="Fade">Fade moderno</option>
            <option value="Clasico">Corte clásico</option>
            <option value="Barba">Barba & Perfilado</option>
            <option value="Diseno">Diseño personalizado</option>
          </select>
          <input id="date" type="date" />
        </div>
        <textarea id="note" placeholder="
