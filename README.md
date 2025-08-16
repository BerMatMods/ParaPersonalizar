
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Juego XO - BerMat_Mods</title>
  <style>
    body {
      background: radial-gradient(circle at top, #111, #000);
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
      text-shadow: 0 0 20px cyan, 0 0 40px blue;
      margin-bottom: 20px;
    }

    .players {
      margin-bottom: 20px;
    }

    .players input {
      padding: 8px;
      margin: 5px;
      border-radius: 10px;
      border: none;
      font-size: 1em;
      text-align: center;
    }

    #game {
      display: grid;
      grid-template-columns: repeat(3, 120px);
      grid-template-rows: repeat(3, 120px);
      gap: 10px;
    }

    .cell {
      width: 120px;
      height: 120px;
      background: linear-gradient(145deg, #222, #111);
      border: 3px solid cyan;
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.5em;
      cursor: pointer;
      box-shadow: 0 0 15px cyan;
      transition: all 0.2s;
    }

    .cell:hover {
      background: linear-gradient(145deg, #333, #111);
      transform: scale(1.05);
    }

    #message {
      position: absolute;
      top: 20%;
      background: rgba(0,0,0,0.85);
      padding: 20px 40px;
      border-radius: 15px;
      font-size: 1.8em;
      text-align: center;
      display: none;
      animation: fadeIn 1s ease-in-out;
      box-shadow: 0 0 25px lime;
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: scale(0.5);}
      to {opacity: 1; transform: scale(1);}
    }

    @keyframes vibrate {
      0% { transform: translate(0);}
      25% { transform: translate(-2px, 2px);}
      50% { transform: translate(2px, -2px);}
      75% { transform: translate(-2px, -2px);}
      100% { transform: translate(0);}
    }

    .scoreboard {
      margin: 20px;
      font-size: 1.2em;
      text-shadow: 0 0 10px magenta;
    }

    #credits {
      margin-top: 30px;
      font-size: 0.9em;
      text-shadow: 0 0 10px cyan;
    }

    /* 🎉 Confetti para cuando gana */
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background: hsl(var(--hue), 100%, 50%);
      top: -10px;
      animation: fall 3s linear infinite;
    }

    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(360deg);
      }
    }
  </style>
</head>
<body>
  <h1>🎮 Juego de XO - BerMat_Mods</h1>

  <div class="players">
    <input type="text" id="player1" placeholder="Nombre Jugador 1">
    <input type="text" id="player2" placeholder="Nombre Jugador 2 / Bot">
    <button onclick="startGame()">Iniciar</button>
  </div>

  <div id="game"></div>
  <div class="scoreboard" id="scoreboard">Marcador: </div>

  <div id="message"></div>
  <div id="credits">⚡ Creado por Anth'Zz Berrocal (Alias: BerMat_Mods) ⚡</div>

  <script>
    const gameBoard = document.getElementById('game');
    const messageBox = document.getElementById('message');
    const scoreboard = document.getElementById('scoreboard');
    let currentPlayer = 'X';
    let board = Array(9).fill('');
    let playerNames = ['Jugador 1','Jugador 2'];
    let scores = {X:0,O:0};

    function startGame() {
      playerNames[0] = document.getElementById('player1').value || "Jugador 1";
      playerNames[1] = document.getElementById('player2').value || "Jugador 2";
      resetBoard();
      updateScoreboard();
    }

    function resetBoard() {
      board = Array(9).fill('');
      gameBoard.innerHTML = '';
      for (let i=0;i<9;i++){
        const cell = document.createElement('div');
        cell.className = 'cell';
        cell.dataset.index = i;
        cell.addEventListener('click', handleClick);
        gameBoard.appendChild(cell);
      }
    }

    function handleClick(e){
      const index = e.target.dataset.index;
      if (board[index] !== '') return;

      board[index] = currentPlayer;
      e.target.textContent = currentPlayer;
      e.target.style.animation = "vibrate 0.2s";

      if (checkWinner()) {
        scores[currentPlayer]++;
        updateScoreboard();
        showMessage(`🎉 Felicidades ${playerNames[currentPlayer === 'X' ? 0:1]} (${currentPlayer}) ganó! 🎉`);
        confetti();
        setTimeout(resetBoard, 2500);
        return;
      }

      if (board.every(cell => cell !== '')) {
        showMessage("🤝 ¡Empate! Grandes jugadores 👏");
        setTimeout(resetBoard, 2000);
        return;
      }

      currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    }

    function checkWinner(){
      const combos = [
        [0,1,2],[3,4,5],[6,7,8],
        [0,3,6],[1,4,7],[2,5,8],
        [0,4,8],[2,4,6]
      ];
      return combos.some(([a,b,c]) => board[a] && board[a]===board[b] && board[a]===board[c]);
    }

    function showMessage(msg){
      messageBox.textContent = msg;
      messageBox.style.display = "block";
      setTimeout(()=>{messageBox.style.display="none"}, 2000);
    }

    function updateScoreboard(){
      scoreboard.textContent = `Marcador: ${playerNames[0]} (X): ${scores.X} | ${playerNames[1]} (O): ${scores.O}`;
    }

    function confetti(){
      for(let i=0;i<50;i++){
        const c = document.createElement('div');
        c.className='confetti';
        c.style.left = Math.random()*100+'vw';
        c.style.setProperty('--hue', Math.random()*360);
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),3000);
      }
    }
  </script>
</body>
</html>
