
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Juego XO - BerMatMods</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');

  * {
    box-sizing: border-box;
  }

  body {
    margin: 0; 
    background: linear-gradient(135deg, #1f1c2c, #928dab);
    font-family: 'Poppins', sans-serif;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 20px 15px 60px 15px;
  }

  h1 {
    margin-bottom: 5px;
    font-size: 3.5rem;
    letter-spacing: 2px;
    text-shadow: 0 0 10px #e0aaff;
    user-select: none;
  }

  h2 {
    margin-top: 0;
    font-weight: 500;
    font-size: 1.5rem;
    margin-bottom: 20px;
    user-select: none;
  }

  #mode-select {
    margin-bottom: 15px;
  }

  select {
    font-size: 1.2rem;
    padding: 8px 15px;
    border-radius: 10px;
    border: none;
    background: #442266;
    color: #fff;
    cursor: pointer;
    box-shadow: 0 0 8px #a37cff;
    transition: background-color 0.3s ease;
  }
  select:hover {
    background: #6a3ea1;
  }

  #name-inputs {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
    flex-wrap: wrap;
    justify-content: center;
  }

  #name-inputs > div {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  label {
    font-weight: 600;
    margin-bottom: 5px;
  }

  input[type="text"] {
    padding: 8px 12px;
    font-size: 1.1rem;
    border-radius: 8px;
    border: none;
    outline: none;
    box-shadow: inset 0 0 8px #6b4dbb;
    width: 180px;
    color: #333;
  }
  input[type="text"]:focus {
    box-shadow: 0 0 10px #bb33ff;
  }

  #board {
    display: grid;
    grid-template-columns: repeat(3, 120px);
    grid-template-rows: repeat(3, 120px);
    gap: 15px;
    user-select: none;
  }

  .cell {
    background: #2e2a44;
    border-radius: 15px;
    box-shadow: inset 0 0 10px #4a3f77;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 5rem;
    font-weight: 900;
    color: #cfa4ff;
    position: relative;
    transition: background-color 0.3s ease;
  }

  .cell:hover:not(.disabled) {
    background: #5e4dbb;
  }

  /* Animación parpadeo para X */
  .x {
    color: #ff5c8d;
    animation: blinkX 1.2s infinite alternate;
    text-shadow:
      0 0 5px #ff5c8d,
      0 0 15px #ff1f6a,
      0 0 30px #ff004c;
  }
  @keyframes blinkX {
    0%, 100% {opacity: 1;}
    50% {opacity: 0.5;}
  }

  /* Animación parpadeo para O */
  .o {
    color: #4affca;
    animation: blinkO 1.2s infinite alternate;
    text-shadow:
      0 0 5px #4affca,
      0 0 15px #00f6d4,
      0 0 30px #00c9a4;
  }
  @keyframes blinkO {
    0%, 100% {opacity: 1;}
    50% {opacity: 0.5;}
  }

  .disabled {
    pointer-events: none;
  }

  #info {
    margin-top: 25px;
    font-size: 1.4rem;
    min-height: 40px;
    user-select: none;
    text-align: center;
    padding: 10px 20px;
    background: rgba(0,0,0,0.3);
    border-radius: 12px;
    box-shadow: 0 0 12px #9255ff88;
  }

  #reset-btn {
    margin-top: 20px;
    font-size: 1.3rem;
    background: #bb33ff;
    border: none;
    padding: 12px 28px;
    color: white;
    font-weight: 700;
    border-radius: 25px;
    cursor: pointer;
    box-shadow: 0 0 15px #bb33ffaa;
    transition: background-color 0.3s ease;
  }
  #reset-btn:hover {
    background: #dd44ff;
  }

  /* Pie de página con marca y redes */
  footer {
    position: fixed;
    bottom: 0; left: 0; right: 0;
    background: #2e2a44cc;
    color: #ddaaff;
    font-size: 0.9rem;
    padding: 8px 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    user-select: none;
    box-shadow: 0 -3px 10px #bb33ffaa;
  }
  footer .brand {
    font-weight: 700;
    font-size: 1.2rem;
    letter-spacing: 1.5px;
    text-shadow: 0 0 6px #bb33ff;
  }
  footer .info {
    flex: 1;
    text-align: center;
  }
  footer .socials a {
    color: #ddaaff;
    text-decoration: none;
    margin-left: 15px;
    font-weight: 700;
    transition: color 0.3s ease;
  }
  footer .socials a:hover {
    color: #ff77ff;
  }

