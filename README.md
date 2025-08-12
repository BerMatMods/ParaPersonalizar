
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
    let move = findBestMove('O'); // Intentar ganar
    if(move === null) move = findBestMove('X'); // Bloquear jugador
    if(move === null) move = emptyIndexes[Math.floor(Math.random() * emptyIndexes.length)];

    if(move !== null){
      board[move] = currentPlayer;
      updateBoard();

      const result = checkResult();

      if(result){
        gameActive = false;
        if(result === 'draw'){
          infoEl.textContent = "¡Empate! 😐";
        } else {
          infoEl.textContent = `¡Ganó el Bot (O)! 🎉`;
          highlightWinningCells(result);
        }
        return;
      }
      switchPlayer();
      infoEl.textContent = `Turno: ${playerNames[currentPlayer]} (${currentPlayer})`;
    }
  }

  // Buscar movimiento ganador o bloqueador
  function findBestMove(player) {
    for(let condition of winningConditions){
      const [a,b,c] = condition;
      const line = [board[a], board[b], board[c]];

      if(line.filter(cell => cell === player).length === 2 && line.includes('')){
        const emptyIndex = [a,b,c].find(idx => board[idx] === '');
        return emptyIndex;
      }
    }
    return null;
  }

  // Resaltar combinación ganadora
  function highlightWinningCells(winner) {
    for(let condition of winningConditions){
      const [a,b,c] = condition;
      if(board[a] === winner && board[b] === winner && board[c] === winner){
        const cells = boardEl.querySelectorAll('.cell');
        [a,b,c].forEach(i => {
          cells[i].style.boxShadow = winner === 'X' ?
            '0 0 20px 6px #ff3c6e' :
            '0 0 20px 6px #0fffc9';
          cells[i].style.transition = 'box-shadow 0.5s ease';
        });
        break;
      }
    }
  }

  // Reiniciar juego
  function resetGame() {
    board = ['', '', '', '', '', '', '', '', ''];
    currentPlayer = 'X';
    gameActive = true;
    updateBoard();
    infoEl.textContent = `Turno: ${playerNames[currentPlayer]} (${currentPlayer})`;
  }

  // Actualizar nombres jugadores desde inputs
  function updatePlayerNames(){
    const xName = playerXInput.value.trim();
    const oName = playerOInput.value.trim();

    playerNames.X = xName || 'Jugador X';
    if(mode === 'bot'){
      playerNames.O = 'Bot (O)';
    } else {
      playerNames.O = oName || 'Jugador O';
    }
    updateTurnInfo();
  }

  function updateTurnInfo() {
    if(!gameActive){
      return; // no cambiar mensaje en juego terminado
    }
    if(currentPlayer === 'O' && mode === 'bot'){
      infoEl.textContent = `Turno: Bot (O)`;
    } else {
      infoEl.textContent = `Turno: ${playerNames[currentPlayer]} (${currentPlayer})`;
    }
  }

  // Cambiar modo juego
  modeSelect.addEventListener('change', () => {
    mode = modeSelect.value;
    subtitle.textContent = mode === '2players' ? "Modo: 2 Jugadores" : "Modo: Jugar contra Bot";

    // Mostrar u ocultar input de jugador O
    if(mode === 'bot'){
      playerONameDiv.style.display = 'none';
      playerOInput.value = '';
    } else {
      playerONameDiv.style.display = 'flex';
    }

    updatePlayerNames();
    resetGame();
  });

  // Escuchar cambios en inputs para actualizar nombres
  playerXInput.addEventListener('input', () => {
    updatePlayerNames();
  });
  playerOInput.addEventListener('input', () => {
    if(mode === '2players') updatePlayerNames();
  });

  // Inicialización
  createBoard();
  updatePlayerNames();
  updateBoard();

  resetBtn.addEventListener('click', resetGame);

</script>

</body>
</html>
