
# Evidencias de la unidad 7

## Actividad 1

> abrir el codigo
> 
> fordward el port, ponerle que 3000, para mandarlo a internet
> 
> cambiar la visibilidad del puerto a pública

- **1.) ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**

  - Por que ya no todo pasa en el mismo computador, el celular se debe de conectar por internet. Entonces esa URL que sale es la dirección de ese servidor en internet.

- **2.) Describe brevemente qué hace npm install y npm start.**

  - npm install se encarga de instalar todos los paquetes de los que depende el proyecto y npm start se encarga de abrir el servidor (eso en nuestor caso) creo que en realidad lo que hace es que corre los scripts.

- **3.) ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

  - <img width="560" height="334" alt="image" src="https://github.com/user-attachments/assets/4c1259a4-dd49-40f3-bef8-a731cbd9e655" />

  - <img width="520" height="576" alt="image" src="https://github.com/user-attachments/assets/34994c34-d209-4a10-b441-60a7387acb0a" />

- **4.) Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

  - Yo lo noté medianamente inmediato, diría que como no se corre localmente debe ser un poquito más lento.
  - Sin embargo despues de correr la aplicación solamente en el computador si noté que había algún tipo de retraso puesto que localmente la respuesta es inmediata.
 
## Actividad 2

- **1.) Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

  - DevTunnels es necesario por que la conexión sucede por medio de internet, conceptualmente es como una especie de lugar que se encarga de redirigir información a lugares invisibles que solo el sabe donde está.

- **2.) Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

  - la función touchMoved() se encarga de detectar cuando se presiona la pantalla y se llama cada frame en lo que esto pase. La variable threshold es utilizada para identificar si hubo cambios significativos en la posición x/y del touch, de esta forma, si el cambio fue menor 5 entonces no hace nada.

-  **3.) Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**

    -  pues en un principio diría que todo lo local es mucho más rápido y seguro que cualquier otra cosa que se conecte a internet, entonces localmente diría que la IP local es mucho más rápida

-  **4.) Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

    -  <img width="1036" height="934" alt="image" src="https://github.com/user-attachments/assets/1b0ba905-f787-40b2-83f0-3d1835462092" />

## Actividad 3

- **1.) ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

  - eso lo que está haciendo es que está buscando los archivos que están en esa carpeta public del proyecto y está creando una instancia estática pues el servidor solo va a sacar la infor de lo que está ahí. y es diferente del get en el sentido en que el get no crea la instancia estática de los archivos.

- **2.) Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**

  - <img width="590" height="388" alt="image" src="https://github.com/user-attachments/assets/349e7b5a-395e-4e72-8b85-c172eebb01c9" />

  - <img width="426" height="222" alt="image" src="https://github.com/user-attachments/assets/c286ac9d-4811-4c76-aa2f-f326be0b58cf" />

  - <img width="338" height="153" alt="image" src="https://github.com/user-attachments/assets/8f0afd03-9484-4944-88c8-2e35acca7c2d" />

  - la difernecia es que sockect.emit se lo manda a TODOS los clientes conectados, y socket.broadcast.emit se lo manda también a todos EXCEPTO a la conexión más reciente, lo que sea que signifique eso.

- **3.) Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**

  - pues realmente todo depende de a que URL estén conectados, pero entendiendo la definición de socket.broadcast.emit, eso significa que solo le mandaría la info del celular  

- **4.) ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**

  - <img width="583" height="461" alt="image" src="https://github.com/user-attachments/assets/bb92ea00-4d50-4d6e-bb7f-03faa140d5f1" />

## Actividad 4

**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.**

<img width="576" height="743" alt="image" src="https://github.com/user-attachments/assets/a707f53f-2aff-4eb0-ba3f-18dba53ecf68" />

## Actividad 5

me gustan los pescados y el videito de yellow submarine entonces voy a hacer algo con esa estética, lo quiero hacer como con un enjambre de pescados que cambie de color, forma, velocidad y pues que se desorganicen de vez en cuando con el coro, ahí vemos.

antes que todo y primero que nada, piratear la canción y cargarla.

En la unidad pasada hice lo de crear una clase que tuviera un update y un draw y llamar esos metodos propios por cada instancia de la clase, y me pareció muy facil de implementar entonces eso es lo que voy a hacer de nuevo. Entonces como me lo imagino es que se vea como una cantidad infinita de pescados pero en realidad cuando salen del frame cambia su posición a una relativa en la esquina opuesta, ahora, en cuanto a interacción, quiero que vayan hacía donde mi dedo apunte.

Para empezar lo importante es crear la clase de pescado, donde tengo pensado definir cosas basicas como su apariencia y comportamiento, como su reaccion a la musica, su update y su draw.

Para la parte de velocidad, tamñano y color sean manejadas por los bajos, para que se vea como que están pegando saltitos, los medios y altos aún no se pero se me ocurre que pueden mover la velocidad y saturación del color.

en cuanto a interactividad tengo pensado que la perosna pueda definir la dirección en la que se mueven los pescados, lo pienso como un cardumen de pescados y como elegí yellow submarine entonces que se vuelvan amarillos cuando se toque la pantalla.

en ese caso necesito varias cosas desde el cliente mobile saber cuando termina y empieza un toque Y cuadno hay un toque, de esta forma podrá saber cuando volver al comportamiento nomral y cuando ir en una dirección.

entonces para eso diría que hay que añadir dos metodos adicionales en el pescado para que: 1. reaccione a la múscia, 2. cambie su comportamiento. PERO eso no es problema mio, solo necesito definir como va a ser la comunicación entre clientes y servidor.

<img width="526" height="470" alt="image" src="https://github.com/user-attachments/assets/e608064d-f784-462d-ad37-4657be7b9538" />

<img width="714" height="319" alt="image" src="https://github.com/user-attachments/assets/346827b4-c841-44dd-acc8-da280cb7813a" />

## desktop

```js
let fishes = [];
let numFish = 80;
let fft, song;
let audioStarted = false;

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

  for (let f of fishes) {
    f.reactToMusic(bass, mid, treble);
    f.updateBehavior(targetDir, bass);
    f.update();
    f.display();
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
```
## mobile

```js
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

# EVIDENCIAS