</style>
</head>
<body>

<h1>🕹️ Tic Tac Toe (XO)</h1>
<h2 id="subtitle">Modo: 2 Jugadores</h2>

<div id="mode-select">
  <label for="mode">Selecciona modo: </label>
  <select id="mode" aria-label="Selecciona modo de juego">
    <option value="2players" selected>2 Jugadores</option>
    <option value="bot">Jugar contra Bot</option>
  </select>
</div>

<div id="name-inputs" aria-label="Nombres de jugadores">
  <div id="playerX-name-div">
    <label for="playerX-name">Nombre jugador X:</label>
    <input type="text" id="playerX-name" placeholder="Jugador X" maxlength="12" />
  </div>
  <div id="playerO-name-div">
    <label for="playerO-name">Nombre jugador O:</label>
    <input type="text" id="playerO-name" placeholder="Jugador O" maxlength="12" />
  </div>
</div>

<div id="board" aria-label="Tablero de Tic Tac Toe" role="grid" tabindex="0">
  <!-- Celdas generadas por JS -->
</div>

<div id="info" aria-live="polite">Turno: Jugador X</div>
<button id="reset-btn" aria-label="Reiniciar juego">Reiniciar Juego</button>

<footer>
  <div class="brand">⚡ BerMatMods ⚡</div>
  <div class="info">Creado por <strong>Anth'Zz Berrocal</strong> | Andahuaylas</div>
  <div class="socials" aria-label="Redes sociales de BerMatMods">
    <a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener noreferrer" title="Telegram">Telegram</a>
    <a href="https://github.com/BerMatMods" target="_blank" rel="noopener noreferrer" title="GitHub">GitHub</a>
    <a href="https://wa.me/51937556459" target="_blank" rel="noopener noreferrer" title="WhatsApp">WhatsApp</a>
  </div>
</footer>

