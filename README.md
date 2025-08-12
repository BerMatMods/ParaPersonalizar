<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>BerMatMix — Sorpresa para Briyidth</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@300;400;700;900&family=Dancing+Script&family=Orbitron:wght@400;700&display=swap" rel="stylesheet">
  <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>

  <style>
    :root{
      --bg-1:#071029; --card:#0f1724; --accent:#ff6b81; --accent2:#ffd166;
      --green:#3be36b; --matrix-dark:#001102; --glass: rgba(255,255,255,0.03);
      --blue:#5fb7ff; --red:#ff4d6d; --muted:#b8d9e6;
      --mono: 'Orbitron', monospace;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Montserrat,system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial;background:linear-gradient(180deg,#00101a 0%,var(--bg-1) 100%);color:var(--muted);-webkit-font-smoothing:antialiased}
    a{color:var(--accent2)}
    /* Layout */
    .wrap{max-width:1200px;margin:16px auto;padding:16px}
    header.top{display:flex;gap:12px;align-items:center;position:fixed;left:0;right:0;top:10px;padding:10px 18px;z-index:9999}
    .hamb{font-size:26px;color:var(--green);cursor:pointer;margin-right:12px}
    .brand{font-family:'Great Vibes';font-size:32px;color:var(--accent);text-shadow:0 6px 18px rgba(0,0,0,0.6)}
    .subtitle{font-size:12px;color:var(--accent2);opacity:0.95;margin-left:auto}
    /* Side menu */
    .side{position:fixed;left:-320px;top:0;height:100%;width:320px;background:linear-gradient(180deg,#08121a, #061219);border-right:1px solid rgba(255,255,255,0.03);padding:28px;transition:left .35s;z-index:9998}
    .side.show{left:0}
    .side h3{color:var(--green);font-family:var(--mono);font-weight:700;margin-bottom:8px}
    .side p{font-size:13px;color:#cfeefc}
    .navlink{display:block;padding:12px 10px;margin-top:8px;color:#cfeefc;text-decoration:none;border-radius:8px}
    .navlink:hover{background:rgba(255,255,255,0.02)}
    /* Matrix canvas background (full screen behind content) */
    canvas.matrix{position:fixed;inset:0;z-index:0;opacity:0.55}
    /* Main hero */
    main{position:relative;z-index:2;padding-top:120px}
    .grid{display:grid;grid-template-columns:1fr 420px;gap:18px;align-items:start}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:18px;border-radius:12px;box-shadow:0 12px 40px rgba(0,0,0,0.6);border:1px solid rgba(255,255,255,0.03)}
    .heroTitle{font-family:'Great Vibes';font-size:36px;color:var(--accent);margin-bottom:6px}
    .heroText{font-family:'Dancing Script',cursive;font-size:18px;color:#f6fbff}
    .actions{display:flex;gap:8px;margin-top:12px;flex-wrap:wrap}
    .btn{background:linear-gradient(90deg,var(--accent),#ff8fb3);border:none;padding:10px 12px;border-radius:10px;color:white;font-weight:700;cursor:pointer}
    .ghost{background:transparent;border:1px solid rgba(255,255,255,0.06)}
    /* Visuals area */
    .visuals{height:320px;border-radius:12px;overflow:hidden;position:relative;background:linear-gradient(180deg,rgba(0,0,0,0.2), rgba(0,0,0,0.1));border:1px solid rgba(255,255,255,0.02)}
    .flowers, .hearts{position:absolute;inset:0;pointer-events:none}
    /* Projects */
    .projects{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-top:12px}
    .proj{padding:10px;border-radius:8px;background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);border:1px solid rgba(255,255,255,0.02)}
    .proj h4{margin:0 0 6px 0;color:var(--green)}
    /* Terminal / Hacker mode */
    .termZone{margin-top:18px;padding:14px;border-radius:10px;background:linear-gradient(90deg,#021007,#071a0b);color:var(--green);font-family:monospace;position:relative;overflow:hidden}
    .termHeader{display:flex;align-items:center;gap:10px;margin-bottom:8px}
    .dot{width:12px;height:12px;border-radius:50%;display:inline-block}
    .dot.red{background:#ff5c6a}
    .dot.yellow{background:#ffd166}
    .dot.green{background:#3be36b}
    .termWindow{background:#000;border-radius:8px;padding:12px;min-height:160px;max-height:300px;overflow:auto;border:1px solid rgba(0,255,0,0.06)}
    .log{font-size:13px;line-height:1.4;color:var(--green)}
    .log .err{color:var(--red);font-weight:700}
    .log .ok{color:var(--blue);font-weight:700}
    .controls{display:flex;gap:8px;margin-top:10px}
    .inputFake{width:100%;padding:8px;background:#041205;border-radius:6px;border:1px solid rgba(255,255,255,0.03);color:var(--green);font-family:monospace}
    /* Comments */
    .comments{margin-top:14px;display:flex;flex-direction:column;gap:10px}
    .comment{background:linear-gradient(90deg,rgba(0,0,0,0.3),rgba(255,255,255,0.01));padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.02)}
    .stars{color:gold}
    /* Footer */
    footer{margin-top:24px;text-align:center;color:rgba(255,255,255,0.6);font-size:13px;padding-bottom:40px}
    /* Responsive */
    @media(max-width:980px){.grid{grid-template-columns:1fr}.visuals{height:200px}}
  </style>
</head>
<body>

  <!-- MATRIX CANVAS (background) -->
  <canvas id="matrix" class="matrix"></canvas>

  <!-- Top header -->
  <header class="top">
    <span class="hamb" id="hamb" title="Abrir menú" onclick="toggleSide()">&#9776;</span>
    <div class="brand">BerMatMix</div>
    <div class="subtitle">Sorpresa para <strong>Briyidth</strong> — Anth'Zz Berrocal</div>
  </header>

  <!-- Side menu -->
  <aside id="side" class="side">
    <h3>⚡BerMatModZ🔥 — Menú</h3>
    <p><strong>Nombre:</strong> Anth'Zz Berrocal<br><strong>Alias:</strong> ⚡BerMatModZ🔥<br><strong>Ubicación:</strong> Andahuaylas</p>
    <nav>
      <a class="navlink" href="#inicio" onclick="toggleSide()">Inicio</a>
      <a class="navlink" href="#proyectos" onclick="toggleSide()">Proyectos</a>
      <a class="navlink" href="#perfil" onclick="toggleSide()">Perfil</a>
      <a class="navlink" href="#redes" onclick="toggleSide()">Redes Sociales</a>
      <a class="navlink" href="#briyidth" onclick="toggleSide()">Mensaje para Briyidth</a>
      <a class="navlink" href="#hack" onclick="toggleSide()">Modo Secreto: Terminal</a>
    </nav>
    <hr style="border:none;border-top:1px solid rgba(255,255,255,0.03);margin-top:12px">
    <div style="font-size:13px;color:#cfeefc;margin-top:8px"><strong>Telegram:</strong> <a href="https://t.me/Berrocal_mdz" target="_blank">t.me/Berrocal_mdz</a><br><strong>GitHub:</strong> github.com/BerMatMods</div>
  </aside>

  <!-- Main content -->
  <main class="wrap">

    <div id="inicio" class="grid">
      <section class="card">
        <div class="heroTitle">TE AMO MUCHÍSIMO MI REINA</div>
        <div class="heroText">Mi BriyidthCha — te dedico esto con todo mi corazón. Aquí encontrarás todo mi mundo: proyectos, perfil y un modo secreto especial solo para ti.</div>

        <div class="actions">
          <button class="btn" onclick="openSurprise()">💌 Ver Carta Sorpresa</button>
          <button class="btn ghost" onclick="shareWhatsApp()">Compartir por WhatsApp</button>
          <button class="btn ghost" onclick="downloadHTML()">Descargar HTML</button>
          <button class="btn" onclick="activateModeSecret()">Activar Modo Secreto</button>
        </div>

        <div style="margin-top:12px" class="termZone">
          <div class="termHeader">
            <span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span>
            <div style="margin-left:8px;color:#9fffc2;font-family:var(--mono);font-weight:700">BerMatMix Terminal — Estado: <span id="termStatus" style="color:var(--green)">INACTIVO</span></div>
          </div>

          <div class="termWindow" id="termWindow" aria-live="polite">
            <div class="log">> Consola lista. Presiona <strong>Iniciar Simulación</strong> para lanzar secuencia.</div>
          </div>

          <div class="controls">
            <button class="btn" onclick="startSimulation()">Iniciar Simulación</button>
            <button class="btn ghost" onclick="stopSimulation()">Detener</button>
            <button class="btn ghost" onclick="clearTerminal()">Limpiar</button>
          </div>

          <div style="margin-top:12px">
            <input class="inputFake" placeholder="Comando simulado (ej: status / scan / run exploit_demo)" id="pseudoCmd" />
          </div>
        </div>
      </section>

      <aside class="card">
        <div class="visuals" id="visuals">
          <div class="flowers" id="flowers"></div>
          <div class="hearts" id="hearts"></div>
          <!-- small profile summary -->
          <div style="position:absolute;left:14px;bottom:14px;background:rgba(0,0,0,0.35);padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.02)">
            <strong style="color:var(--accent)">⚡BerMatModZ🔥</strong><br>
            Anth'Zz Berrocal — Programador & amante de la tecnología.
          </div>
        </div>

        <div style="margin-top:12px"><strong>Proyectos recopilados</strong>
          <div class="projects">
            <div class="proj">
              <h4>⚡BerMat-Bot MD🔥</h4>
              <div class="meta">Bot WhatsApp con menú personalizado, juegos XO, stickers y respuestas IA.</div>
            </div>
            <div class="proj">
              <h4>BerMatMods / BerMat_Mods</h4>
              <div class="meta">Scripts para Termux, gratis y personalizables.</div>
            </div>
            <div class="proj">
              <h4>BerMatModZ_ProyecBot</h4>
              <div class="meta">IA conversacional y juegos integrados.</div>
            </div>
            <div class="proj">
              <h4>Presentación HTML</h4>
              <div class="meta">Animaciones románticas, dedicatorias y páginas para sorprender.</div>
            </div>
          </div>
        </div>

      </aside>
    </div>

    <!-- Projects section -->
    <section id="proyectos" class="card" style="margin-top:18px">
      <h2 style="font-family:var(--mono);color:var(--green)">Proyectos</h2>
      <p style="color:#cfeefc">Resumen rápido de los proyectos principales e ideas: bots, Termux scripts, páginas animadas, y simuladores visuales.</p>
    </section>

    <!-- Profile -->
    <section id="perfil" class="card" style="margin-top:18px">
      <h2 style="font-family:var(--mono);color:var(--green)">Perfil</h2>
      <p><strong>Nombre:</strong> Anth'Zz Berrocal<br>
      <strong>Alias:</strong> ⚡BerMatModZ🔥<br>
      <strong>Ubicación:</strong> Andahuaylas<br>
      <strong>Gustos:</strong> gimnasio, tecnología, hacking estético, automatización con Python</p>
    </section>

    <!-- Social -->
    <section id="redes" class="card" style="margin-top:18px">
      <h2 style="font-family:var(--mono);color:var(--green)">Redes Sociales</h2>
      <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap;margin-top:10px">
        <a class="btn ghost" href="https://github.com/BerMatMods" target="_blank"><i class="fab fa-github"></i> GitHub</a>
        <a class="btn ghost" href="https://t.me/Berrocal_mdz" target="_blank"><i class="fab fa-telegram"></i> Telegram</a>
        <a class="btn ghost" href="#" target="_blank"><i class="fab fa-instagram"></i> Instagram</a>
      </div>
    </section>

    <!-- Briyidth message -->
    <section id="briyidth" class="card" style="margin-top:18px">
      <h2 style="font-family:'Great Vibes';font-size:30px;color:var(--accent)">Para mi reina — Briyidth</h2>
      <p style="font-family:'Dancing Script';font-size:20px;color:#fff">Te amo mucho mi amor mi reina hermosa, te doy gracias por llegar a mi vida; eres lo más valioso que tengo y tengo miedo a perderte. Siempre te voy a amar en las buenas y en las malas y sé que juntos vamos a salir adelante. Te amo muchísimo mi mami.</p>
    </section>

    <!-- Terminal / Hack Mode Section -->
    <section id="hack" class="card" style="margin-top:18px">
      <h2 style="font-family:var(--mono);color:var(--green)">Modo Secreto — Terminal de Simulación</h2>

      <p style="color:#cfeefc">Este panel es una simulación estética. Todo es ficticio y solo sirve para sorprender con efectos visuales.</p>

      <div style="display:flex;gap:12px;flex-wrap:wrap;align-items:flex-start">
        <div style="flex:1;min-width:320px">
          <div class="termZone">
            <div class="termHeader"><span style="font-family:var(--mono)">~ AnthZz@bermat</span></div>
            <div class="termWindow" id="fullTerm">
              <div class="log">[0.001] kernel loaded...</div>
            </div>

            <div style="margin-top:10px;display:flex;gap:8px">
              <button class="btn" onclick="startFullSim()">Iniciar Secuencia</button>
              <button class="btn ghost" onclick="panicButton()">⛔ Panic (Sim)</button>
              <button class="btn ghost" onclick="clearFullTerm()">Limpiar</button>
            </div>
          </div>
        </div>

        <div style="width:360px">
          <div class="card">
            <h4 style="color:var(--green)">Panel de Eventos</h4>
            <div id="events" style="font-family:monospace;font-size:13px;color:var(--muted);min-height:160px"></div>
          </div>

          <div class="card" style="margin-top:10px">
            <h4 style="color:var(--green)">Comentarios</h4>
            <div class="comments" id="comments">
              <!-- sample comments injected by JS -->
            </div>
          </div>
        </div>
      </div>

    </section>

    <footer>
      <div>Creado con ❤️ por <strong>Anth'Zz Berrocal</strong> — Envía esto a Briyidth para sorprenderla</div>
    </footer>

  </main>

  <!-- Background audio (romantic by default, user can replace) -->
  <audio id="bgMusic" loop preload="none" src="https://www.bensound.com/bensound-music/bensound-romantic.mp3"></audio>

  <script>
    /* ---------- Small helpers & visuals ---------- */
    // Flowers & hearts for romantic panel
    const flowersEl = document.getElementById('flowers');
    const heartsEl = document.getElementById('hearts');
    function makeFlowers(n=10){
      flowersEl.innerHTML='';
      for(let i=0;i<n;i++){
        const f=document.createElement('div'); f.className='flower';
        const s=30+Math.random()*60; f.style.width=s+'px'; f.style.height=s+'px';
        f.style.left=(Math.random()*100)+'%'; f.style.top=(Math.random()*100)+'%';
        f.style.background='radial-gradient(circle at 30% 30%, rgba(255,255,255,0.15), transparent 30%), linear-gradient(135deg,#ff9ab3,#ffd166)';
        f.style.borderRadius='50%'; f.style.opacity=0.7+Math.random()*0.3;
        f.style.position='absolute'; f.style.filter='blur(0.2px)'; flowersEl.appendChild(f);
      }
    }
    function makeHearts(n=10){
      heartsEl.innerHTML='';
      for(let i=0;i<n;i++){
        const h=document.createElement('div'); h.className='heart';
        h.style.position='absolute'; h.style.left=(Math.random()*100)+'%'; h.style.bottom=(Math.random()*20)+'%';
        h.style.width='18px'; h.style.height='18px'; h.style.transform='rotate(-45deg)';
        h.style.background='var(--accent)'; h.style.opacity=0.9;
        h.style.borderRadius='2px'; heartsEl.appendChild(h);
      }
    }
    makeFlowers(8); makeHearts(10);

    /* ---------- Matrix background ---------- */
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    function resizeCanvas(){ canvas.width = window.innerWidth; canvas.height = window.innerHeight; initMatrix(); }
    window.addEventListener('resize', resizeCanvas, false);

    let columns, drops, fontSize=14, letters='01';
    function initMatrix(){
      fontSize = Math.max(12, Math.floor(window.innerWidth / 120));
      columns = Math.floor(canvas.width / fontSize);
      drops = new Array(columns).fill(1);
      ctx.font = fontSize + "px monospace";
    }
    resizeCanvas();

    function drawMatrix(){
      ctx.fillStyle = "rgba(0,10,0,0.06)";
      ctx.fillRect(0,0,canvas.width,canvas.height);
      ctx.fillStyle = "#07ff6b";
      ctx.font = fontSize + "px monospace";
      for(let i=0;i<drops.length;i++){
        const text = letters.charAt(Math.floor(Math.random() * letters.length));
        ctx.fillText(text, i*fontSize, drops[i]*fontSize);
        if (drops[i]*fontSize > canvas.height && Math.random() > 0.985) drops[i] = 0;
        drops[i]++;
      }
    }
    setInterval(drawMatrix, 50);

    /* ---------- Side menu toggle ---------- */
    function toggleSide(){ document.getElementById('side').classList.toggle('show'); }

    /* ---------- Surprise modal / card typed animation ---------- */
    function openSurprise(){
      // Create modal
      if(document.getElementById('surpriseModal')) return;
      const modal = document.createElement('div'); modal.id='surpriseModal';
      modal.style.position='fixed'; modal.style.inset=0; modal.style.background='rgba(0,0,0,0.85)'; modal.style.display='flex'; modal.style.alignItems='center'; modal.style.justifyContent='center'; modal.style.zIndex=99999; modal.style.padding='18px';
      const card = document.createElement('div'); card.style.width='100%'; card.style.maxWidth='920px'; card.style.borderRadius='12px'; card.style.padding='20px'; card.style.background='linear-gradient(180deg,#081226,#071223)'; card.style.color='#fff';
      // close btn
      const close = document.createElement('button'); close.textContent='✕'; close.style.position='absolute'; close.style.right='20px'; close.style.top='18px'; close.style.fontSize='20px'; close.style.background='transparent'; close.style.border='none'; close.style.color='#fff'; close.onclick=()=>{document.body.removeChild(modal); bgMusic.pause();}
      modal.appendChild(close);
      const title = document.createElement('h2'); title.textContent = 'Para mi reina — Sorpresa'; title.style.fontFamily='Great Vibes'; title.style.color='var(--accent)';
      card.appendChild(title);
      const textWrap = document.createElement('div'); textWrap.style.whiteSpace='pre-wrap'; textWrap.style.fontSize='18px'; textWrap.style.padding='8px'; textWrap.style.marginTop='8px'; textWrap.style.minHeight='220px';
      card.appendChild(textWrap);
      const controls = document.createElement('div'); controls.style.marginTop='12px'; controls.style.display='flex'; controls.style.gap='8px';
      const musicBtn = document.createElement('button'); musicBtn.className='btn'; musicBtn.textContent='Reproducir/pausar música'; musicBtn.onclick = () => { toggleMusic(); }
      const shareBtn = document.createElement('button'); shareBtn.className='btn ghost'; shareBtn.textContent='Compartir por WhatsApp'; shareBtn.onclick = shareWhatsApp;
      controls.appendChild(musicBtn); controls.appendChild(shareBtn);
      card.appendChild(controls);
      modal.appendChild(card); card.style.position='relative';
      document.body.appendChild(modal);

      // Typing text
      const message = `🌸 Mi amor, esto es para ti 🌸\n\nTE AMO MUCHÍSIMO MI REINA Mi BriyidthCha\n\nTe amo mucho mi amor mi reina hermosa, te doy gracias por llegar a mi vida; eres lo más valioso que tengo y tengo miedo a perderte. Siempre te voy a amar en las buenas y en las malas y sé que juntos vamos a salir adelante. Te amo muchísimo mi mami.\n\n— Con todo mi corazón, Anth'Zz Berrocal`;
      let i = 0;
      bgMusic.volume = 0.75;
      // try to autoplay (may be blocked)
      bgMusic.play().catch(()=>{});
      const typer = setInterval(()=>{ textWrap.textContent = message.slice(0,i) + (i%2 ? '▌' : ''); i++; if(i>message.length){ clearInterval(typer); textWrap.textContent=message; showerHearts(); } }, 28);
    }

    function showerHearts(){
      makeHearts(32); setTimeout(()=>makeHearts(6),4000);
    }

    /* ---------- Music control ---------- */
    const bgMusic = document.getElementById('bgMusic');
    function toggleMusic(){ if(bgMusic.paused) bgMusic.play().catch(()=>alert('Activa reproducción desde el modal.')); else bgMusic.pause
