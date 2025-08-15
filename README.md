<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>La Magia del Barbero — Barber Shop Premium</title>
  <meta name="description" content="La Magia del Barbero — Barber Shop premium. Fades, clásicos, barba. Reserva por WhatsApp." />
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Montserrat:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    /* ------------------------
       VARIABLES Y RESET
       ------------------------ */
    :root{
      --bg:#070709;
      --panel:#0f1213;
      --gold:#d4af37;
      --gold-2:#ffcf66;
      --silver:#bfc7cc;
      --muted:#9aa4ad;
      --glass: rgba(255,255,255,0.03);
      --accent: linear-gradient(90deg,var(--gold),var(--gold-2));
      --card-radius:16px;
      --shadow-lg: 0 30px 60px rgba(0,0,0,0.7);
      --transition: 400ms cubic-bezier(.2,.9,.2,1);
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family: "Montserrat", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:
        radial-gradient(800px 400px at 10% 10%, rgba(212,175,55,0.04), transparent 10%),
        radial-gradient(800px 400px at 90% 90%, rgba(191,199,204,0.02), transparent 10%),
        var(--bg);
      color:#e9eef2;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      line-height:1.45;
      overflow-x:hidden;
      padding-bottom:60px;
    }
    a{color:inherit;text-decoration:none}
    img{max-width:100%;display:block}

    /* ------------------------
       LAYOUT: contenedor y header
       ------------------------ */
    .wrap{max-width:1200px;margin:26px auto;padding:20px}
    header{
      display:flex;align-items:center;justify-content:space-between;gap:16px;
      padding:18px;border-radius:14px;background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border:1px solid rgba(255,255,255,0.03);
      box-shadow: var(--shadow-lg);
      position:sticky;top:12px;z-index:60;
      backdrop-filter: blur(6px);
    }
    .brand{display:flex;gap:14px;align-items:center}
    .logo{
      width:68px;height:68px;border-radius:14px;background:linear-gradient(135deg,#0a0b0c,#111213);
      display:grid;place-items:center;border:1px solid rgba(255,255,255,0.04);box-shadow:0 8px 30px rgba(0,0,0,0.6);
      transform: translateZ(0);
    }
    .brand h1{font-family:"Bebas Neue",sans-serif;font-size:22px;color:var(--gold);letter-spacing:1px;margin:0}
    .brand p{font-size:12px;color:var(--muted);margin-top:2px}

    nav{display:flex;gap:8px;align-items:center}
    .nav-link{
      color:var(--silver);padding:8px 12px;border-radius:10px;font-weight:600;font-size:13px;
      transition: all 180ms ease;
    }
    .nav-link:hover{color:#070709;background:var(--gold);transform:translateY(-3px);box-shadow:0 10px 28px rgba(212,175,55,0.12)}

    .cta-wa{display:inline-flex;gap:10px;align-items:center;background:#25d366;color:#04240b;padding:10px 14px;border-radius:10px;font-weight:800;box-shadow:0 12px 30px rgba(37,211,102,0.12)}

    /* ------------------------
       HERO
       ------------------------ */
    .hero{
      margin-top:18px;display:grid;grid-template-columns:1fr 420px;gap:22px;align-items:stretch;
    }
    @media(max-width:980px){.hero{grid-template-columns:1fr}}
    .hero-card{
      border-radius:var(--card-radius);padding:28px;background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border:1px solid rgba(255,255,255,0.03);box-shadow:0 30px 60px rgba(0,0,0,0.6);position:relative;overflow:visible;
    }
    .hero h2{font-family:"Bebas Neue";font-size:42px;color:var(--gold);line-height:1;margin-bottom:10px}
    .hero p.lead{color:var(--silver);margin-bottom:18px;font-size:15px}

    .hero-actions{display:flex;gap:12px;flex-wrap:wrap}
    .btn{
      padding:12px 18px;border-radius:12px;font-weight:800;border:none;cursor:pointer;transition:all 220ms ease;
      box-shadow:0 12px 30px rgba(0,0,0,0.5);
    }
    .btn-primary{background:var(--gold);color:#070709}
    .btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--silver)}

    /* bright ribbon */
    .ribbon{
      position:absolute;right:-40px;top:-40px;width:220px;height:220px;border-radius:50%;background:conic-gradient(from 120deg, rgba(212,175,55,0.06), rgba(255,255,255,0.02));
      filter: blur(18px);opacity:0.9;pointer-events:none;
    }

    /* HERO ART (3D shiny card) */
    .art-card{
      border-radius:14px;background:linear-gradient(180deg,#0b0d0e,#070708);padding:10px;border:1px solid rgba(255,255,255,0.03);
      box-shadow:0 30px 60px rgba(0,0,0,0.6);display:grid;place-items:center;position:relative;overflow:hidden;
    }
    .art-card .shine{position:absolute;left:-50%;top:-50%;width:200%;height:200%;background:radial-gradient(800px 200px at 10% 10%, rgba(255,255,255,0.06), transparent 10%);transform:rotate(15deg);mix-blend-mode:overlay;animation:shimmer 5s linear infinite}
    @keyframes shimmer{0%{transform:translateX(-30%) rotate(15deg)}50%{transform:translateX(10%) rotate(15deg)}100%{transform:translateX(-30%) rotate(15deg)}}

    /* ------------------------
       SECCIONES 3D CARDS BRILLANTES
       ------------------------ */
    .section-title{font-family:"Bebas Neue";font-size:28px;color:var(--gold);text-align:center;margin:18px 0 24px}
    .cards-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
    @media(max-width:980px){.cards-grid{grid-template-columns:repeat(2,1fr)}}
    @media(max-width:640px){.cards-grid{grid-template-columns:1fr}}

    /* tarjeta 3D principal */
    .card-3d{
      perspective:1000px;
    }
    .card-inner{
      transform-style:preserve-3d;transition:transform var(--transition), box-shadow var(--transition);
      border-radius:14px;padding:14px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.03);box-shadow: 0 20px 40px rgba(0,0,0,0.6);overflow:hidden;position:relative;
    }
    .card-inner::before{
      content:"";position:absolute;inset:0;padding:1px;border-radius:14px;pointer-events:none;
      background:linear-gradient(90deg, rgba(212,175,55,0.06), rgba(255,255,255,0.01));mix-blend-mode:overlay;
    }
    .card-media{height:160px;border-radius:10px;overflow:hidden;border:1px solid rgba(255,255,255,0.02);display:grid;place-items:center;background:#060708;margin-bottom:12px}
    .card-title{font-family:"Bebas Neue";color:var(--gold);font-size:20px;margin-bottom:6px}
    .card-desc{color:var(--muted);font-size:14px}

    /* marco dorado brillante (animado) */
    .frame{
      position:absolute;inset:6px;border-radius:12px;pointer-events:none;
      box-shadow:0 4px 30px rgba(212,175,55,0.06), inset 0 0 24px rgba(212,175,55,0.02);
      background: linear-gradient(90deg, rgba(212,175,55,0.04), rgba(255,255,255,0.01));
      mix-blend-mode:screen;transition:opacity 300ms;
    }
    .glow{position:absolute;inset:-30px;border-radius:20px;filter:blur(24px);opacity:0.6;background:radial-gradient(300px 120px at 20% 20%, rgba(212,175,55,0.10), transparent)}

    /* ENTRY ANIMATIONS ON SCROLL */
    .invisible{opacity:0;transform:translateY(20px) scale(.98)}
    .visible{opacity:1;transform:translateY(0) scale(1);transition: all 700ms cubic-bezier(.2,.9,.2,1)}

    /* ------------------------
       GALLERY LIGHTBOX
       ------------------------ */
    .gallery{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
    @media(max-width:980px){.gallery{grid-template-columns:repeat(2,1fr)}}
    @media(max-width:640px){.gallery{grid-template-columns:1fr}}
    .g-thumb{cursor:pointer;border-radius:10px;overflow:hidden;border:1px solid rgba(255,255,255,0.03);position:relative}
    .g-thumb img{width:100%;height:170px;object-fit:cover;display:block;transition:transform 260ms}
    .g-thumb:hover img{transform:scale(1.04)}
    /* lightbox */
    .lightbox{position:fixed;inset:0;background:rgba(0,0,0,0.85);display:none;align-items:center;justify-content:center;z-index:2000;padding:20px}
    .lightbox.open{display:flex}
    .lightbox img{max-width:95%;max-height:85%;border-radius:12px;box-shadow:0 30px 60px rgba(0,0,0,0.8)}

    /* ------------------------
       TEAM, REVIEWS, LOYALTY
       ------------------------ */
    .team{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
    @media(max-width:980px){.team{grid-template-columns:repeat(2,1fr)}}
    @media(max-width:640px){.team{grid-template-columns:1fr}}
    .person{display:flex;gap:12px;align-items:center;padding:12px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);border:1px solid rgba(255,255,255,0.03)}
    .avatar{width:64px;height:64px;border-radius:12px;display:grid;place-items:center;background:#0b0c0d;border:1px solid rgba(255,255,255,0.03)}

    .reviews{display:grid;gap:12px}

    /* ------------------------
       RESERVA
       ------------------------ */
    .reserva{display:grid;grid-template-columns:1fr 380px;gap:18px}
    @media(max-width:980px){.reserva{grid-template-columns:1fr}}
    .form{padding:14px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);border:1px solid rgba(255,255,255,0.03)}
    input,textarea,select{width:100%;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:var(--silver);margin-bottom:10px;outline:none}
    textarea{min-height:100px;resize:vertical}

    /* ------------------------
       FOOTER
       ------------------------ */
    footer{margin-top:28px;padding:18px;border-radius:12px;text-align:center;color:var(--muted);border:1px solid rgba(255,255,255,0.03);background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent)}
    footer .credit{font-weight:700;color:var(--silver)}

    /* small helpers */
    .muted{color:var(--muted);font-size:13px}
    .center{display:grid;place-items:center}

    /* mobile tilt simulation */
    @media(max-width:640px){
      .card-inner{transform:none!important}
      .card-inner:hover{transform:none!important}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <!-- HEADER -->
    <header>
      <div class="brand">
        <div class="logo" aria-hidden>
          <!-- simple barber icon -->
          <svg width="44" height="44" viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
            <rect width="64" height="64" rx="10" fill="#0b0b0c"/>
            <path d="M18 42c10 6 28 6 36 0" stroke="#ffd56b" stroke-width="2" stroke-linecap="round"/>
            <path d="M28 12c4-2 12-2 16 0" stroke="#ffd56b" stroke-width="2" stroke-linecap="round"/>
            <circle cx="20" cy="24" r="2.5" fill="#ffd56b"/>
            <circle cx="44" cy="24" r="2.5" fill="#ffd56b"/>
          </svg>
        </div>
        <div>
          <h1>La Magia del Barbero</h1>
          <p class="muted">Jirón Alfonso Ugarte, 3er piso — Barbería premium</p>
        </div>
      </div>

      <nav>
        <a class="nav-link" href="#servicios">Servicios</a>
        <a class="nav-link" href="#galeria">Galería</a>
        <a class="nav-link" href="#equipo">Equipo</a>
        <a class="nav-link" href="#reserva">Reservar</a>
        <a class="cta-wa" href="https://wa.me/51977355999?text=Hola%20La%20Magia%20del%20Barbero%2C%20quiero%20reservar" target="_blank">📲 WhatsApp</a>
      </nav>
    </header>

    <!-- HERO -->
    <section class="hero">
      <div class="hero-card card-3d invisible" data-appear>
        <div class="ribbon" aria-hidden></div>
        <h2>Precisión y estilo — Tu look al siguiente nivel</h2>
        <p class="lead">Fades impecables, cortes clásicos y perfilados de barba con navaja caliente. Ambiente premium y atención personalizada.</p>
        <div class="hero-actions">
          <button class="btn btn-primary" onclick="document.getElementById('reserva').scrollIntoView({behavior:'smooth'})">Reservar ahora</button>
          <button class="btn btn-ghost" onclick="document.getElementById('galeria').scrollIntoView({behavior:'smooth'})">Ver galería</button>
        </div>
        <div style="margin-top:16px" class="muted">Tel: <strong>977 355 999</strong> • <strong>931 538 059</strong></div>
      </div>

      <aside class="art-card invisible" data-appear>
        <div class="shine" aria-hidden></div>
        <!-- card tilt container -->
        <div class="card-inner center" data-tilt style="width:100%;height:320px;border-radius:12px;overflow:hidden;position:relative">
          <img src="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=0be18b8f4a6f1d7f3a1d0f3e0b9c4b05" alt="Barbería - ejemplo" style="width:100%;height:100%;object-fit:cover;display:block;transform:translateZ(20px)">
          <div style="position:absolute;left:12px;bottom:14px;background:linear-gradient(90deg, rgba(0,0,0,0.4), transparent);padding:8px 12px;border-radius:10px">
            <div style="font-weight:800;color:var(--gold);font-family:'Bebas Neue'">La Magia del Barbero</div>
            <div style="color:var(--muted);font-size:13px">Experiencia y detalle en cada corte</div>
          </div>
        </div>
      </aside>
    </section>

    <!-- SERVICIOS -->
    <section id="servicios" style="margin-top:28px">
      <div class="section-title">Servicios destacados</div>
      <div class="cards-grid">
        <!-- Card 1 -->
        <div class="card-3d invisible" data-appear>
          <div class="card-inner" data-tilt>
            <div class="frame"></div>
            <div class="glow"></div>
            <div class="card-media">
              <img src="https://images.unsplash.com/photo-1582095133179-298c8729f480?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=4b8c3b2f5c2d9f6a1b2a3c4d5e6f7a8b" alt="Fade moderno" style="width:100%;height:100%;object-fit:cover">
            </div>
            <div>
              <div class="card-title">Fade moderno</div>
              <div class="card-desc">Degradados nítidos, contornos limpios y textura para tu estilo urbano.</div>
            </div>
          </div>
        </div>

        <!-- Card 2 -->
        <div class="card-3d invisible" data-appear>
          <div class="card-inner" data-tilt>
            <div class="frame"></div><div class="glow"></div>
            <div class="card-media">
              <img src="https://images.unsplash.com/photo-1599351430501-00c34fd10928?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=97b8c3f9d1a0b6c2d3e4f5a6b7c8d9e0" alt="Clásico" style="width:100%;height:100%;object-fit:cover">
            </div>
            <div>
              <div class="card-title">Corte clásico</div>
              <div class="card-desc">Corte a tijera y peine con acabado elegante y atemporal.</div>
            </div>
          </div>
        </div>

        <!-- Card 3 -->
        <div class="card-3d invisible" data-appear>
          <div class="card-inner" data-tilt>
            <div class="frame"></div><div class="glow"></div>
            <div class="card-media">
              <img src="https://images.unsplash.com/photo-1556228720-0a6b9ee8a6ae?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=abcd1234ef567890abcd1234ef567890" alt="Barba" style="width:100%;height:100%;object-fit:cover">
            </div>
            <div>
              <div class="card-title">Barba & Perfilado</div>
              <div class="card-desc">Navaja caliente, toalla y acabado profesional que define tu perfil.</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- GALERÍA -->
    <section id="galeria" style="margin-top:28px">
      <div class="section-title">Galería de trabajos</div>
      <div class="gallery">
        <div class="g-thumb card-3d invisible" data-appear>
          <img src="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=0be18b8f4a6f1d7f3a1d0f3e0b9c4b05" alt="Trabajo 1" data-full="https://images.unsplash.com/photo-1621605815971-79e3f8e5c16f?q=80&w=2000&auto=format&fit=crop&ixlib=rb-4.0.3&s=0be18b8f4a6f1d7f3a1d0f3e0b9c4b05">
        </div>
        <div class="g-thumb card-3d invisible" data-appear>
          <img src="https://images.unsplash.com/photo-1582095133179-298c8729f4a6f?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=77a8b9c3d1e2f3a4b5c6d7e8f9a0b1c2" alt="Trabajo 2" data-full="https://images.unsplash.com/photo-1582095133179-298c8729f4a6f?q=80&w=2000&auto=format&fit=crop&ixlib=rb-4.0.3&s=77a8b9c3d1e2f3a4b5c6d7e8f9a0b1c2">
        </div>
        <div class="g-thumb card-3d invisible" data-appear>
          <img src="https://images.unsplash.com/photo-1599351430501-00c34fd10928?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=97b8c3f9d1a0b6c2d3e4f5a6b7c8d9e0" alt="Trabajo 3" data-full="https://images.unsplash.com/photo-1599351430501-00c34fd10928?q=80&w=2000&auto=format&fit=crop&ixlib=rb-4.0.3&s=97b8c3f9d1a0b6c2d3e4f5a6b7c8d9e0">
        </div>
        <div class="g-thumb card-3d invisible" data-appear>
          <img src="https://images.unsplash.com/photo-1556228720-0a6b9ee8a6ae?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=abcd1234ef567890abcd1234ef567890" alt="Trabajo 4" data-full="https://images.unsplash.com/photo-1556228720-0a6b9ee8a6ae?q=80&w=2000&auto=format&fit=crop&ixlib=rb-4.0.3&s=abcd1234ef567890abcd1234ef567890">
        </div>
      </div>
    </section>

    <!-- TEAM & TESTIMONIOS -->
    <section style="margin-top:28px;display:grid;grid-template-columns:1fr 1fr;gap:18px">
      <div id="equipo">
        <div class="section-title" style="text-align:left;margin-left:10px">Nuestro equipo</div>
        <div class="team">
          <div class="person card-3d invisible" data-appear>
            <div class="avatar"><img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?q=80&w=600&auto=format&fit=crop&ixlib=rb-4.0.3&s=a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6" alt="Jorge" style="width:64px;height:64px;border-radius:10px;object-fit:cover"></div>
            <div>
              <div style="font-weight:800;color:var(--gold)">Jorge — Maestro Barbero</div>
              <div class="muted">10 años de experiencia en fades y navaja</div>
            </div>
          </div>

          <div class="person card-3d invisible" data-appear>
            <div class="avatar"><img src="https://images.unsplash.com/photo-1554151228-14d9def656e4?q=80&w=600&auto=format&fit=crop&ixlib=rb-4.0.3&s=99887766554433221100aabbccddeeff" alt="Marcos" style="width:64px;height:64px;border-radius:10px;object-fit:cover"></div>
            <div>
              <div style="font-weight:800;color:var(--gold)">Marcos — Perfilista</div>
              <div class="muted">Especialista en barba y detalles finos</div>
            </div>
          </div>

          <div class="person card-3d invisible" data-appear>
            <div class="avatar"><img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=600&auto=format&fit=crop&ixlib=rb-4.0.3&s=7766554433221100ffeeddccbbaa9988" alt="Lina" style="width:64px;height:64px;border-radius:10px;object-fit:cover"></div>
            <div>
              <div style="font-weight:800;color:var(--gold)">Lina — Estilista</div>
              <div class="muted">Peinados y tratamientos de acabado</div>
            </div>
          </div>
        </div>
      </div>

      <div>
        <div class="section-title" style="text-align:left;margin-left:10px">Testimonios</div>
        <div class="reviews">
          <div class="card-inner card-3d invisible" data-appear style="padding:16px">
            <div style="font-weight:800;color:var(--gold)">“El mejor fade que me han hecho — atención top.”</div>
            <div class="muted" style="margin-top:8px">— Carlos M.</div>
          </div>
          <div class="card-inner card-3d invisible" data-appear style="padding:16px">
