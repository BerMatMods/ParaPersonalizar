
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>⚡ Tres en Raya - BerMat_Mods ⚡</title>
<style>
  body {
    background: radial-gradient(circle at top, #0f0f0f, #000);
    color: #fff;
    font-family: 'Poppins', sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
  }

  h1 {
    font-size: 2.5rem;
    text-shadow: 0 0 20px cyan, 0 0 40px blue;
    margin-bottom: 10px;
  }

  #gameMode {
    margin: 15px;
  }

  .board {
    display: grid;
    grid-template-columns: repeat(3, 120px);
    grid-template-rows: repeat(3, 120px);
    gap: 12px;
  }

  .cell {
    width: 120px;
    height: 120px;
    background: rgba(255,255,255,0.05);
    border-radius: 15px;
    box-shadow: 0 0 20px cyan;
    font-size: 3rem;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: all .3s;
  }

  .cell:hover {
    box-shadow: 0 0 25px #ff00ff, 0 0 50px #00ffff;
    transform: scale(1.05);
  }

  .winner {
    animation: glow 1s infinite alternate;
  }

  @keyframes glow {
    from { box-shadow: 0 0 20px lime; }
    to { box-shadow: 0 0 40px yellow; }
  }

  #message {
    margin-top: 20px;
    font-size: 1.5rem;
    text-shadow: 0 0 15px lime, 0 0 30px yellow;
  }

  .scoreboard {
    margin-top: 15px;
    display: flex;
    gap: 25px;
    font-size: 1.2rem;
    text-shadow: 0 0 15px cyan;
  }

  button {
    margin-top: 20px;
    padding: 10px 25px;
    border: none;
    border-radius: 10px;
    background: linear-gradient(90deg, cyan, blue);
    color: white;
    font-size: 1rem;
    cursor: pointer;
    box-shadow: 0 0 20px cyan;
    transition: all .3s;
  }

  button:hover {
    transform: scale(1.1);
    box-shadow: 0 0 30px #ff00ff;
  }
</style>
</head>
<body>
  <h1>⚡ Tres en Raya - BerMat_Mods ⚡</h1>

  <select id="gameMode">
    <option value="bot">Jugador vs Bot</option>
    <option value="2p">Jugador vs Jugador</option>
  </select>

  <div class="board" id="board"></div>

  <div id="message"></div>

  <div class="scoreboard">
    <div>👤 Jugador X: <span id="scoreX">0</span></div>
    <div>🤖 Jugador O: <span id="scoreO">0</span></div>
  </div>

  <button onclick="resetGame()">🔄 Reiniciar</button>

<script>
  const board = document.getElementById("board");
  const message = document.getElementById("message");
  const scoreXEl = document.getElementById("scoreX");
  const scoreOEl = document.getElementById("scoreO");
  const gameMode = document.getElementById("gameMode");

  let cells, currentPlayer, gameActive, scoreX = 0, scoreO = 0;

  function startGame() {
    board.innerHTML = "";
    currentPlayer = "X";
    gameActive = true;
    message.textContent = "👉 Turno de: " + currentPlayer;

    for (let i = 0; i < 9; i++) {
      const cell = document.createElement("div");
      cell.classList.add("cell");
      cell.addEventListener("click", () => handleClick(cell), { once: true });
      board.appendChild(cell);
    }
    cells = document.querySelectorAll(".cell");
  }

  function handleClick(cell) {
    if (!gameActive) return;
    cell.textContent = currentPlayer;
    cell.style.color = currentPlayer === "X" ? "cyan" : "yellow";
    if (checkWin(currentPlayer)) {
      endGame(false);
    } else if ([...cells].every(c => c.textContent !== "")) {
      endGame(true);
    } else {
      currentPlayer = currentPlayer === "X" ? "O" : "X";
      message.textContent = "👉 Turno de: " + currentPlayer;

      if (gameMode.value === "bot" && currentPlayer === "O") {
        botMove();
      }
    }
  }

  function botMove() {
    let emptyCells = [...cells].filter(c => c.textContent === "");
    if (emptyCells.length === 0) return;
    let move = emptyCells[Math.floor(Math.random() * emptyCells.length)];
    setTimeout(() => handleClick(move), 500);
  }

  function checkWin(player) {
    const winPatterns = [
      [0,1,2],[3,4,5],[6,7,8],
      [0,3,6],[1,4,7],[2,5,8],
      [0,4,8],[2,4,6]
    ];
    return winPatterns.some(pattern => 
      pattern.every(index => cells[index].textContent === player)
    );
  }

  function endGame(draw) {
    gameActive = false;
    if (draw) {
      message.textContent = "🤝 Empate! Grandes mentes piensan igual 💡";
    } else {
      message.textContent = "🎉 Felicitaciones " + currentPlayer + "! Eres un verdadero campeón 🏆✨";
      if (currentPlayer === "X") {
        scoreX++;
        scoreXEl.textContent = scoreX;
      } else {
        scoreO++;
        scoreOEl.textContent = scoreO;
      }
    }
  }

  function resetGame() {
    startGame();
  }

  startGame();
</script>
</body>
</html>
