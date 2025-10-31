
# Evidencias de la unidad 8

## Actividad 1

- **1.) Documenta los referentes visuales que te inspiren.**

  - Mi referente principal es el video de [yellow submarine](https://www.youtube.com/watch?v=m2uTFF_3MaA&list=RDm2uTFF_3MaA&start_radio=1) que desde chiquito me fascina.
  - Y tambien este [video](https://www.youtube.com/watch?v=UjNBJ39XNQA) que me encanta y me llena de alegría cada que lo veo

- **2.) Define el concepto de las visuales que quieres crear.**

me gustan los pescados y el videito de yellow submarine entonces voy a hacer algo con esa estética, lo quiero hacer como con un enjambre de pescados que cambie de color, forma, velocidad y pues que se desorganicen de vez en cuando con el coro, ahí vemos.

antes que todo y primero que nada, piratear la canción y cargarla.

En la unidad pasada hice lo de crear una clase que tuviera un update y un draw y llamar esos metodos propios por cada instancia de la clase, y me pareció muy facil de implementar entonces eso es lo que voy a hacer de nuevo. Entonces como me lo imagino es que se vea como una cantidad infinita de pescados pero en realidad cuando salen del frame cambia su posición a una relativa en la esquina opuesta, ahora, en cuanto a interacción, quiero que vayan hacía donde mi dedo apunte.

Para empezar lo importante es crear la clase de pescado, donde tengo pensado definir cosas basicas como su apariencia y comportamiento, como su reaccion a la musica, su update y su draw.

Para la parte de velocidad, tamñano y color sean manejadas por los bajos, para que se vea como que están pegando saltitos, los medios y altos aún no se pero se me ocurre que pueden mover la velocidad y saturación del color.

en cuanto a interactividad tengo pensado que la perosna pueda definir la dirección en la que se mueven los pescados, lo pienso como un cardumen de pescados y como elegí yellow submarine entonces que se vuelvan amarillos cuando se toque la pantalla.

en ese caso necesito varias cosas desde el cliente mobile saber cuando termina y empieza un toque Y cuadno hay un toque, de esta forma podrá saber cuando volver al comportamiento nomral y cuando ir en una dirección.

- **3.) Explica cómo el móvil y el micro:bit controlarán las visuales.**

  - El movil se encargará de dos comportamientos: cambiar el color a amarillo cuando haya un toque y definir la dirección de los pescados.
  - El microbit se encargará de darles comidita a los pescados y de darles unos comportamientos.

- **4.) Haz un bocetos de todas las interfaces del sistema.**

  - desktop

    - <img width="1272" height="712" alt="image" src="https://github.com/user-attachments/assets/e735ecb7-45bc-4981-ba0e-993076cab255" />


  - mobile

    - <img width="470" height="846" alt="image" src="https://github.com/user-attachments/assets/76865a6a-e054-4f88-b950-000bfa446ca0" />


- **5.) Haz un diagrama que explique cómo se comunicarán los diferentes componentes del sistema.**

  - <img width="862" height="672" alt="image" src="https://github.com/user-attachments/assets/113a51c8-cd4b-49f8-810c-d9cdc97f8c74" />

## Actividad 2

### Construcción

<img width="647" height="260" alt="image" src="https://github.com/user-attachments/assets/a3092f53-50fc-4316-b616-a6a09d82aa33" />

Este primer prompt sirvió de maravilla, si tuve que hacer un par de correcciones en el sentido de que no me gustó bastante los colores que eligió o en que orden dibuja las cosas, pero aparte de eso, en el aldo técnico implementó exactamente lo que le pedí.

<img width="635" height="178" alt="image" src="https://github.com/user-attachments/assets/ff3f1b1e-ce0b-46b7-a875-5f04989012ac" />

Hizo eso esaxtamente, tuve que hacerle unos ajustes, de nuevo por la dirección de los pescados, la velocidad, el tamaño de las particulas y ya.

Realmente la implementación de la IA sirvió más que todo como una forma de escribir más rápido un texto simple

**MICROBIT**

```py
from microbit import *

uart.init(baudrate=115200)
display.show(Image.BUTTERFLY)

while True:
    if button_a.is_pressed():
        uart.write('A')
        sleep(500)
    if button_b.is_pressed():
        uart.write('B')
        sleep(500)
    if accelerometer.was_gesture('shake'):
        uart.write('C')
        sleep(500)
```
**DESKTOP**

p5js

