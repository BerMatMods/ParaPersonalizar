<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>BerMatMods - Multijuegos Web</title>
<style>
  /* Reset y base */
  * { box-sizing: border-box; }
  body {
    margin: 0; font-family: 'Montserrat', sans-serif;
    background: #0a0f12; color: #00ff00;
    display: flex; min-height: 100vh; flex-direction: column;
  }
  a {
    color: #00ff00; text-decoration: none;
  }
  a:hover {
    color: #0ff;
  }
  /* Menú toggle y icono */
  #menuToggle { display: none; }
  .menu-icon {
    cursor: pointer; display: inline-block;
    padding: 10px; position: fixed; top: 10px; left: 10px;
    z-index: 2000;
  }
  .menu-icon div {
    width: 25px; height: 3px; background-color: #0ff;
    margin: 5px 0; transition: 0.4s;
  }
  /* Navegación lateral */
  nav {
    background: #01110f; width: 240px; height: 100vh;
    padding-top: 3rem; position: fixed; top: 0; left: 0;
    overflow-y: auto; transform: translateX(0);
    transition: transform 0.3s ease; z-index: 1000;
  }
  nav ul {
    list-style: none; padding: 0; margin: 0;
  }
  nav ul li {
    border-bottom: 1px solid #022;
  }
  nav ul li a {
    display: block; padding: 15px 20px; font-weight: 700;
    border-left: 4px solid transparent;
  }
  nav ul li a:hover,
  nav ul li a.active {
    background: #013333;
    border-left-color: #0ff;
    color: #0ff;
  }
  /* Sobre mí */
  .about-me {
    padding: 20px;
    color: #0ff;
    margin-top: 20px;
    font-family: 'Dancing Script', cursive;
    border-top: 1px solid #022;
  }
  .about-me h3 {
    margin-top: 0;
  }
  .about-me ul.social-links {
    list-style: none;
    padding-left: 0;
  }
  .about-me ul.social-links li {
    margin: 5px 0;
  }
  .about-me ul.social-links li a {
    color: #0ff;
  }
  /* Contenido principal */
  main {
    margin-left: 240px; padding: 20px; flex-grow: 1;
    min-height: 100vh;
  }
  /* Responsive */
  @media (max-width: 768px) {
    nav {
      transform: translateX(-100%);
      position: fixed;
      z-index: 1000;
    }
    #menuToggle:checked + nav {
      transform: translateX(0);
    }
    main {
      margin-left: 0;
      padding-top: 70px;
    }
  }
  /* Juego Tic Tac Toe */
  .tictactoe-wrapper {
    display: flex; flex-wrap: wrap; gap: 30px; justify-content: center;
  }
  .tictactoe-game {
    background: #022; border-radius: 15px; padding: 20px;
    box-shadow: 0 0 15px #0ff; width: 320px;
  }
  .tictactoe-board {
    display: grid;
    grid-template-columns: repeat(3, 80px);
    grid-gap: 10px;
  }
  .cell {
    background: #004040;
    color: #0ff;
    font-size: 3rem;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    border-radius: 10px;
    user-select: none;
    transition: background 0.3s ease;
  }
  .cell:hover {
    background: #006666;
  }
  #status {
    margin-top: 15px;
    font-weight: bold;
    font-size: 1.2rem;
    text-align: center;
  }
  #resetButton {
    margin-top: 15px;
    background: #0ff;
    border: none;
    color: #022;
    font-weight: 700;
    padding: 10px 15px;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.3s ease;
    width: 100%;
  }
  #resetButton:hover {
    background: #33ffff;
  }
  /* Info animada */
  .info-box {
    background: #011;
    border: 2px solid #0ff;
    border-radius: 15px;
    padding: 20px;
    width: 300px;
    color: #0ff;
    font-family: 'Dancing Script', cursive;
    box-shadow: 0 0 15px #0ff;
    animation: float 4s ease-in-out infinite;
  }
  .info-box img {
    display: block;
    margin: 0 auto 15px auto;
    width: 100px;
    border-radius: 50%;
    border: 2px solid #0ff;
  }
  .info-box h3 {
    text-align: center;
    margin: 0 0 10px 0;
  }
  .info-box p {
    margin: 5px 0;
    text-align: center;
  }
  @keyframes float {
    0%, 100% {
      transform: translateY(0);
      box-shadow: 0 0 15px #0ff;
    }
    50% {
      transform: translateY(-10px);
      box-shadow: 0 0 25px #33ffff;
    }
  }
