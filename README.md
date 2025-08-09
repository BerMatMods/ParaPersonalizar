<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Contador en tiempo real</title>
<style>
  body {
    background: #001f3f;
    color: #a0e9ff;
    font-family: 'Raleway', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
  }
  #contador {
    font-size: 32px;
    font-weight: 700;
    text-shadow: 0 0 15px #3ecfff;
  }
</style>
</head>
<body>

<div id="contador">Calculando...</div>

<script>
  const inicio = new Date("2023-11-10T00:00:00");
  const contadorEl = document.getElementById("contador");

  function actualizarContador() {
    const ahora = new Date();

    let anos = ahora.getFullYear() - inicio.getFullYear();
    let meses = ahora.getMonth() - inicio.getMonth();
    let dias = ahora.getDate() - inicio.getDate();
    let horas = ahora.getHours() - inicio.getHours();
    let minutos = ahora.getMinutes() - inicio.getMinutes();
    let segundos = ahora.getSeconds() - inicio.getSeconds();

    if (segundos < 0) { segundos += 60; minutos--; }
    if (minutos < 0) { minutos += 60; horas--; }
    if (horas < 0) { horas += 24; dias--; }
    if (dias < 0) {
      meses--;
      const mesAnterior = new Date(ahora.getFullYear(), ahora.getMonth(), 0);
      dias += mesAnterior.getDate();
    }
    if (meses < 0) { meses += 12; anos--; }

    contadorEl.textContent = `💞 YA VAMOS: ${anos} AÑOS, ${meses} MESES, ${dias} DÍAS, ${horas}h ${minutos}m ${segundos}s 💞`;
  }

  setInterval(actualizarContador, 1000);
  actualizarContador();
</script>

</body>
</html>