``` js
let numFish = 40;
let fft, song;
let audioStarted = false;

let fishes = [];
let submarines = [];
let bubbles = [];

let particles = [];
let particleFishPairs = [];
let particleModeActive = false;
let lastTime = 0;

let rays = [];
let socket;
let targetDir = null;
let lastTouchTime = 0;

let yellowShiftActive = false;
let yellowShiftStart = 0;
let yellowShiftDuration = 2000;

let colorShiftActive = false;
let colorShiftStart = 0;
let colorShiftDuration = 2000;
let hueOffset = 0;

let nextAutoShift = 0;
let autoShiftInterval = 25000;

function preload() {
  soundFormats('mp3', 'ogg');
  song = loadSound('Yellow Submarine.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  angleMode(DEGREES);
  colorMode(RGB);

    port = createSerial();
    connectBtn = createButton('Connect to micro:bit');
    connectBtn.position(20, 20);
    connectBtn.mousePressed(connectBtnClick);

  for (let i = 0; i < numFish; i++) {
    fishes.push(new Fish(random(width), random(height)));
  }

  let numRays = 30;
  for (let i = 0; i < numRays; i++) {
    let spacing = width / numRays;
    rays.push({
      x: i * spacing,
      width: random(25, 45),
      offset: random(TWO_PI)
    });
  }

  fft = new p5.FFT();

  nextAutoShift = millis() + autoShiftInterval;

  socket = io();
  socket.on('connect', () => console.log('Connected to server'));

  socket.on('message', (data) => {
  if (data.type === 'touch') {
    lastTouchTime = millis();
    targetDir = createVector(data.x - width / 2, data.y - height / 2).normalize();
  } else if (data.type === 'yellowShift') {
    yellowShiftActive = true;
    yellowShiftStart = millis();
  }
});

  socket.on('disconnect', () => console.log('Disconnected'));
}

function draw() {

  push();
  translate(0, sin(frameCount * 0.01) * 15);

  let currentTime = millis();
  let deltaTime = lastTime === 0 ? 16 : currentTime - lastTime;
  lastTime = currentTime;

      if(port.availableBytes() > 0){
  let dataRx = port.read(1);
  if(dataRx == 'A'){
    console.log('A');
    submarines.push(new YellowSubmarine());
  }
  else if(dataRx == 'B'){
    console.log('B');
    for (let i = 0; i < 60; i++) {
      bubbles.push(new Bubble());
    }
  }
  else if(dataRx == 'C'){
    console.log('SHAKE AHHHHHHHHHHHHHHHHHHHH');
    activateParticleMode();
  }
  else{
    return;
  }
}


    if (!port.opened()) {
        connectBtn.html('Connect to micro:bit');
    }
    else {
        connectBtn.html('Disconnect');
    }

  drawGradientBackground();
  drawLightRays();

  if (!audioStarted) {
    drawStartScreen();
    return;
  }

  if (millis() - lastTouchTime > 500) targetDir = null;

  let spectrum = fft.analyze();
  let bass = fft.getEnergy('bass');
  let mid = fft.getEnergy('mid');
  let treble = fft.getEnergy('treble');

if (millis() > nextAutoShift) {
  colorShiftActive = true;
  colorShiftStart = millis();
  nextAutoShift = millis() + autoShiftInterval;
}

if (colorShiftActive) {
  let elapsed = millis() - colorShiftStart;
  let progress = constrain(elapsed / colorShiftDuration, 0, 1);
  hueOffset = lerp(0, 180, progress);
  if (progress >= 1) colorShiftActive = false;
} else {
  hueOffset = 0;
}

if (bass > 220 && !colorShiftActive) { 
  colorShiftActive = true;
  colorShiftStart = millis();
}

for (let i = submarines.length - 1; i >= 0; i--) {
  submarines[i].update();
  submarines[i].display();
  
  if (submarines[i].isOffScreen()) {
    submarines.splice(i, 1);
  }
}

if (particleModeActive) {
  for (let i = particles.length - 1; i >= 0; i--) {
    particles[i].update();
    particles[i].display();
    
    if (particles[i].isOffScreen()) {
      particles.splice(i, 1);
    }
  }
  
for (let i = particleFishPairs.length - 1; i >= 0; i--) {
  let pair = particleFishPairs[i];
  
  if (pair.particle && pair.fish) {
    pair.lerpProgress += (1000 / 60) / pair.lerpDuration;
    let easedProgress = easeOutCubic(min(pair.lerpProgress, 1));
    
    pair.fish.pos.x = lerp(pair.fish.pos.x, pair.particle.pos.x, easedProgress * 0.1);
    pair.fish.pos.y = lerp(pair.fish.pos.y, pair.particle.pos.y, easedProgress * 0.1);
    
    let targetDirection = createVector(
      pair.particle.pos.x - pair.fish.pos.x,
      pair.particle.pos.y - pair.fish.pos.y
    ).normalize();
    
    pair.fish.vel.lerp(targetDirection.mult(pair.fish.speed), 0.1);
    
    pair.fish.angle = degrees(pair.fish.vel.heading());
    
    let distance = dist(pair.fish.pos.x, pair.fish.pos.y, pair.particle.pos.x, pair.particle.pos.y);
    if (distance < 10 || pair.lerpProgress >= 1) {
      let particleIndex = particles.indexOf(pair.particle);
      if (particleIndex > -1) {
        particles.splice(particleIndex, 1);
      }
      
      pair.fish.speed = pair.fishOriginalSpeed;
      
      particleFishPairs.splice(i, 1);
    }
  }
}
  
  if (particles.length === 0 && particleFishPairs.length === 0) {
    particleModeActive = false;
  }
}

for (let f of fishes) {
  f.reactToMusic(bass, mid, treble);
  let isChasingParticle = particleFishPairs.some(pair => pair.fish === f);
  if (!isChasingParticle) {
    f.updateBehavior(targetDir, bass);
  }
  
  f.update();
  f.display();
}

for (let i = bubbles.length - 1; i >= 0; i--) {
  bubbles[i].update();
  bubbles[i].display();
  
  if (bubbles[i].isOffScreen()) {
    bubbles.splice(i, 1);
  }
}

  pop();

}

function drawStartScreen() {
  fill(255);
  textAlign(CENTER, CENTER);
  textSize(32);
  text('PRESIONA PARA EMPEZAR', width / 2, height / 2);
}

function mousePressed() {
  if (!audioStarted) {
    userStartAudio();
    song.loop();
    audioStarted = true;
  }
}

function touchStarted() {
  lastTouchTime = millis();
  if (!audioStarted) {
    userStartAudio();
    song.loop();
    audioStarted = true;
  } else if (touches.length > 0) {
    let t = touches[0];
    targetDir = createVector(t.x - width / 2, t.y - height / 2).normalize();
  }
  return false;
}

function touchMoved() {
  lastTouchTime = millis();
  if (touches.length > 0) {
    let t = touches[0];
    targetDir = createVector(t.x - width / 2, t.y - height / 2).normalize();
  }
  return false;
}

function touchEnded() {
  targetDir = null;
}


class Fish {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = p5.Vector.random2D();
    this.baseSpeed = random(1.2, 2.5);
    this.speed = this.baseSpeed;
    this.size = random(10, 25);
    this.angle = random(360);
    this.wanderTheta = random(TWO_PI);
    this.baseHue = random(0, 360);
    this.color = color(200, 200, 255);
  }

  updateBehavior(targetDir, bass) {
    if (targetDir) {
      let dir = targetDir.copy();
      this.vel = p5.Vector.lerp(this.vel, dir.mult(this.speed + map(bass, 0, 255, 2, 8)), 0.1);
    } else {
      this.wanderTheta += random(-0.25, 0.25);
      let wanderDir = p5.Vector.fromAngle(this.wanderTheta);
      this.vel = p5.Vector.lerp(this.vel, wanderDir.mult(this.speed), 0.05);
    }
  }

  reactToMusic(bass, mid, treble) {
  this.size = map(bass, 0, 255, 10, 90);
  this.speed = this.baseSpeed + map(bass, 0, 255, 0, 8);

  colorMode(HSB);

  let baseHue = (this.baseHue + map(mid, 0, 255, -40, 40)) % 360;
  let baseSat = map(mid, 0, 255, 20, 80);
  let baseBright = map(treble, 0, 255, 70, 100);

  let hueValue = baseHue;
  let satValue = baseSat;
  let brightValue = baseBright;

  if (yellowShiftActive) {
    let elapsed = millis() - yellowShiftStart;
    let progress = constrain(elapsed / yellowShiftDuration, 0, 1);
    if (progress < 1) {
      let yellowHue = 55;
      let yellowSat = 90;
      let yellowBright = 100;

      hueValue = lerp(baseHue, yellowHue, progress);
      satValue = lerp(baseSat, yellowSat, progress);
      brightValue = lerp(baseBright, yellowBright, progress);
    } else {
      let backProgress = constrain((elapsed - yellowShiftDuration) / yellowShiftDuration, 0, 1);

      hueValue = lerp(55, baseHue, backProgress);
      satValue = lerp(90, baseSat, backProgress);
      brightValue = lerp(100, baseBright, backProgress);

      if (backProgress >= 1) yellowShiftActive = false;
    }
  }

  this.color = color(hueValue, satValue, brightValue);
  colorMode(RGB);
}


  update() {
    this.pos.add(this.vel);
    this.angle = degrees(this.vel.heading());

    if (this.pos.x < -this.size) this.pos.x = width + this.size;
    if (this.pos.x > width + this.size) this.pos.x = -this.size;
    if (this.pos.y < -this.size) this.pos.y = height + this.size;
    if (this.pos.y > height + this.size) this.pos.y = -this.size;
  }

  display() {
    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.angle);

    colorMode(HSB);
    let glow = color(hue(this.color), saturation(this.color), brightness(this.color), 0.1);
    fill(glow);
    noStroke();
    ellipse(0, 0, this.size * 2, this.size * 1.2);

    fill(this.color);
    noStroke();

    ellipse(0, 0, this.size * 1.8, this.size);
    triangle(
      -this.size * 0.9, 0,
      -this.size * 1.5, this.size * 0.5,
      -this.size * 1.5, -this.size * 0.5
    );

    fill(255);
    ellipse(this.size * 0.5, 0, this.size * 0.4);
    fill(0);
    ellipse(this.size * 0.5, 0, this.size * 0.15);

    colorMode(RGB);
    pop();
  }
}

function drawGradientBackground() {
  noFill();
  for (let y = 0; y <= height; y++) {
    let inter = map(y, 0, height, 0, 1);
    let c1 = color(90, 190, 255);
    let c2 = color(0, 25, 70);
    let c = lerpColor(c1, c2, inter);
    stroke(c);
    line(0, y, width, y);
  }
}

function drawLightRays() {
  if (!audioStarted) return;

  let low = fft.getEnergy('bass');
  let mid = fft.getEnergy('mid');
  let high = fft.getEnergy('treble');

  push();
  blendMode(ADD);
  noStroke();

  let globalSway = sin(frameCount * 0.008) * 40;
  let raySpacing = width / rays.length;

  for (let i = 0; i < rays.length; i++) {
    let r = rays[i];

    let t = i / (rays.length - 1);
    let energy = lerp(low, high, t) * 0.6 + mid * 0.4;

    let len = map(energy, 0, 255, height * 0.4, height * 1.1);
    let w = r.width;
    let baseAlpha = map(energy, 0, 255, 15, 45);

    let sway = sin(frameCount * 0.01 + r.offset) * 15 + globalSway * 0.3;
    let x = i * raySpacing + sway;

    for (let yy = 0; yy < len; yy += 8) {
      let inter = map(yy, 0, len, 1, 0);
      let beamAlpha = inter * baseAlpha;
      fill(180, 225, 255, beamAlpha);
      rect(x, yy, w, 8);
    }
  }

  blendMode(BLEND);
  pop();
}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}

class YellowSubmarine {
  constructor() {
    this.size = random(100, 150);
    this.speed = random(4, 8);
    
    this.startFromLeft = random() > 0.5;
    
    if (this.startFromLeft) {
      this.x = -this.size;
      this.direction = 1;
    } else {
      this.x = width + this.size;
      this.direction = -1;
    }
    
    this.y = random(height * 0.2, height * 0.8);
    this.wobbleOffset = random(1000);
    this.wobbleAmount = random(2, 5);
  }

  update() {
    this.x += this.speed * this.direction;
    
    this.wobbleY = sin(frameCount * 0.05 + this.wobbleOffset) * this.wobbleAmount;
  }

  display() {
    push();
    translate(this.x, this.y + this.wobbleY);
    
    fill(255, 204, 0);
    noStroke();
    
    ellipse(0, 0, this.size, this.size * 0.4);
    
    rect(-this.size * 0.1, -this.size * 0.3, this.size * 0.2, this.size * 0.3);
    
    fill(173, 216, 230);
    for (let i = -2; i <= 2; i++) {
      ellipse(i * this.size * 0.15, 0, this.size * 0.08);
    }
    
    fill(100);
    rect(this.size * 0.05, -this.size * 0.45, this.size * 0.03, this.size * 0.15);
    ellipse(this.size * 0.065, -this.size * 0.5, this.size * 0.06);
    
    pop();
  }

  isOffScreen() {
    if (this.direction > 0) {
      return this.x > width + this.size * 2;
    } else {
      return this.x < -this.size * 2;
    }
  }
}

class Bubble {
  constructor() {
    this.x = random(width);
    this.y = height + 20;
    this.size = random(10, 30);
    this.speed = random(2, 5);
    this.wobbleOffset = random(TWO_PI);
    this.wobbleAmount = random(10, 20);
    this.horizontalSpeed = random(-0.5, 0.5);
  }

  update() {
    this.y -= this.speed;
    this.x += sin(frameCount * 0.1 + this.wobbleOffset) * 0.5 + this.horizontalSpeed;
  }

  display() {
    push();
    translate(this.x, this.y);
    
    noFill();
    stroke(255, 255, 255, 150);
    strokeWeight(2);
    ellipse(0, 0, this.size);
    
    fill(255, 255, 255, 100);
    noStroke();
    ellipse(-this.size * 0.2, -this.size * 0.2, this.size * 0.3);
    
    pop();
  }

  isOffScreen() {
    return this.y < -this.size;
  }
}

class Particle {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = createVector(0, random(2, 4));
    this.size = random(5, 15);
    this.color = color(139, 69, 19);
    this.wobbleOffset = random(TWO_PI);
    this.wobbleAmount = random(3, 8);
  }

  update() {
    this.pos.add(this.vel);
    
    this.pos.x += sin(frameCount * 0.1 + this.wobbleOffset) * 0.3;
  }

  display() {
    push();
    translate(this.pos.x, this.pos.y);
    
    fill(this.color);
    noStroke();
    ellipse(0, 0, this.size);
    
    fill(160, 82, 45);
    ellipse(-this.size * 0.2, -this.size * 0.2, this.size * 0.4);
    
    pop();
  }

  isOffScreen() {
    return this.pos.y > height + this.size;
  }
}

function activateParticleMode() {
  particleModeActive = true;
  particles = [];
  particleFishPairs = [];
  
  for (let i = 0; i < fishes.length; i++) {
    let particle = new Particle(random(width), -20);
    particles.push(particle);
    
    particleFishPairs.push({
      particle: particle,
      fish: fishes[i],
      fishOriginalSpeed: fishes[i].speed,
      lerpProgress: 0,
      lerpDuration: random(10000, 25000)
    });
    
    fishes[i].speed = fishes[i].baseSpeed * 0.3;
  }
}

function easeOutCubic(x) {
  return 1 - Math.pow(1 - x, 3);
}
```
librerias

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
    <script src="https://unpkg.com/@gohai/p5.webserial@^1/libraries/p5.webserial.js"></script>


    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <script src="sketch.js"></script>
    <title>Desktop p5.js Application</title>