</style>
</head>
<body>

<input type="checkbox" id="menuToggle" />
<label for="menuToggle" class="menu-icon">
  <div></div><div></div><div></div>
</label>

<nav>
  <ul>
    <li><a href="#juego1" class="active">Tic Tac Toe</a></li>
    <li><a href="#juego2">Snake</a></li>
    <li><a href="#juego3">Memory Match</a></li>
    <li><a href="#juego4">Pong</a></li>
    <li><a href="#juego5">Simon Dice</a></li>
    <li><a href="#juego6">Flappy Bird</a></li>
    <li><a href="#juego7">Breakout</a></li>
    <li><a href="#juego8">Laberinto</a></li>
    <li><a href="#juego9">Sudoku</a></li>
    <li><a href="#juego10">Quiz Trivia</a></li>
    <li><a href="#juego11">Ahorcado</a></li>
    <li><a href="#juego12">Clicker</a></li>
    <li><a href="#juego13">Tower Defense</a></li>
    <li><a href="#juego14">Juego de Cartas</a></li>
    <li><a href="#juego15">Text Adventure</a></li>
    <li><a href="#juego16">Rhythm Game</a></li>
    <li><a href="#juego17">Juego de Dados</a></li>
    <li><a href="#juego18">RPG Simple</a></li>
    <li><a href="#juego19">Juego de Palabras</a></li>
    <li><a href="#juego20">Lanzamiento Física</a></li>
  </ul>

  <hr />
  <div class="about-me">
    <h3>Sobre AnthZz Berrocal</h3>
    <p>Alias: <strong>⚡BerMatModZ🔥</strong></p>
    <p>Ubicación: Andahuaylas, Perú</p>
    <p>Profesión: Programador & Hacker Ético</p>
    <p>Redes Sociales:</p>
    <ul class="social-links">
      <li><a href="https://github.com/BerMatMods" target="_blank" rel="noopener">GitHub</a></li>
      <li><a href="https://t.me/Berrocal_mdz" target="_blank" rel="noopener">Telegram</a></li>
      <li><a href="https://wa.me/937556459" target="_blank" rel="noopener">WhatsApp</a></li>
      <li><a href="https://instagram.com/berrocalanthony12" target="_blank" rel="noopener">Instagram</a></li>
    </ul>
  </div>
</nav>

<main>
  <!-- Contenido cargado dinámicamente -->
</main>