<script>
  const boardEl = document.getElementById('board');
  const infoEl = document.getElementById('info');
  const resetBtn = document.getElementById('reset-btn');
  const modeSelect = document.getElementById('mode');
  const subtitle = document.getElementById('subtitle');
  const playerXInput = document.getElementById('playerX-name');
  const playerOInput = document.getElementById('playerO-name');
  const playerONameDiv = document.getElementById('playerO-name-div');

  let board = ['', '', '', '', '', '', '', '', ''];
  let currentPlayer = 'X';
  let gameActive = true;
  let mode = '2players'; // o 'bot'

  // Nombres jugadores (por defecto)
  let playerNames = {
    X: 'Jugador X',
    O: 'Jugador O'
  };

  // Posibles combinaciones ganadoras
  const winningConditions = [
    [0,1,2],[3,4,5],[6,7,8], // filas
    [0,3,6],[1,4,7],[2,5,8], // columnas
    [0,4,8],[2,4,6]          // diagonales
  ];

  // Crear las celdas del tablero
  function createBoard() {
    boardEl.innerHTML = '';
    for(let i=0; i<9; i++){
      const cell = document.createElement('div');
      cell.classList.add('cell');
      cell.setAttribute('data-cell-index', i);
      cell.setAttribute('role', 'button');
      cell.setAttribute('tabindex', 0);
      cell.addEventListener('click', () => handleCellClick(i));
      cell.addEventListener('keydown', (e) => {
        if(e.key === 'Enter' || e.key === ' ') {
          e.preventDefault();
          handleCellClick(i);
        }
      });
      boardEl.appendChild(cell);
    }
  }

  // Actualiza el tablero visual según array board
  function updateBoard() {
    const cells = boardEl.querySelectorAll('.cell');
    cells.forEach((cell, i) => {
      cell.textContent = board[i];
      cell.classList.remove('x','o','disabled');
      if(board[i] === 'X') {
        cell.classList.add('x', 'disabled');
      } else if(board[i] === 'O') {
        cell.classList.add('o', 'disabled');
      }
      else {
        cell.classList.remove('disabled');
      }
    });
  }

  // Comprobar ganador o empate
  function checkResult() {
    for(let condition of winningConditions){
      const [a,b,c] = condition;
      if(board[a] && board[a] === board[b] && board[a] === board[c]){
        return board[a]; // X u O ganador
      }
    }
    if(!board.includes('')) return 'draw'; // empate
    return null;
  }

  // Cambiar jugador
  function switchPlayer() {
    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    infoEl.textContent = `Turno: ${playerNames[currentPlayer]} (${currentPlayer})`;
  }

  // Maneja el click en celda
  function handleCellClick(index) {
    if(!gameActive || board[index]) return;

    board[index] = currentPlayer;
    updateBoard();

    const result = checkResult();

    if(result){
      gameActive = false;
      if(result === 'draw'){
        infoEl.textContent = "¡Empate! 😐";
      } else {
        infoEl.textContent = `¡Ganó ${playerNames[result]} (${result})! 🎉`;
        highlightWinningCells(result);
      }
      return;
    }

    switchPlayer();

    if(mode === 'bot' && currentPlayer === 'O' && gameActive){
      infoEl.textContent = `Turno: Bot (O)`;
      setTimeout(botMove, 700);
    }
  }

  // Bot elige movimiento simple
  function botMove() {
    if(!gameActive) return;
    const emptyIndexes = board
      .map((val, idx) => val === '' ? idx : null)
      .filter(i => i !== null);

    // Estrategia simple: ganar, bloquear, aleatorio
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Juego XO - BerMatMods</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');

  * {
    box-sizing: border-box;
  }

  body {
    margin: 0; 
    font-family: 'Poppins', sans-serif;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 20px 15px 100px 15px;
    background: var(--bg-gradient);
    transition: background 0.8s ease;
  }

  /* Temas neón */
  :root {
    --bg-gradient: linear-gradient(135deg, #1f1c2c, #928dab);
    --color-x: #ff5c8d;
    --color-o: #4affca;
    --color-x-shadow: #ff004c;
    --color-o-shadow: #00c9a4;
    --btn-bg: #bb33ff;
    --btn-bg-hover: #dd44ff;
    --board-bg: #2e2a44;
    --board-shadow: #4a3f77;
    --info-bg: rgba(0,0,0,0.3);
    --info-shadow: #9255ff88;
    --modal-bg: rgba(25,0,50,0.95);
  }

  /* Tema 2 (azul) */
  body.theme-blue {
    --bg-gradient: linear-gradient(135deg, #0a2540, #355375);
    --color-x: #3ec6ff;
    --color-o: #00ffd1;
    --color-x-shadow: #0099ff;
    --color-o-shadow: #00cca3;
    --btn-bg: #007acc;
    --btn-bg-hover: #0099ff;
    --board-bg: #16324f;
    --board-shadow: #245d8c;
    --info-bg: rgba(0, 30, 60, 0.5);
    --info-shadow: #007acc88;
    --modal-bg: rgba(0,20,40,0.95);
  }

  /* Tema 3 (rosa) */
  body.theme-pink {
    --bg-gradient: linear-gradient(135deg, #350a3f, #7e2f65);
    --color-x: #ff3e96;
    --color-o: #ff63c3;
    --color-x-shadow: #d9006e;
    --color-o-shadow: #e600a3;
    --btn-bg: #d81e88;
    --btn-bg-hover: #ff3e96;
    --board-bg: #502a4a;
    --board-shadow: #7d3b6e;
    --info-bg: rgba(60,20,60,0.5);
    --info-shadow: #d81e8888;
    --modal-bg: rgba(40,10,40,0.95);
  }

  h1 {
    margin-bottom: 5px;
    font-size: 3.5rem;
    letter-spacing: 2px;
    user-select: none;
    text-shadow:
      0 0 8px var(--color-x),
      0 0 20px var(--color-x-shadow);
  }

  h2 {
    margin-top: 0;
    font-weight: 500;
    font-size: 1.5rem;
    margin-bottom: 15px;
    user-select: none;
    color: #ddd;
    text-shadow: 0 0 5px var(--btn-bg);
  }

  #mode-select {
    margin-bottom: 15px;
  }

  label {
    font-weight: 600;
    margin-bottom: 5px;
  }

  select, input[type="text"] {
    font-size: 1.2rem;
    padding: 8px 15px;
    border-radius: 12px;
    border: none;
    outline: none;
    background: var(--board-bg);
    color: #fff;
    box-shadow: 0 0 12px var(--btn-bg);
    transition: box-shadow 0.3s ease;
  }
  select:hover, input[type="text"]:focus {
    box-shadow: 0 0 20px var(--btn-bg);
  }

  #name-inputs {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
    flex-wrap: wrap;
    justify-content: center;
  }

  #name-inputs > div {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  #board {
    display: grid;
    grid-template-columns: repeat(3, 130px);
    grid-template-rows: repeat(3, 130px);
    gap: 18px;
    user-select: none;
  }

  .cell {
    background: var(--board-bg);
    border-radius: 20px;
    box-shadow:
      inset 0 0 12px var(--board-shadow),
      0 0 15px transparent;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 6rem;
    font-weight: 900;
    color: var(--color-x);
    position: relative;
    transition: background-color 0.3s ease, box-shadow 0.4s ease;
  }

  .cell:hover:not(.disabled) {
    background: #5533aa;
    box-shadow:
      0 0 25px var(--btn-bg),
      0 0 40px var(--btn-bg);
  }

  /* Animación parpadeo para X */
  .x {
    color: var(--color-x);
    animation: blinkX 1.2s infinite alternate;
    text-shadow:
      0 0 8px var(--color-x),
      0 0 25px var(--color-x-shadow),
      0 0 50px var(--color-x-shadow);
  }
  @keyframes blinkX {
    0%, 100% {opacity: 1;}
    50% {opacity: 0.5;}
  }

  /* Animación parpadeo para O */
  .o {
    color: var(--color-o);
    animation: blinkO 1.2s infinite alternate;
    text-shadow:
      0 0 8px var(--color-o),
      0 0 25px var(--color-o-shadow),
      0 0 50px var(--color-o-shadow);
  }
  @keyframes blinkO {
    0%, 100% {opacity: 1;}
    50% {opacity: 0.5;}
  }

  .disabled {
    pointer-events: none;
  }

  #info {
    margin-top: 25px;
    font-size: 1.4rem;
    min-height: 40px;
    user-select: none;
    text-align: center;
    padding: 12px 25px;
    background: var(--info-bg);
    border-radius: 16px;
    box-shadow: 0 0 20px var(--info-shadow);
    letter-spacing: 1.1px;
  }

  #reset-btn {
    margin-top: 20px;
    font-size: 1.3rem;
    background: var(--btn-bg);
    border: none;
    padding: 14px 34px;
    color: white;
    font-weight: 700;
    border-radius: 30px;
    cursor: pointer;
    box-shadow: 0 0 20px var(--btn-bg);
    transition: background-color 0.3s ease, box-shadow 0.4s ease;
  }
  #reset-btn:hover {
    background: var(--btn-bg-hover);
    box-shadow:
      0 0 30px var(--btn-bg-hover),
      0 0 60px var(--btn-bg-hover);
  }

  /* Botón cambiar tema */
  #theme-btn {
    margin-top: 15px;
    font-size: 1rem;
    background: transparent;
    border: 2px solid var(--btn-bg);
    padding: 8px 20px;
    border-radius: 20px;
    color: var(--btn-bg);
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  #theme-btn:hover {
    background: var(--btn-bg);
    color: #fff;
    box-shadow: 0 0 20px var(--btn-bg);
  }

  /* Pie de página con marca y redes */
  footer {
    position: fixed;
    bottom: 0; left: 0; right: 0;
    background: var(--board-bg);
    color: #ddaaff;
    font-size: 0.9rem;
    padding: 10px 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    user-select: none;
    box-shadow: 0 -3px 15px var(--btn-bg);
  }
  footer .brand {
    font-weight: 700;
    font-size: 1.2rem;
    letter-spacing: 1.5px;
    text-shadow: 0 0 10px var(--btn-bg);
  }
  footer .info {
    flex: 1;
    text-align: center;
  }
  footer .socials a {
    color: #ddaaff;
    text-decoration: none;
    margin-left: 15px;
    font-weight: 700;
    transition: color 0.3s ease;
  }
  footer .socials a:hover {
    color: var(--btn-bg-hover);
    text-shadow: 0 0 10px var(--btn-bg-hover);
  }

  /* Modal pantalla final */
  #result-modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0.8);
    background: var(--modal-bg);
    border-radius: 25px;
    padding: 35px 40px;
    box-shadow:
      0 0 30px var(--btn-bg),
      0 0 70px var(--btn-bg);
    color: #fff;
    text-align: center;
    font-size: 2.1rem;
    font-weight: 700;
    user-select: none;
    z-index: 200;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.4s ease, transform 0.4s ease;
    max-width: 90vw;
  }

  #result-modal.active {
    opacity: 1;
    pointer-events: auto;
    transform: translate(-50%, -50%) scale(1);
  }

  #result-modal .message {
    margin-bottom: 20px;
    text-shadow:
      0 0 12px var(--btn-bg),
      0 0 25px var(--btn-bg);
  }

  #result-modal .buttons {
    margin-top: 15px;
    display: flex;
    justify-content: center;
    gap: 25px;
    flex-wrap: wrap;
  }

  #result-modal button, #result-modal a.button-link {
    font-size: 1.2rem;
    font-weight: 700;
    padding: 12px 30px;
    border-radius: 30px;
    border: none;
    cursor: pointer;
    background: var(--btn-bg);
    color: white;
    box-shadow: 0 0 20px var(--btn-bg);
    transition: background-color 0.3s ease, box-shadow 0.4s ease;
    text-decoration: none;
    user-select: none;
  }
  #result-modal button:hover, #result-modal a.button-link:hover {
    background: var(--btn-bg-hover);
    box-shadow:
      0 0 30px var(--btn-bg-hover),
      0 0 60px var(--btn-bg-hover);
  }

  /* Redes sociales en modal */
  #result-modal .socials {
    margin-top: 25px;
    font-size: 1rem;
  }
  #result-modal .socials a {
    color: var(--btn-bg);
    margin: 0 12px;
    font-weight: 700;
    text-decoration: none;
    transition: color 0.3s ease;
  }
  #result-modal .socials a:hover {
    color: var(--btn-bg-hover);
    text-shadow: 0 0 15px var(--btn-bg-hover);
  }

  /* Responsive pequeño */
  @media (max-width: 450px) {
    #board {
      grid-template-columns: repeat(3, 90px);
      grid-template-rows: repeat(3, 90px);
      gap: 12px;
    }
    .cell {
      font-size: 4rem;
      border-radius: 15px;
    }
    #reset-btn {
      font-size: 1.1rem;
      padding: 10px 24px;
    }
    #result-modal {
      font-size: 1.5rem;
      padding: 25px 30px;
    }
    #result-modal button, #result-modal a.button-link {
      font-size: 1rem;
      padding: 10px 24px;
    }
  }
