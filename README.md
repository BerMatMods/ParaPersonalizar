<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flip Card Tarjeta</title>
<style>
/* Contenedor principal */
.flip-card {
  background-color: transparent;
  width: 240px;
  height: 154px;
  perspective: 1000px;
  color: white;
  margin: 50px auto;
  position: relative;
  font-family: 'Arial', sans-serif;
}

/* Interacción flip */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  cursor: pointer;
}

.flip-card-inner.flipped {
  transform: rotateY(180deg);
}

/* Frente y reverso */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 1rem;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 2px,
              rgba(0, 0, 0, 0.3) 0px 7px 13px -3px,
              rgba(0, 0, 0, 0.2) 0px -1px 0px inset;
  background-color: #171717;
}

/* Reverso rotado */
.flip-card-back {
  transform: rotateY(180deg);
}

/* Elementos del frente */
.chip {
  position: absolute;
  top: 15px;
  left: 15px;
  width: 40px;
  height: 30px;
  background-color: gold;
  border-radius: 5px;
}

.contactless {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 20px;
  height: 15px;
  background-color: silver;
  border-radius: 50%;
}

.logo {
  position: absolute;
  bottom: 15px;
  right: 15px;
  font-weight: bold;
  font-size: 1em;
}

.number {
  position: absolute;
  top: 60px;
  left: 15px;
  font-weight: bold;
  font-size: 0.9em;
  letter-spacing: 2px;
}

.valid_thru {
  position: absolute;
  top: 90px;
  left: 15px;
  font-weight: bold;
  font-size: 0.6em;
}

.date_8264 {
  position: absolute;
  top: 90px;
  left: 80px;
  font-weight: bold;
  font-size: 0.6em;
}

.name {
  position: absolute;
  bottom: 15px;
  left: 15px;
  font-weight: bold;
  font-size: 0.7em;
}

/* Banda magnética y códigos */
.strip {
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 30px;
  background: repeating-linear-gradient(
    45deg,
    #303030,
    #303030 10px,
    #202020 10px,
    #202020 20px
  );
}

.mstrip {
  position: absolute;
  top: 50px;
  left: 10px;
  width: 80px;
  height: 8px;
  background-color: #fff;
  border-radius: 2px;
}

.sstrip {
  position: absolute;
  top: 50px;
  left: 150px;
  width: 40px;
  height: 8px;
  background-color: #fff;
  border-radius: 2px;
}

/* Texto de código (reverso) */
.code {
  font-weight: bold;
  text-align: center;
  color: black;
  margin: 10px;
}

/* Responsividad */
@media (max-width: 500px) {
  .flip-card {
    width: 90%;
    height: auto;
  }
  .number, .valid_thru, .date_8264, .name {
    font-size: 0.8em;
  }
}
</style>
</head>
<body>

<div class="flip-card">
  <div class="flip-card-inner" onclick="this.classList.toggle('flipped')">

    <!-- Frente -->
    <div class="flip-card-front">
      <div class="chip"></div>
      <div class="contactless"></div>
      <div class="strip"></div>
      <div class="mstrip"></div>
      <div class="sstrip"></div>
      <div class="number">1234 5678 9012 3456</div>
      <div class="valid_thru">VALID THRU</div>
      <div class="date_8264">12/28</div>
      <div class="name">Anth'Zz Berrocal</div>
      <div class="logo">LOGO</div>
    </div>

    <!-- Reverso -->
    <div class="flip-card-back">
      <div class="code">123</div>
    </div>

  </div>
</div>

</body>
</html>