<script>
  // Manejo navegación menú y carga juegos
  document.addEventListener('DOMContentLoaded', () => {
    const menuLinks = document.querySelectorAll('nav ul li a');
    const main = document.querySelector('main');

    function clearActive() {
      menuLinks.forEach(link => link.classList.remove('active'));
    }

    // Juego Tic Tac Toe - implementación completa
    function ticTacToe() {
      main.innerHTML = `
      <h2>Tic Tac Toe - Juego y Mi Info</h2>
      <div class="tictactoe-wrapper">
        <div class="tictactoe-game">
          <div class="tictactoe-board" id="board">
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
            <div class="cell" data-cell></div>
          </div>
          <div id="status">Turno de: X</div>
          <button id="resetButton">Reiniciar Juego</button>
        </div>
        <aside class="info-box">
          <img src="https://avatars.githubusercontent.com/u/74011966?v=4" alt="Avatar de AnthZz Berrocal" />
          <h3>AnthZz Berrocal</h3>
          <p><strong>Alias:</strong> ⚡BerMatModZ🔥</p>
          <p><strong>Ubicación:</strong> Andahuaylas, Perú</p>
          <p><strong>Profesión:</strong> Programador & Hacker Ético</p>
          <p>¡Gracias por jugar! 😊</p>
        </aside>
      </div>
      `;

      const X = 'X';
      const O = 'O';
      let turn = X;
      let board = Array(9).fill(null);
      const cells = main.querySelectorAll('.cell');
      const status = main.querySelector('#status');
      const resetButton = main.querySelector('#resetButton');

      function checkWin(player) {
        const winPatterns = [
          [0,1,2],[3,4,5],[6,7,8], // filas
          [0,3,6],[1,4,7],[2,5,8], // columnas
          [0,4,8],[2,4,6]          // diagonales
        ];
        return winPatterns.some(pattern =>
          pattern.every(index => board[index] === player)
        );
      }
      function checkDraw() {
        return board.every(cell => cell !== null);
      }
      function updateStatus(text) {
        status.textContent = text;
      }
      function handleClick(e) {
        const index = [...cells].indexOf(e.target);
        if(board[index] !== null) return;
        board[index] = turn;
        e.target.textContent = turn;
        if(checkWin(turn)) {
          updateStatus(`¡Jugador ${turn} gana! 🎉`);
          cells.forEach(c => c.removeEventListener('click', handleClick));
          return;
        }
        if(checkDraw()) {
          updateStatus(`¡Empate! 🤝`);
          return;
        }
        turn = turn === X ? O : X;
        updateStatus(`Turno de: ${turn}`);
      }
      cells.forEach(cell => cell.addEventListener('click', handleClick));
      resetButton.addEventListener('click', () => {
        board.fill(null);
        cells.forEach(cell => cell.textContent = '');
        turn = X;
        updateStatus(`Turno de: ${turn}`);
        cells.forEach(cell => cell.addEventListener('click', handleClick));
      });
    }

    // Juegos pendientes: mostrar mensaje "Próximamente"
    function comingSoon(name) {
      main.innerHTML = `<h2>${name}</h2><p style="font-size:1.2rem; text-align:center; margin-top:40px;">Este juego estará disponible próximamente. ¡Mantente atento! 🚀</p>`;
    }

    function loadGame(id) {
      clearActive();
      const link = document.querySelector(`nav ul li a[href="#${id}"]`);
      if (link) link.classList.add('active');

      switch(id) {
        case 'juego1': ticTacToe(); break;
        case 'juego2': comingSoon('Snake'); break;
        case 'juego3': comingSoon('Memory Match'); break;
        case 'juego4': comingSoon('Pong'); break;
        case 'juego5': comingSoon('Simon Dice'); break;
        case 'juego6': comingSoon('Flappy Bird'); break;
        case 'juego7': comingSoon('Breakout'); break;
        case 'juego8': comingSoon('Laberinto'); break;
        case 'juego9': comingSoon('Sudoku'); break;
        case 'juego10': comingSoon('Quiz Trivia'); break;
        case 'juego11': comingSoon('Ahorcado'); break;
        case 'juego12': comingSoon('Clicker'); break;
        case 'juego13': comingSoon('Tower Defense'); break;
        case 'juego14': comingSoon('Juego de Cartas'); break;
        case 'juego15': comingSoon('Text Adventure'); break;
        case 'juego16': comingSoon('Rhythm Game'); break;
        case 'juego17': comingSoon('Juego de Dados'); break;
        case 'juego18': comingSoon('RPG Simple'); break;
        case 'juego19': comingSoon('Juego de Palabras'); break;
        case 'juego20': comingSoon('Lanzamiento Física'); break;
        default:
          main.innerHTML = `<p>Juego no encontrado.</p>`;
      }
    }

    // Inicializar el primer juego
    loadGame('juego1');

    // Manejo clicks menú
    menuLinks.forEach(link => {
      link.addEventListener('click', e => {
        e.preventDefault();
        const id = link.getAttribute('href').substring(1);
        loadGame(id);
      });
    });
  });
</script>

</body>
</html>
