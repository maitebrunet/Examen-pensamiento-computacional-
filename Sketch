let filas = 30;
let columnas = 30;
let cuadrado = 30;
let modoColor = 1;

let colores=[
[253,255,0], //amarillo
[0,249,255], //celeste 
[253,0,255], //rosado
];

let estado = 0;
let tiempoInicio;
let sonido;

// AUDIO
function preload() {
  sonido = loadSound("game.mp3");
}

function setup() {
  createCanvas(700, 700);
  rectMode(CENTER);
  noStroke();
  for (let i = 0; i < 5; i++) {
  console.log("Inicio sistema:", i);
}
}

function draw() {
  background(20);

  if (estado == 0) {
    pantallaInicio();
  } else if (estado == 1) {
    pantallaJuego();
  } else if (estado == 2) {
    pantallaFinal();
  }
}

//INICIO 
function pantallaInicio() {
  fill(255);
  textAlign(CENTER, CENTER);

  textSize(30);
  text("DISEÑO INTERACTIVO", width / 2, 220);

  textSize(16);
  text("Presionar CLICK y luego ENTER para comenzar", width / 2, 280);
  text("1, 2 y 3 cambian los colores", width / 2, 320);
}

//JUEGO
function pantallaJuego() {
  let efecto = map(mouseX, 0, width, 0.5, 2);
  let volumen = map(mouseX, 0, width, 0.1, 1);

  // Controla el volumen 
  sonido.setVolume(volumen);

  for (let fila = 0; fila < filas; fila++) {
    for (let columna = 0; columna < columnas; columna++) {
      let x = columna * cuadrado + 10;
      let y = fila * cuadrado + 10;

      let d = dist(x, y, width / 2, height / 2);
      let escala = map(d, 0, 350, 1.8 * efecto, 0.6);

      // Movimiento cinético
   let ruido = random(-0.5, 0.5);
     let movimiento = sin(frameCount * 0.03 + d * 0.04) * 0.15 + ruido;
      let finalSize = cuadrado * (escala + movimiento);

     fill(
       colores[modoColor -1][0],
       colores[modoColor -1][1],
       colores[modoColor -1][2] 
       
     );
      dibujarModulo(x, y, finalSize);
    }
  }
  
  fill(255);
  textAlign(LEFT, CENTER);
  textSize(14);
  text(
    "Mueve el mouse para cambiar el efecto y el volumen. Presiona 1, 2 o 3 para cambiar colores.",
    20,
    30
  );

  // TIEMPO DE DURACIÓN DE 3O SEGUNDOS 
  if (millis() - tiempoInicio > 30000) {
    estado = 2;
    sonido.stop();
  }
}

// FINAL 
function pantallaFinal() {
  fill(255);
  textAlign(CENTER, CENTER);

  textSize(30);
  text("Experiencia Finalizada", width / 2, 230);

  textSize(18);
  text("ENTER para volver a comenzar", width / 2, 290);
}

function keyPressed() {
  userStartAudio();

  if (keyCode === ENTER) {
    if (estado == 0 || estado == 2) {
      estado = 1;
      tiempoInicio = millis();

      // Evita que el sonido se duplique
      if (!sonido.isPlaying()) {
        sonido.loop();
      }
    }
  }

  if (key == "1") {
    modoColor = 1;
  }

  if (key == "2") {
    modoColor = 2;
  }

  if (key == "3") {
    modoColor = 3;
  }
}

function mousePressed() {
  userStartAudio();

  // Si el juego ya empezó y el sonido no está sonando, lo activa
  if (estado == 1 && !sonido.isPlaying()) {
    sonido.loop();
  }
}

function dibujarModulo(x, y, finalSize) {
  rect(x, y, finalSize, finalSize);

  fill(255, 105, 180);
  rect(x, y, finalSize * 0.65, finalSize * 0.65);

  fill(255);
  ellipse(x, y, finalSize * 0.4, finalSize * 0.4);
}
