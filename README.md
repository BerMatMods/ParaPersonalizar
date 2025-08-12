<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Juego XO - BerMatMods</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');

  /* Variables tema morado neón (default) */
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

  /* Tema azul neón */
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

  /* Tema rosa neón */
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

  /* Reset y estilos generales */
  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    color: #fff;
    background: var(--bg-gradient);
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 20px 15px 100px 15px;
    transition: background 0.8s ease;
  }

  h1 {
    font-size: 3.5rem;
    letter-spacing: 2px;
    margin-bottom: 5px;
    user-select: none;
    text-shadow:
      0 0 8px var(--color-x),
      0 0 20px var(--color-x-shadow);
  }

  h2 {
    font-size: 1.5rem;
    font-weight: 500;
    margin-top: 0;
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

  #reset-btn, #theme-btn {
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
    user-select: none;
  }
  #reset-btn:hover, #theme-btn:hover {
    background: var(--btn-bg-hover);
    box-shadow:
      0 0 30px var(--btn-bg-hover),
      0 0 60px var(--btn-bg-hover);
  }
  #theme-btn {
    margin-left: 10px;
  }

  /* Contenedor para botones reset y tema */
  #buttons-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 12px;
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
    #reset-btn, #theme-btn {
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
    <input type="text" id="playerX-name" placeholder="Jugador X" maxlength="12" autocomplete="off"/>
  </div>
  <div id="playerO-name-div">
    <label for="playerO-name">Nombre jugador O:</label>
    <input type="text" id="playerO-name" placeholder="Jugador O" maxlength="12" autocomplete="off"/>
  </div>
</div>

<div id="board" aria-label="Tablero de Tic Tac Toe" role="grid" tabindex="0" aria-live="polite">
  <!-- Celdas generadas por JS -->
</div>

<div id="info" aria-live="polite">Turno: Jugador X</div>

<div id="buttons-container">
  <button id="reset-btn" aria-label="Reiniciar juego">Reiniciar Juego</button>
  <button id="theme-btn" aria-label="Cambiar tema de colores">Cambiar Tema 🎨