</head>
<body></body>
</html>
```

**MOBILE**

``` js
let socket;
let lastTouchX = null;
let lastTouchY = null;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  socket = io();

  socket.on('connect', () => console.log('Connected to server'));
}

function draw() {
  background(70, 80, 255);
  fill(90, 190, 255);
  textAlign(CENTER, CENTER);
  textSize(20);
  text('MANTENER PRESIONADO PARA MOVER LOS PESCADOS\n PRESIONAR PARA VOLVERLOS AMARILLOS', width / 2, height / 2);
}

function touchStarted() {
  if (socket && socket.connected) {
    socket.emit('message', { type: 'yellowShift' });
    let t = touches[0];
    socket.emit('message', { type: 'touch', x: t.x, y: t.y });
  }
  return false;
}

function touchMoved() {
  if (socket && socket.connected && touches.length > 0) {
    let t = touches[0];
    socket.emit('message', { type: 'touch', x: t.x, y: t.y });
  }
  return false;
}

function touchEnded() {
  if (socket && socket.connected) {
    socket.emit('message', { type: 'touchEnd' });
  }
  return false;
}
```
librerias

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <script src="https://unpkg.com/@gohai/p5.webserial@^1/libraries/p5.webserial.js"></script>
    <script src="sketch.js"></script>
    <title>Mobile p5.js Application</title>
</head>
<body></body>
</html>
```
**SERVER**

``` js
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```
# EVIDENCIAS

- **Actividad 1**
	- Realicé todo lo que proponía la actividad.
 	- [EVIDENCIA](#actividad-1)
- **Actividad 2**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
 	- [EVIDENCIA](#actividad-2)
