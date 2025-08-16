
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Juego XO - BerMat_Mods</title>
  <style>
    body {
      background: linear-gradient(135deg, #0f0f0f, #1e1e1e, #000);
      color: #fff;
      font-family: 'Orbitron', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    h1 {
      font-size: 2.5em;
      color: #00ffcc;
      text-shadow: 0 0 20px #00ffcc;
      margin-bottom: 15px;
    }

    #players {
      margin-bottom: 15px;
    }

    #players input {
      padding: 8px;
      margin: 5px;
      border: none;
      border-radius: 8px;
      font-size: 1em;
      outline: none;
      text-align: center;
    }

    .board {
      display: grid;
      grid-template-columns: repeat(3, 120px);
      grid-template-rows: repeat(3, 120px);
      gap: 10px;
    }

    .cell {
      background: #222;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3em;
      font-weight: bold;
      color: #00ffcc;
      border-radius: 15px;
      cursor: pointer;
      box-shadow: 0 0 15px #00ffcc;
      transition: transform 0.2s, box-shadow 0.3s;
    }

    .cell.taken {
      cursor: not-allowed;
    }

    .cell:hover {
      transform: scale(1.1);
    }

    .cell.glow {
      animation: glow 0.6s ease-out;
    }

    @keyframes glow {
      0% { box-shadow: 0 0 5px #fff; }
      50% { box-shadow: 0 0 25px #00ffcc; }
      100% { box-shadow: 0 0 5px #fff; }
    }

    #message {
      margin-top: 20px;
      font-size: 1.4em;
      text-align: center;
      padding: 15px;
      border-radius: 12px;
      background: rgba(0, 255, 200, 0.15);
      display: none;
      animation: fadeIn 1s;
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(-10px);}
      to {opacity: 1; transform: translateY(0);}
    }

    #score {
      margin-top: 15px;
      font-size: 1.2em;
      color: #ffcc00;
      text-shadow: 0 0 10px #ffcc00;
    }

    #credits {
      position: absolute;
      bottom: 10px;
      font-size: 0.9em;
      color: #888;
    }

    button {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      font-size: 1em;
      cursor: pointer;
      background: #00ffcc;
      color: #000;
      font-weight: bold;
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.1);
      background: #ffcc00;
    }
  </style>
</head>
<body>
  <h1>🔥 Juego XO - BerMat_Mods ⚡</h1>

  <div id="players">
    <input type="text" id="playerX" placeholder="Jugador X" />
    <input type="text" id="playerO" placeholder="Jugador O o Bot" />
    <button onclick="startGame()">Iniciar Juego</button>
  </div>

  <div class="board" id="board"></div>

  <div id="message"></div>
  <div id="score"></div>

  <div id="credits">⚡ Creado por: <b>BerMat_Mods</b> 🔥</div>

  <audio id="applause" src="https://www.soundjay.com/human/applause-1.mp3"></audio>

  <script>
    const boardElement = document.getElementById("board");
    const messageElement = document.getElementById("message");
    const scoreElement = document.getElementById("score");
    const applause = document.getElementById("applause");

    let board, currentPlayer, gameOver, scores, playerX, playerO, vsBot;

    function startGame() {
      playerX = document.getElementById("playerX").value || "Jugador X";
      playerO = document.getElementById("playerO").value || "Jugador O";
      vsBot = playerO.toLowerCase().includes("bot");

      board = Array(9).fill("");
      currentPlayer = "X";
      gameOver = false;
      scores = scores || {X: 0, O: 0};

      renderBoard();
      updateScore();
      messageElement.style.display = "none";
    }

    function renderBoard() {
      boardElement.innerHTML = "";
      board.forEach((cell, index) => {
        const cellElement = document.createElement("div");
        cellElement.classList.add("cell");
        if (cell) {
          cellElement.textContent = cell;
          cellElement.classList.add("taken");
        }
        cellElement.addEventListener("click", () => makeMove(index));
        boardElement.appendChild(cellElement);
      });
    }

    function makeMove(index) {
      if (board[index] || gameOver) return;

      board[index] = currentPlayer;
      vibrate();
      renderBoard();
      document.querySelectorAll(".cell")[index].classList.add("glow");

      if (checkWin(currentPlayer)) {
        endGame(`${currentPlayer === "X" ? playerX : playerO} ha ganado 🎉👏`);
        scores[currentPlayer]++;
        updateScore();
        return;
      }

      if (!board.includes("")) {
        endGame("Empate 🤝 ¡Gran partida!");
        return;
      }

      currentPlayer = currentPlayer === "X" ? "O" : "X";

      if (vsBot && currentPlayer === "O") {
        setTimeout(botMove, 500);
      }
    }

    function botMove() {
      // Estrategia básica: ganar si puede, bloquear si debe, si no aleatorio
      let move = findBestMove();
      makeMove(move);
    }

    function findBestMove() {
      // 1. Ganar si posible
      for (let i = 0; i < 9; i++) {
        if (!board[i]) {
          board[i] = "O";
          if (checkWin("O")) { board[i] = ""; return i; }
          board[i] = "";
        }
      }
      // 2. Bloquear a X
      for (let i = 0; i < 9; i++) {
        if (!board[i]) {
          board[i] = "X";
          if (checkWin("X")) { board[i] = ""; return i; }
          board[i] = "";
        }
      }
      // 3. Centro
      if (!board[4]) return 4;
      // 4. Esquinas
      const corners = [0,2,6,8].filter(i => !board[i]);
      if (corners.length) return corners[Math.floor(Math.random()*corners.length)];
      // 5. Restantes
      const empty = board.map((v,i)=>v?null:i).filter(v=>v!==null);
      return empty[Math.floor(Math.random()*empty.length)];
    }

    function checkWin(player) {
      const winPatterns = [
        [0,1,2],[3,4,5],[6,7,8],
        [0,3,6],[1,4,7],[2,5,8],
        [0,4,8],[2,4,6]
      ];
      return winPatterns.some(pattern => 
        pattern.every(index => board[index] === player)
      );
    }

    function endGame(msg) {
      messageElement.innerText = msg;
      messageElement.style.display = "block";
      applause.play();
      gameOver = true;
    }

    function updateScore() {
      scoreElement.innerText = `${playerX} (X): ${scores.X} | ${playerO} (O): ${scores.O}`;
    }

    function vibrate() {
      if (navigator.vibrate) navigator.vibrate(100);
    }
  </script>
</body>
</html>