</style>
</head>
<body>

<h1>🕹️ Tic Tac Toe (XO)</h1>
<h2 id="subtitle">Modo: 2 Jugadores</h2>

<div id="mode-select">
  <label for="mode">Selecciona modo: </label>
  <select id="mode" aria-label="Selecciona modo de juego">
    <option value="2players" selected>2 Jugadores</option>
    <option value="bot">Jugar contra Bot</option>
  </select>
</div>

<div id="name-inputs" aria-label="Nombres de jugadores">
  <div id="playerX-name-div">
    <label for="playerX-name">Nombre jugador X:</label>
    <input type="text" id="playerX-name" placeholder="Jugador X" maxlength="12" />
  </div>
  <div id="playerO-name-div">
    <label for="playerO-name">Nombre jugador O:</label>
    <input type="text" id="playerO-name" placeholder="Jugador O" maxlength="12" />
  </div>
</div>

<div id="board" aria-label="Tablero de Tic Tac Toe" role="grid" tabindex="0">
  <!-- Celdas generadas por JS -->
</div>

<div id="info" aria-live="polite">Turno: Jugador X</div>
<button id="reset-btn" aria-label="Reiniciar juego">Reiniciar Juego</button>
<button id="theme-btn" aria-label="Cambiar tema de colores">Cambiar Tema 🎨</button>

