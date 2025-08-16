
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>XO RGB — BerMat_Mods</title>

<!-- Fuentes llamativas -->
<link href="https://fonts.googleapis.com/css2?family=Audiowide&family=Russo+One&family=Orbitron:wght@400;600;800&display=swap" rel="stylesheet">

<style>
  :root{
    --glass: rgba(255,255,255,.06);
    --neon: #00ffe0;
    --gold: #ffd54a;
    --danger: #ff3d6e;
  }

  /* Fondo con halos y líneas */
  body{
    margin:0;
    min-height:100vh;
    display:grid;
    place-items:center;
    background:
      radial-gradient(1000px 600px at 20% -10%, #0ff2, transparent 60%),
      radial-gradient(900px 500px at 120% 10%, #f0f2, transparent 60%),
      linear-gradient(135deg,#0b0b10,#040408,#000);
    color:#fff;
    font-family: 'Orbitron', system-ui, sans-serif;
    overflow-x:hidden;
  }

  /* Contenedor centrado */
  .wrap{
    width:min(960px, 92vw);
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:14px;
  }

  /* Título con brillo */
  h1{
    font-family:'Russo One', sans-serif;
    letter-spacing:.5px;
    margin:8px 0 2px;
    font-size:clamp(1.6rem, 2.5vw + 1rem, 2.6rem);
    color:#eaffff;
    text-shadow:0 0 14px #00fff2, 0 0 40px #00d0ff;
  }

  /* Panel superior */
  .top{
    display:flex; gap:10px; flex-wrap:wrap; justify-content:center; align-items:center;
    background:var(--glass);
    border:1px solid #ffffff18;
    padding:10px 12px; border-radius:16px;
    backdrop-filter: blur(6px);
    box-shadow:0 0 30px #00fff222 inset;
  }
  .top input, .top select, .top button{
    font-family:'Audiowide', monospace;
    font-size:.95rem;
    padding:10px 12px;
    border-radius:12px; border:1px solid #ffffff25; outline:none;
    background:#0b0f13; color:#cfe;
  }
  .top input::placeholder{ color:#7ab;}
  .top button{
    cursor:pointer; font-weight:700; letter-spacing:.4px;
    background:linear-gradient(90deg, #00ffe0, #00aaff, #7a5cff);
    background-size:300% 100%;
    animation: btnwave 5s linear infinite;
    color:#001016; border:none; box-shadow:0 0 16px #00ffe055, 0 0 40px #6d74ff22 inset;
  }
  @keyframes btnwave{ 0%{background-position:0 0} 100%{background-position:300% 0}}

  /* Marcador */
  .score{
    display:flex; gap:18px; flex-wrap:wrap; justify-content:center;
    font-weight:700;
    text-shadow:0 0 10px #00fff280;
  }
  .badge{
    padding:8px 12px; border-radius:12px;
    background:#061017; border:1px solid #00ffff22;
  }

  /* Marco RGB del tablero */
  .board-wrap{
    position:relative;
    padding:18px;
    border-radius:24px;
    background:#070b10;
    box-shadow:
      0 0 30px #00ffe020 inset,
      0 0 60px #7a5cff18 inset,
      0 0 28px #00e5ff55;
  }
  .board-wrap::before{
    content:"";
    position:absolute; inset:-3px;
    border-radius:26px;
    padding:2px; background: linear-gradient(135deg, red, orange, yellow, lime, cyan, blue, magenta, red);
    filter:blur(6px) saturate(140%);
    -webkit-mask:
      linear-gradient(#000 0 0) content-box,
      linear-gradient(#000 0 0);
    -webkit-mask-composite: xor; mask-composite: exclude;
    animation: rainbow 6s linear infinite;
  }
  @keyframes rainbow{ to{ filter:hue-rotate(360deg) blur(6px) saturate(140%)}}

  /* Tablero */
  .board{
    width:min(520px, 92vw);
    aspect-ratio:1/1;
    display:grid;
    grid-template-columns:repeat(3,1fr);
    grid-template-rows:repeat(3,1fr);
    gap:14px;
  }

  /* Celdas */
  .cell{
    position:relative;
    display:grid; place-items:center;
    background:#0c1218;
    border-radius:18px;
    border:1px solid #ffffff14;
    box-shadow:
      0 0 20px #00ffe015 inset,
      0 0 20px #0099ff22,
      0 0 60px #7a5cff14 inset;
    cursor:pointer;
    transition: transform .18s ease, box-shadow .25s ease, background .25s ease;
    overflow:hidden;
  }
  .cell::after{ /* brillo cruzado */
    content:"";
    position:absolute; inset:-120%;
    background: linear-gradient(120deg, transparent 40%, #ffffff15 50%, transparent 60%);
    transform: rotate(12deg);
    transition: transform .6s ease;
  }
  .cell:hover{ transform:translateY(-2px) scale(1.02); box-shadow:0 0 26px #00ffe055, 0 0 80px #7a5cff33 inset;}
  .cell:hover::after{ transform: translate(30%, -30%) rotate(12deg); }

  /* XO estilizados con animación */
  .xo{
    font-family:'Russo One', sans-serif;
    font-size:clamp(2.6rem, 8vw, 5rem);
    letter-spacing:2px;
    filter: drop-shadow(0 0 8px #00ffe0) drop-shadow(0 0 18px #7a5cff);
    animation: pop .18s ease-out, chroma 4s linear infinite;
  }
  .xo.X{ color:#93fffb; text-shadow:0 0 20px #00fff2, 0 0 42px #00aaff; }
  .xo.O{ color:#ffda6e; text-shadow:0 0 20px #ffd54a, 0 0 42px #ff9d00; }

  @keyframes pop{ from{transform:scale(.6); opacity:.3} to{transform:scale(1); opacity:1}}
  @keyframes chroma{ 0%{filter:hue-rotate(0)} 100%{filter:hue-rotate(360deg)} }

  /* Mensaje ganador/empate al centro */
  .toast{
    position:fixed; inset:0; display:grid; place-items:center; pointer-events:none;
  }
  .toast .card{
    pointer-events:auto;
    padding:20px 28px;
    border-radius:18px;
    background:linear-gradient(180deg, #0c141cBB, #070c12EE);
    border:1px solid #ffffff25;
    box-shadow: 0 0 30px #00fff255;
    text-align:center;
    min-width:min(560px, 92vw);
    transform: translateY(-10px);
    animation: show .35s ease-out;
    backdrop-filter: blur(8px) saturate(130%);
  }
  .toast h2{
    margin:6px 0 8px;
    font-family:'Audiowide', monospace;
    font-size:clamp(1.3rem, 1.4rem + .7vw, 2rem);
  }
  .toast p{ margin:0; opacity:.9 }
  @keyframes show{ from{opacity:0; transform:translateY(-18px) scale(.96)} to{opacity:1; transform:translateY(0) scale(1)}}

  /* Botones */
  .actions{ display:flex; gap:10px; flex-wrap:wrap; justify-content:center }
  .btn{
    margin-top:4px;
    padding:10px 16px;
    border-radius:12px; border:none; cursor:pointer;
    font-family:'Audiowide', monospace;
    background:linear-gradient(90deg,#00ffe0,#00aaff,#7a5cff);
    color:#001018; font-weight:800;
    box-shadow:0 0 16px #00ffe055;
    background-size:300% 100%;
    animation: btnwave 5s linear infinite;
  }

  /* Confeti */
  .confetti{
    position:fixed; top:-10px; width:10px; height:10px;
    background:hsl(var(--h),100%,55%);
    left:var(--x,50vw);
    transform:translateX(-50%);
    opacity:.95; border-radius:2px;
    animation: fall 2.4s linear forwards;
  }
  @keyframes fall{
    90%{ transform: translateX(calc(-50% + var(--drift))) translateY(90vh) rotate(600deg)}
    100%{ transform: translateX(calc(-50% + var(--drift))) translateY(96vh) rotate(720deg); opacity:0}
  }

  /* Créditos al fondo */
  footer{
    margin-top:10px;
    font-size:.9rem;
    opacity:.8;
    text-align:center;
  }
</style>
</head>
<body>
  <div class="wrap">
    <h1>🔥 XO RGB Futurista — BerMat_Mods</h1>

    <div class="top">
      <select id="mode">
        <option value="bot">Jugador vs Bot (IA)</option>
        <option value="pvp">Jugador vs Jugador</option>
      </select>
      <input id="nameX" placeholder="Nombre Jugador X" />
      <input id="nameO" placeholder="Nombre Jugador O / Bot" />
      <button id="start" class="btn">Iniciar</button>
    </div>

    <div class="score">
      <div class="badge" id="scoreX">X: 0</div>
      <div class="badge" id="turn">Turno: —</div>
      <div class="badge" id="scoreO">O: 0</div>
    </div>

    <div class="board-wrap">
      <div id="board" class="board"></div>
    </div>

    <!-- Toast de mensajes -->
    <div id="toast" class="toast" style="display:none;">
      <div class="card">
        <h2 id="toastTitle">¡Victoria!</h2>
        <p id="toastMsg">Mensaje</p>
        <div class="actions">
          <button id="again" class="btn">Jugar de nuevo</button>
        </div>
      </div>
    </div>

    <footer>
      ⚡ Creado por <strong>Anth'Zz Berrocal</strong> — <strong>BerMat_Mods</strong> ⚡
    </footer>
  </div>

  <!-- Sonido de aplausos -->
  <audio id="sfxWin" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_2c2f5f0c33.mp3?filename=short-crowd-cheer-6713.mp3"></audio>

<script>
  const boardEl = document.getElementById('board');
  const modeEl = document.getElementById('mode');
  const nameXEl = document.getElementById('nameX');
  const nameOEl = document.getElementById('nameO');
  const startBtn = document.getElementById('start');

  const turnEl = document.getElementById('turn');
  const scoreXEl = document.getElementById('scoreX');
  const scoreOEl = document.getElementById('scoreO');

  const toast = document.getElementById('toast');
  const toastTitle = document.getElementById('toastTitle');
  const toastMsg = document.getElementById('toastMsg');
  const againBtn = document.getElementById('again');
  const sfxWin = document.getElementById('sfxWin');

  let board = Array(9).fill("");
  let current = "X";
  let scores = { X:0, O:0 };
  let playing = false;
  let vsBot = true;
  let names = { X:"Jugador X", O:"Bot" };

  startBtn.addEventListener('click', start);
  againBtn.addEventListener('click', () => { hideToast(); reset(false); });

  function start(){
    vsBot = (modeEl.value === 'bot');
    names.X = nameXEl.value.trim() || "Jugador X";
    names.O = (vsBot ? (nameOEl.value.trim() || "Bot") : (nameOEl.value.trim() || "Jugador O"));
    reset(true);
  }

  function reset(fresh){
    board = Array(9).fill("");
    current = "X";
    playing = true;
    turnEl.textContent = `Turno: ${names[current]} (${current})`;
    if(fresh){ /* mantener scores */ }
    render();
  }

  function render(){
    boardEl.innerHTML = "";
    for(let i=0;i<9;i++){
      const cell = document.createElement('div');
      cell.className = 'cell';
      cell.dataset.idx = i;
      const val = board[i];
      if(val){
        const span = document.createElement('span');
        span.className = `xo ${val}`;
        span.textContent = val;
        cell.appendChild(span);
      }
      cell.addEventListener('click', onCell);
      boardEl.appendChild(cell);
    }
    scoreXEl.textContent = `X: ${scores.X} — ${names.X}`;
    scoreOEl.textContent = `${names.O} — O: ${scores.O}`;
  }

  function onCell(e){
    if(!playing) return;
    const i = +e.currentTarget.dataset.idx;
    if(board[i]) return;

    place(i, current);

    if(checkWin(board, current)){
      endRound(current, `${fraseWin()} ${names[current]} (${current})`);
      return;
    }
    if(full(board)){
      endRound(null, "🤝 ¡Empate épico! Dos mentes brillantes en equilibrio.");
      return;
    }

    swap();
    if(vsBot && current === "O" && playing){
      setTimeout(botTurn, 320);
    }
  }

  function place(i, p){
    board[i] = p;
    haptic();
    glowCell(i);
    render();
  }

  function glowCell(i){
    const c = boardEl.children[i];
    c.classList.add('glowOnce');
    c.animate(
      [{boxShadow: '0 0 6px #fff'}, {boxShadow:'0 0 26px #00ffe0'}, {boxShadow:'0 0 6px #fff'}],
      {duration:420, easing:'ease-out'}
    );
  }

  function swap(){
    current = (current === "X") ? "O" : "X";
    turnEl.textContent = `Turno: ${names[current]} (${current})`;
  }

  function endRound(winner, msg){
    playing = false;
    if(winner){
      scores[winner]++; sfxWin.currentTime = 0; sfxWin.play();
      confettiBurst();
      toastTitle.textContent = "🎉 ¡Victoria!";
      toastMsg.textContent = `${msg}. Sigue así, disciplina y mente fría.`;
    }else{
      toastTitle.textContent = "🤝 ¡Empate!";
      toastMsg.textContent = msg;
    }
    showToast();
    render();
  }

  function showToast(){ toast.style.display = "grid"; }
  function hideToast(){ toast.style.display = "none"; }

  /* --------- IA: Minimax para O --------- */
  function botTurn(){
    const idx = bestMove(board);
    place(idx, "O");
    if(checkWin(board,"O")){
      endRound("O", `${fraseWin()} ${names.O} (O)`);
      return;
    }
    if(full(board)){
      endRound(null, "🤝 ¡Empate! Pulsos de energía en sintonía.");
      return;
    }
    swap();
  }

  function bestMove(b){
    // Si tablero vacío, elegir centro
    if(b.every(v=>!v)) return 4;

    let bestScore = -Infinity, move = 0;
    for(let i=0;i<9;i++){
      if(!b[i]){
        b[i] = "O";
        let score = minimax(b, 0, false);
        b[i] = "";
        if(score > bestScore){ bestScore = score; move = i; }
      }
    }
    return move;
  }

  const scoresMap = { O: 10, X: -10, T: 0 };

  function minimax(b, depth, isMax){
    const winO = checkWin(b,"O");
    const winX = checkWin(b,"X");
    if(winO) return scoresMap.O - depth;
    if(winX) return scoresMap.X + depth;
    if(full(b)) return scoresMap.T;

    if(isMax){
      let best = -Infinity;
      for(let i=0;i<9;i++){
        if(!b[i]){
          b[i] = "O";
          best = Math.max(best, minimax(b, depth+1, false));
          b[i] = "";
        }
      }
      return best;
    }else{
      let best = Infinity;
      for(let i=0;i<9;i++){
        if(!b[i]){
          b[i] = "X";
          best = Math.min(best, minimax(b, depth+1, true));
          b[i] = "";
        }
      }
      return best;
    }
  }

  /* --------- Utils --------- */
  function lines(){
    return [
      [0,1,2],[3,4,5],[6,7,8],
      [0,3,6],[1,4,7],[2,5,8],
      [0,4,8],[2,4,6]
    ];
  }
  function checkWin(b, p){
    return lines().some(l => l.every(i => b[i]===p));
  }
  function full(b){ return b.every(v => !!v); }

  function haptic(){
    if(navigator.vibrate) navigator.vibrate(55);
  }

  function fraseWin(){
    const f = [
      "Campeón total 💎",
      "Mente fría, manos de acero 🧠⚡",
      "Estrategia perfecta 🏆",
      "Leyenda del tablero 👑",
      "Flujo imparable 🚀"
    ];
    return f[Math.floor(Math.random()*f.length)];
  }

  function confettiBurst(){
    for(let i=0;i<80;i++){
      const c = document.createElement('div');
      c.className = 'confetti';
      c.style.setProperty('--h', Math.floor(Math.random()*360));
      c.style.setProperty('--x', Math.random()*100 + 'vw');
      c.style.setProperty('--drift', (Math.random()*160 - 80) + 'px');
      document.body.appendChild(c);
      setTimeout(()=>c.remove(), 2600);
    }
  }

  // Autoinit
  start();
</script>
</body>
</html>
