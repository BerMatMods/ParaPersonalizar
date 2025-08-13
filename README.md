<!DOCTYPE html><html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Rubik 3D Neon — BerMatModZ</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;800&family=Orbitron:wght@500;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#05060a;
      --panel:#0b0f1a;
      --accent:#00e5ff;
      --accent2:#ff00ff;
      --glow:0 0 20px rgba(0,229,255,.6),0 0 40px rgba(255,0,255,.2);
      --soft:0 10px 30px rgba(0,0,0,.4);
    }
    *{box-sizing:border-box}
    body{
      margin:0; background: radial-gradient(1200px 600px at 15% 10%,#0b0f1a 0%,#070912 45%,#05060a 100%);
      color:#e8f1ff; font-family:Poppins, system-ui, -apple-system, Segoe UI, Roboto, Arial;
      min-height:100vh; display:grid; grid-template-columns: 1.2fr .8fr; gap:16px;
    }
    header{
      position:fixed; left:16px; right:16px; top:12px; display:flex; align-items:center; justify-content:space-between; z-index:10;
    }
    .brand{
      display:flex; align-items:center; gap:12px; letter-spacing:.5px;
      text-shadow:0 0 10px rgba(0,229,255,.5);
    }
    .brand .logo{
      width:40px; height:40px; border-radius:12px; background:conic-gradient(from 0deg,#00e5ff,#22ff88,#ffe600,#ff6b00,#ff00ff,#00e5ff);
      box-shadow: var(--glow); filter:saturate(1.2);
    }
    .brand h1{font:800 18px/1 Orbitron, Poppins; margin:0}.wrap3d{ position:relative; height:100vh; overflow:hidden; }
canvas{ display:block; width:100%; height:100%; }

.ui{
  position:absolute; bottom:22px; left:50%; transform:translateX(-50%);
  display:flex; flex-wrap:wrap; gap:10px; justify-content:center;
  backdrop-filter: blur(8px); background: linear-gradient( to right, rgba(0,229,255,.12), rgba(255,0,255,.12));
  border:1px solid rgba(255,255,255,.12); padding:12px; border-radius:16px; box-shadow: var(--soft);
}
.btn{
  font:600 14px/1 Poppins; letter-spacing:.5px; padding:10px 12px; border-radius:12px; border:1px solid rgba(255,255,255,.14);
  background: radial-gradient(120% 120% at 10% 10%, rgba(0,229,255,.25), rgba(255,0,255,.18));
  color:#eaffff; cursor:pointer; transition:.2s transform, .2s box-shadow; text-shadow:0 0 6px rgba(0,229,255,.6);
  box-shadow: 0 0 0 0 rgba(0,229,255,.0);
}
.btn:hover{ transform:translateY(-1px); box-shadow:0 8px 24px rgba(0,229,255,.18); }
.btn:active{ transform:translateY(0) scale(.98) }

.side{
  position:sticky; top:0; height:100vh; overflow:auto; padding:80px 18px 24px; background: linear-gradient(180deg, rgba(0,229,255,.05), rgba(255,0,255,.04));
  border-left:1px solid rgba(255,255,255,.08);
}
.card{
  background:linear-gradient(180deg, rgba(15,22,35,.8), rgba(10,12,24,.8));
  border:1px solid rgba(255,255,255,.08); border-radius:18px; padding:18px; margin-bottom:16px; box-shadow: var(--soft);
}
.title{ font:800 20px/1.2 Orbitron; margin:0 0 6px; color:#e8fcff }
.sub{ font:600 12px/1.3 Poppins; margin:0 0 10px; color:#9bc7ff }

.grid2{ display:grid; grid-template-columns:1fr 1fr; gap:10px }

.tag{
  padding:8px 10px; border-radius:12px; border:1px solid rgba(255,255,255,.08);
  background: radial-gradient(100% 100% at 10% 10%, rgba(0,229,255,.18), rgba(255,0,255,.12));
  font:600 12px/1 Poppins; color:#eafcff; text-shadow:0 0 8px rgba(0,229,255,.5); box-shadow: var(--soft);
}
.socials{ display:flex; gap:10px; flex-wrap:wrap }
.socials a{
  display:inline-flex; align-items:center; gap:8px; padding:10px 12px; border-radius:14px; text-decoration:none; color:#e8f1ff;
  border:1px solid rgba(255,255,255,.1); box-shadow: var(--soft); background:linear-gradient(120deg, rgba(0,229,255,.16), rgba(255,0,255,.12));
  transition:.2s transform, .2s filter;
}
.socials a:hover{ transform: translateY(-1px); filter: brightness(1.1) }

.marquee{ display:flex; gap:12px; overflow:hidden; mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent); }
.marquee span{ white-space:nowrap; padding:8px 12px; border-radius:12px; border:1px solid rgba(255,255,255,.1); background:linear-gradient(90deg, rgba(0,229,255,.16), rgba(255,0,255,.12)); animation: slide 16s linear infinite; }
@keyframes slide{ from{ transform:translateX(0) } to{ transform:translateX(-50%) } }

.toast{ position:fixed; top:68px; left:50%; transform:translateX(-50%); padding:10px 14px; border-radius:12px; font:600 14px Poppins;
  background:linear-gradient(120deg, rgba(0,229,255,.25), rgba(255,0,255,.2)); border:1px solid rgba(255,255,255,.14); display:none; z-index:20; }

.modal{ position:fixed; inset:0; display:none; place-items:center; backdrop-filter: blur(8px); background:rgba(3,5,12,.6); z-index:50; }
.modal .box{ max-width:520px; margin:16px; background:linear-gradient(180deg, rgba(15,22,35,.95), rgba(10,12,24,.95)); border:1px solid rgba(255,255,255,.14); border-radius:20px; padding:22px; box-shadow: var(--glow); text-align:center }
.modal h2{ font:800 26px Orbitron; margin:0 0 10px; color:#a6fff8; text-shadow: var(--glow); }
.modal p{ margin:0 0 12px }
.modal .ok{ margin-top:4px }

@media (max-width: 980px){ body{ grid-template-columns: 1fr; } .side{ height:auto; position:relative } .wrap3d{ height:76vh } }

  </style>
</head>
<body>
  <header>
    <div class="brand">
      <div class="logo"></div>
      <h1>⚡ BerMatModZ — Rubik 3D Neon 🔥</h1>
    </div>
  </header>  <div class="wrap3d">
    <canvas id="scene"></canvas>
    <div class="ui" id="controls">
      <button class="btn" data-m="U">U</button>
      <button class="btn" data-m="U'">U'</button>
      <button class="btn" data-m="D">D</button>
      <button class="btn" data-m="D'">D'</button>
      <button class="btn" data-m="L">L</button>
      <button class="btn" data-m="L'">L'</button>
      <button class="btn" data-m="R">R</button>
      <button class="btn" data-m="R'">R'</button>
      <button class="btn" data-m="F">F</button>
      <button class="btn" data-m="F'">F'</button>
      <button class="btn" data-m="B">B</button>
      <button class="btn" data-m="B'">B'</button>
      <button class="btn" id="scramble">🔀 Mezclar</button>
      <button class="btn" id="reset">⟲ Reset</button>
    </div>
    <div class="toast" id="toast">¡Movimiento aplicado!</div>
  </div>  <aside class="side">
    <div class="card">
      <h2 class="title">Perfil — Anth'Zz Berrocal</h2>
      <p class="sub">Alias <b>BerMatModZ</b> | Creador de <b>⚡BerMat-Bot MD🔥</b> | Tech & IA | Andahuaylas</p>
      <div class="grid2">
        <div class="tag">WhatsApp Bot • .BerMat</div>
        <div class="tag">Programación • Python/JS</div>
        <div class="tag">Proyecto • BerMat_Mods</div>
        <div class="tag">Juego • XO + IA</div>
      </div>
    </div><div class="card">
  <h3 class="title" style="font-size:18px">Conexiones</h3>
  <div class="socials">
    <a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M9.04 15.315 8.89 19.6c.32 0 .46-.14.62-.31l2.98-2.86 6.18 4.53c1.13.62 1.93.29 2.23-1.05l4.04-18.94h.01c.36-1.67-.6-2.33-1.7-1.93L.96 9.32C-.66 9.96-.64 10.86.67 11.26l5.92 1.85L19.52 5.2c.6-.41 1.14-.18.69.23L9.04 15.315z"/></svg>
      Telegram
    </a>
    <a href="https://github.com/BerMatMods" target="_blank" rel="noopener">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M12 .5C5.73.5.98 5.24.98 11.5c0 4.86 3.15 8.98 7.52 10.43.55.1.75-.23.75-.53 0-.26-.01-1.1-.02-2-3.06.66-3.7-1.3-3.7-1.3-.5-1.27-1.22-1.61-1.22-1.61-.99-.67.08-.65.08-.65 1.1.08 1.68 1.12 1.68 1.12.98 1.68 2.58 1.19 3.21.91.1-.71.38-1.19.69-1.46-2.44-.28-5-1.22-5-5.44 0-1.2.43-2.18 1.13-2.95-.12-.28-.49-1.42.11-2.96 0 0 .92-.3 3.02 1.13a10.52 10.52 0 0 1 5.5 0c2.1-1.43 3.02-1.13 3.02-1.13.6 1.54.23 2.68.11 2.96.7.77 1.12 1.75 1.12 2.95 0 4.23-2.57 5.16-5.02 5.43.39.34.73 1.01.73 2.04 0 1.47-.01 2.65-.01 3.01 0 .3.19.65.76.53A10.99 10.99 0 0 0 23.02 11.5C23.02 5.24 18.27.5 12 .5Z"/></svg>
      GitHub
    </a>
  </div>
</div>

<div class="card">
  <h3 class="title" style="font-size:18px">Mensaje</h3>
  <div class="marquee">
    <span>𝑩𝑬𝑹𝑴𝑨𝑻𝑴𝑶𝑫𝑺 🫦 𝑻𝑬 𝑫𝑨 🤡 𝑳𝑨 𝑩𝑰𝑬𝑵𝑽𝑬𝑵𝑰𝑫𝑨 👹 𝑨𝑳 🔪 𝑴𝑼𝑵𝑫𝑶 𝑫𝑬 🔥 𝑪𝑰𝑽𝑬𝑹𝑨𝑻𝑨𝑸𝑼𝑬 😎 𝒀 💥 𝑪𝑰𝑽𝑬𝑹𝑺𝑬𝑮𝑼𝑹𝑰𝑫𝑨𝑫 👽🤖</span>
    <span>⚡ BerMat-Bot MD 🔥 — IA • Bots • Juegos • Seguridad</span>
  </div>
</div>

<div class="card">
  <h3 class="title" style="font-size:18px">Comandos rápidos</h3>
  <div class="grid2" id="quick">
    <button class="btn" data-m="R">R</button>
    <button class="btn" data-m="R'">R'</button>
    <button class="btn" data-m="F">F</button>
    <button class="btn" data-m="F'">F'</button>
    <button class="btn" id="mix2">Mezcla x10</button>
    <button class="btn" id="check">¿Resuelto?</button>
  </div>
</div>

  </aside>  <!-- Three.js & helpers -->  <script src="https://unpkg.com/three@0.160.0/build/three.min.js"></script>  <script src="https://unpkg.com/three@0.160.0/examples/js/controls/OrbitControls.js"></script>  <script>
  ;(() => {
    const canvas = document.getElementById('scene');

    const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, powerPreference:'high-performance' });
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

    const scene = new THREE.Scene();
    scene.fog = new THREE.Fog(0x05060a, 18, 36);

    const camera = new THREE.PerspectiveCamera(50, 1, 0.1, 100);
    camera.position.set(6.2, 6.2, 6.2);

    const controls = new THREE.OrbitControls(camera, renderer.domElement);
    controls.enableDamping = true;
    controls.dampingFactor = 0.06;
    controls.minDistance = 4.2; controls.maxDistance = 18;

    // Lights — neon vibe
    const amb = new THREE.AmbientLight(0x87dfff, .35); scene.add(amb);
    const p1 = new THREE.PointLight(0x00e5ff, 2, 50); p1.position.set(6,8,10); scene.add(p1);
    const p2 = new THREE.PointLight(0xff00ff, 1.6, 50); p2.position.set(-8,-6,-6); scene.add(p2);

    // Floor glow
    const floorGeo = new THREE.PlaneGeometry(200,200);
    const floorMat = new THREE.MeshPhongMaterial({ color:0x0b0f1a, shininess: 40, specular: 0x112233 });
    const floor = new THREE.Mesh(floorGeo, floorMat);
    floor.rotation.x = -Math.PI/2; floor.position.y = -3.2; scene.add(floor);

    // Cube parameters
    const CUBE_SIZE = 3; // 3x3x3
    const GAP = 0.04; // tiny gap
    const UNIT = 1.0; // size of each cubie

    const COLORS = {
      U: 0xffffff, // white
      D: 0xffff00, // yellow
      L: 0xff8800, // orange
      R: 0xff0000, // red
      F: 0x00ff00, // green
      B: 0x0000ff  // blue
    };

    const neon = (hex) => new THREE.MeshStandardMaterial({ color: hex, metalness: .4, roughness: .22, emissive: hex, emissiveIntensity: .25 });
    const black = new THREE.MeshStandardMaterial({ color: 0x0d111a, metalness:.7, roughness:.5 });

    // Build a cubie with stickers
    function makeCubie(x, y, z){
      const base = new THREE.Mesh(new THREE.BoxGeometry(UNIT - GAP, UNIT - GAP, UNIT - GAP), black.clone());
      base.position.set(x, y, z);
      base.userData.home = { position: base.position.clone(), rotation: base.rotation.clone() };

      const stickers = [];
      const sGeo = new THREE.PlaneGeometry(UNIT*.86, UNIT*.86);

      // For each face, add a thin plane slightly above surface
      const addSticker = (axis, dir, color) => {
        const m = neon(color);
        const s = new THREE.Mesh(sGeo, m);
        s.renderOrder = 1;
        s.userData.face = axis;
        const offset = (UNIT/2) - (GAP/2) + 0.005;
        if(axis==='x'){
          s.position.set(dir*offset, 0, 0); s.rotation.y = Math.PI/2;
        } else if(axis==='y'){
          s.position.set(0, dir*offset, 0); s.rotation.x = -Math.PI/2;
        } else { // z
          s.position.set(0, 0, dir*offset);
        }
        base.add(s); stickers.push(s);
      };

      if(x === 1) addSticker('x', +1, COLORS.R);
      if(x === -1) addSticker('x', -1, COLORS.L);
      if(y === 1) addSticker('y', +1, COLORS.U);
      if(y === -1) addSticker('y', -1, COLORS.D);
      if(z === 1) addSticker('z', +1, COLORS.F);
      if(z === -1) addSticker('z', -1, COLORS.B);

      return base;
    }

    const cubies = [];
    for(let x=-1; x<=1; x++){
      for(let y=-1; y<=1; y++){
        for(let z=-1; z<=1; z++){
          const isCore = (x===0 && y===0 && z===0);
          if(isCore) continue; // hide physical core
          const c = makeCubie(x,y,z);
          cubies.push(c); scene.add(c);
        }
      }
    }

    // Helpers
    const eps = (v) => Math.round(v*100)/100; // limit float drift
    function snapCubie(c){
      c.position.set(eps(c.position.x), eps(c.position.y), eps(c.position.z));
      c.rotation.x = Math.round(c.rotation.x / (Math.PI/2)) * (Math.PI/2);
      c.rotation.y = Math.round(c.rotation.y / (Math.PI/2)) * (Math.PI/2);
      c.rotation.z = Math.round(c.rotation.z / (Math.PI/2)) * (Math.PI/2);
    }

    function getLayer(face){
      const E=0.01;
      if(face==='U') return cubies.filter(c=>c.position.y > 1-E);
      if(face==='D') return cubies.filter(c=>c.position.y < -1+E);
      if(face==='R') return cubies.filter(c=>c.position.x > 1-E);
      if(face==='L') return cubies.filter(c=>c.position.x < -1+E);
      if(face==='F') return cubies.filter(c=>c.position.z > 1-E);
      if(face==='B') return cubies.filter(c=>c.position.z < -1+E);
    }

    function rotateFace(face, prime=false, quarter=1){
      const group = new THREE.Group(); scene.add(group);
      const layer = getLayer(face);
      layer.forEach(c=>group.add(c));

      const axis = (face==='U'||face==='D')?'y':(face==='L'||face==='R')?'x':'z';
      const dir = (face==='U'||face==='R'||face==='F')?1:-1; // conventional direction
      const angle = dir * (prime?-1:1) * (Math.PI/2) * quarter;

      const step = Math.PI/2/12; // smooth 12 frames
      let turned = 0;
      return new Promise(resolve=>{
        const animateTurn = () => {
          const d = Math.sign(angle) * Math.min(Math.abs(step), Math.abs(angle-turned));
          group.rotateOnAxis(new THREE.Vector3(axis==='x', axis==='y', axis==='z'), d);
          turned += d;
          if(Math.abs(turned - angle) > 1e-4){ requestAnimationFrame(animateTurn); }
          else {
            // apply transform to children, then ungroup
            layer.forEach(c=>{
              c.applyMatrix4(group.matrix);
              snapCubie(c);
              scene.add(c);
            });
            scene.remove(group);
            resolve();
          }
        };
        animateTurn();
      });
    }

    // Save initial state for solved check
    const initial = cubies.map(c=>({ id:c.id, p:c.position.clone(), r:c.rotation.clone() }));
    function isSolved(){
      return cubies.every(c=>{
        const s = initial.find(i=>i.id===c.id);
        return s && c.position.distanceTo(s.p) < 1e-3 &&
               Math.abs(c.rotation.x - s.r.x) < 1e-3 &&
               Math.abs(c.rotation.y - s.r.y) < 1e-3 &&
               Math.abs(c.rotation.z - s.r.z) < 1e-3;
      });
    }

    // Renderer sizing
    function onResize(){
      const rect = canvas.getBoundingClientRect();
      const w = rect.width; const h = rect.height;
      renderer.setSize(w,h,false); camera.aspect = w/h; camera.updateProjectionMatrix();
    }
    new ResizeObserver(onResize).observe(document.body);
    onResize();

    // Animate
    const clock = new THREE.Clock();
    ;(function loop(){
      const t = clock.getElapsedTime();
      p1.intensity = 1.8 + Math.sin(t*1.2)*0.2;
      p2.intensity = 1.4 + Math.cos(t*1.0)*0.2;
      controls.update();
      renderer.render(scene, camera);
      requestAnimationFrame(loop);
    })();

    // UI handlers
    const toast = document.getElementById('toast');
    function showToast(msg){
      toast.textContent = msg; toast.style.display='block';
      clearTimeout(showToast.tid); showToast.tid = setTimeout(()=> toast.style.display='none', 900);
    }

    async function doMove(notation){
      const prime = notation.endsWith("'");
      const face = notation[0];
      await rotateFace(face, prime);
      showToast(`Movimiento ${notation}`);
      if(isSolved()) win();
    }

    document.getElementById('controls').addEventListener('click', (e)=>{
      const m = e.target.getAttribute('data-m');
      if(m) doMove(m);
    });
    document.getElementById('quick').addEventListener('click', (e)=>{
      const m = e.target.getAttribute('data-m');
      if(m) doMove(m);
    });

    async function scramble(n=20){
      const faces = ['U','D','L','R','F','B'];
      for(let i=0;i<n;i++){
        const f = faces[Math.floor(Math.random()*6)];
        const p = Math.random()<.5; await rotateFace(f, p);
      }
    }

    document.getElementById('scramble').addEventListener('click', ()=> scramble(25));
    document.getElementById('mix2').addEventListener('click', ()=> scramble(10));

    document.getElementById('reset').addEventListener('click', async ()=>{
      // naive reset: rotate back until solved by searching orientation —
      // For simplicity, rebuild scene to pristine state by reloading page
      location.reload();
    });

    document.getElementById('check').addEventListener('click', ()=>{
      if(isSolved()) win(); else showToast('Aún no. ¡Sigue!');
    });

    // Modal win
    const modal = document.createElement('div'); modal.className='modal';
    modal.innerHTML = `
      <div class="box">
        <h2>¡Cubo resuelto! 🎉</h2>
        <p><b>BerMatModZ</b> — Maestro del Rubik y del código.</p>
        <p>Proyectos: <b>⚡BerMat-Bot MD🔥</b>, <b>BerMat_Mods</b>, Bots de IA y Juegos.</p>
        <p>Contacto rápido: <a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener">Telegram Berrocal_mdz</a></p>
        <button class="btn ok">Seguir jugando</button>
      </div>`;
    document.body.appendChild(modal);
    modal.querySelector('.ok').addEventListener('click', ()=> modal.style.display='none');

    function win(){ modal.style.display='grid'; }

  })();
  </script></body>
</html>