<footer>
  <div class="brand">⚡ BerMatMods ⚡</div>
  <div class="info">Creado por <strong>Anth'Zz Berrocal</strong> | Andahuaylas</div>
  <div class="socials" aria-label="Redes sociales de BerMatMods">
    <a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener noreferrer" title="Telegram">Telegram</a>
    <a href="https://github.com/BerMatMods" target="_blank" rel="noopener noreferrer" title="GitHub">GitHub</a>
    <a href="https://wa.me/51937556459" target="_blank" rel="noopener noreferrer" title="WhatsApp">WhatsApp</a>
  </div>
</footer>

<!-- Modal resultado -->
<div id="result-modal" role="dialog" aria-modal="true" aria-labelledby="result-message" aria-describedby="result-description">
  <div class="message" id="result-message">¡Ganó Jugador X!</div>
  <div class="buttons">
    <button id="play-again-btn" aria-label="Jugar de nuevo">Jugar de nuevo</button>
    <a href="#footer" class="button-link" id="show-socials-btn" aria-label="Mostrar redes sociales">Ver redes</a>
  </div>
  <div class="socials" id="modal-socials" aria-label="Redes sociales de BerMatMods">
    <a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener noreferrer" title="Telegram">Telegram</a>
    <a href="https://github.com/BerMatMods" target="_blank" rel="noopener noreferrer" title="GitHub">GitHub</a>
    <a href="https://wa.me/51937556459" target="_blank" rel="noopener noreferrer" title="WhatsApp">WhatsApp</a>
  </div>
</div>

<script>
  const boardEl = document.getElementById('board');
  const infoEl = document.getElementById('info');
  const resetBtn = document.getElementById('reset-btn');
  const modeSelect = document.getElementById('mode');
  const subtitle = document.getElementById('subtitle');
  const playerXInput = document.getElementById('playerX-name');
  const playerOInput = document.getElementById('playerO-name');
  const playerONameDiv = document.getElementById('playerO-name-div');
  const resultModal = document.getElementById('result-modal');
  const resultMessage = document.getElementById('result-message');
  const playAgainBtn = document.getElementById('play-again-btn');
  const themeBtn = document.getElementById('theme-btn');

  let board = ['', '', '', '', '', '', '', '', ''];
  let currentPlayer = 'X';
  let gameActive = true;
  let mode = '2players'; // o 'bot'
