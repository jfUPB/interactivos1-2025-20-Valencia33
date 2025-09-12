
# Evidencias de la unidad 5

# Set / Seek

## Actividad 1

- **Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

El microbit lo que hace es que manda un "array" de valores con el nombre **data**, realmente no es un array, es más un formato de texto que se le da a los siguientes atributos: xValue, yValue, aState y bState. Esta variable **data** es lo que se manda por el serial, un ejemplo de como se vería sería así: 1000, 900, true, false\n. Una vez p5.js recibe esa información entonces corta ese string cada vez que haya una coma y deja de hacerlo cuando encuentre "\n".

- **¿Cómo es la estructura del protocolo ASCII usado?**

No tengo ni idea a que se refiere con protocolo ASCII pero creo que es el como se pasan los datos. En este caso es un string como lo expliqué en el punto anterior, y los valores que se pasan van de -1024 a 1024 para xValue y yValue y de true a false en aState y bState donde ambos son pasados como strings.

- **Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**

En esta porción de código es donde se reciben los datos del microbit, lo que hace es que lee y separa la string que recibe cada que encuentre una coma, espera que esos datos vengan un orden predeterminado puesto que justo despues los mete en un array que se llama values, el cual almacena strings. Despues de dividir y guardar la string debe de hacer otros procesos puesto que xValue y yValue son enteros y aState y bState son booleanos, entonces le hace el parse a Int a los dos primeros y lo mismo con los dos últimos pero a bool.

Ya para xValue y yValue hace que sus valores correspondan con las dimensiones de la pantalla, sumandoles la mitad de la altura y el ancho. De esta forma ahora xValue y yValue pueden ser utilizados para representar coordenadas en la pantalla.

<img width="546" height="300" alt="image" src="https://github.com/user-attachments/assets/81ee256b-d888-4cbf-8505-87358df450e4" />

- **¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**

Para ambos hace uso de una variable adicional que sirve para chequear el estado de los botones en el frame anterior, de esta forma se sabe si fueron presionados o si los soltaron. Esos son los chequeos que se realizan. Para **Apressed** lo que hace es que mira si newAState es true y precNewAState es falso, como el valor de prevNewAState es definido al final de cada frame entonces se entiende que si esa condición es true entonces A acaba de ser presionado.

Para **Bpressed** es lo mismo pero se chequea si newBState == false y prevNewBState == true, de esta forma se sabe que en el frame anterior B estaba presionado pero en este no, lo que significa que B fue soltado.

Aunque realmente la pregunta la pude haber respondido que se hacía con un print().

<img width="594" height="328" alt="image" src="https://github.com/user-attachments/assets/1d648c8f-55bf-42e4-bbe4-2ef9904d0466" />

- **Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.**

<img width="984" height="855" alt="20250910_171838" src="https://github.com/user-attachments/assets/e4f89c64-c748-466d-9e77-ba116fcfc173" />

<img width="984" height="855" alt="20250910_172304" src="https://github.com/user-attachments/assets/d5b84bbc-aa73-4d2e-a842-addfc7e794f8" />

<img width="984" height="855" alt="20250910_172603" src="https://github.com/user-attachments/assets/366498ad-7ad1-49af-a20f-29524f2e798c" />

## Actividad 2

> El módulo struct permite empaquetar los datos en un formato binario. En este caso,
el formato '>2h2B' indica que se envían 2 enteros cortos (xValue, yValue) y 2 enteros
sin signo (aState, bState). El símbolo > indica que los datos se envían en orden de
bytes grande (big-endian), lo que significa que el byte más significativo se envía primero.
El formato 2h indica que se envían 2 enteros cortos de 2 bytes cada uno (xValue, yValue),
y 2B indica que se envían 2 enteros sin signo de 1 byte cada uno (aState, bState).

### 🧐🧪✍️ EXPERIMENTO 1

<img width="169" height="156" alt="image" src="https://github.com/user-attachments/assets/fcc1e718-ef1c-49c4-89ca-4be21820b4bc" />

Este resultado se ve por que esos son los datos que están siendo guardados en las variables xValue, yValue, aState y bState.


### 🧐🧪✍️ EXPERIMENTO 2

<img width="971" height="174" alt="image" src="https://github.com/user-attachments/assets/cd5ecd17-e4ff-4bca-a6b3-02354bc86ebc" />

Este resultado es mucho mas complicado de entender, puesto que hay que interpretar cada segmento del texto entregado. Por lo que entiendo cada "renglón" está definido por "ciclos", uno de estos ciclos se vería así: **0a3138 34 2c 39 38 34 2c 46 61 6c 73 65 2c 46 61 6c 73 65** y no tengo la menor idea de que significa cada cosa.

- **¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?**

Las ventajas es que manda datos más rápido, pues al menos observé que se entregaban lineas y lineas de código mucho más rápido **PERO** no entiendo nada y no se me ocurre como utilizar esos datos en p5js.

## Actividad 3

### 🧐🧪✍️ EXPERIMENTO 1: Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

En la unidad anterior era necesario estos pasos extra puesto que se mandaba la información por medio de una string, entonces para poder trabajar con los datos que mandamos debemos separar y clasificar, en esta unidad esto no se hace por que se utiliza la biblioteca struct que permite mandar paquetes de datos y tambien por que los datos que se reciben son int y strings. Tambien es por que mandamos todo por un puerto.

### 🧐🧪✍️ EXPERIMENTO 2: Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?

```
if (port.availableBytes() >= 6) {
    let data = port.readBytes(6);
    if (data) {
    const buffer = new Uint8Array(data).buffer;
    const view = new DataView(buffer);
    microBitX = view.getInt16(0);
    microBitY = view.getInt16(2);
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);

    print(`microBitX: ${microBitX} microBitY: ${microBitY} microBitAState: ${microBitAState} microBitBState: ${microBitBState} \n` );

    /*
    microBitX = int(values[0]) + windowWidth / 2;
    microBitY = int(values[1]) + windowHeight / 2;
    microBitAState = values[2].toLowerCase() === "true";
    microBitBState = values[3].toLowerCase() === "true";
    updateButtonStates(microBitAState, microBitBState);
    */

    }
}
```
En un principio observo que está chequeando si los bytes disponibles son mayor o iguales a 6, en ejercicios anteriores esto no sucedía, solamente chequeaba si había uno. Adiconalmente cuando crea la variable data lee los 6 primeros bytes, a diferencia de los otros ejercicios en los cuales solo leía el primer byte.

Por otra parte crea dos variables: La primera es buffer cuyo valor es un array de Uints de 8 bytes de data. Otra de estas variables es view.

Ya las demás si entiendo como las recibe y convierte a un valor con el que se pueda trabajar. lo que hace para cada uno de los valores es que les hace un parse a int pero a los valores a los que les hace el parse tienen unos valores muy arbitrarios 0 y 2, no sé por que por que eso no corresponde al orden con el que se mandaron desde el microbit. Para microBitAState y microBitBState tambien les hace un parse a uint pero utiliza el operador "===" para convertilos a true o false si cumplen con que = 1.

### 🧐🧪✍️ EXPERIMENTO 3:  ¿Qué ves en la consola? ¿Por qué crees que se produce este error?

<img width="755" height="105" alt="image" src="https://github.com/user-attachments/assets/921ed8ea-127a-4497-bb99-d8c94acf5763" />

La razón de este error se me ocurre que es por que en ninguna parte del código se delimitó un final del paquete, entonces pienso que lo que está pasando es que está leyendo muchos valores, sin ningún orden y se lo está asignando a variables que nada que ver.

```
function readSerialData() {
  // Acumula los bytes recibidos en el buffer
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  // Procesa el buffer mientras tenga al menos 8 bytes (tamaño de un paquete)
  while (serialBuffer.length >= 8) {
    // Busca el header (0xAA)
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift(); // Descarta bytes hasta encontrar el header
      continue;
    }

    // Si hay menos de 8 bytes, espera a que llegue el paquete completo
    if (serialBuffer.length < 8) break;

    // Extrae los 8 bytes del paquete
    let packet = serialBuffer.slice(0, 8);
    serialBuffer.splice(0, 8); // Elimina el paquete procesado del buffer

    // Separa datos y checksum
    let dataBytes = packet.slice(1, 7);
    let receivedChecksum = packet[7];
    // Calcula el checksum sumando los datos y aplicando módulo 256
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue; // Descarta el paquete si el checksum no es válido
    }

    // Si el paquete es válido, extrae los valores
    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX = view.getInt16(0);
    microBitY = view.getInt16(2);
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);

    console.log(
      `microBitX: ${microBitX} microBitY: ${microBitY} microBitAState: ${microBitAState} microBitBState: ${microBitBState}`
    );
  }
}
```

### 🧐🧪✍️ EXPERIMENTO 4: ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?

La diferencia en el código del microbit es que ahora crea un paquete base al cual le añade un byte inicial y de último un byte que corresponde al resultado de data % 256, para chequear que todos los bytes están llenos.

Ya en p5js lo que se hace es que busca el header y si no lo encuentra entonces descarta esos bytes. además tambien chequea que llegue la información completa y una vez está sale de ese if y corta el paquete por partes, del 1 - 7 lo guarda en data bytes y el último dato lo guarda (este corresponde al checksum).

Adicionalmente, desde p5js calcula un checksum con los datos recogidos y lo compara con el que llegó, ya si el paquete es válido entonces ahí si guarda los datos.

# Apply

Código microbit

```
from microbit import *
import struct

uart.init(115200)
display.set_pixel(0, 0, 9)

while True:
    xValue = accelerometer.get_x()
    yValue = accelerometer.get_y()
    aState = button_a.is_pressed()
    bState = button_b.is_pressed()
    data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
    checksum = sum(data) % 256
    packet = b'\xAA' + data + bytes([checksum])
    uart.write(packet)
    sleep(100)
```

Código original p5js

```
// M_1_4_01
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * creates a terrain like mesh based on noise values.
 *
 * MOUSE
 * position x/y + left drag   : specify noise input range
 * position x/y + right drag  : camera controls
 *
 * KEYS
 * arrow up                   : noise falloff +
 * arrow down                 : noise falloff -
 * arrow left                 : noise octaves -
 * arrow right                : noise octaves +
 * space                      : new noise seed
 * +                          : zoom in
 * -                          : zoom out
 * s                          : save png
 */

// ------ mesh ------
var tileCount;
var zScale;

// ------ noise ------
var noiseXRange;
var noiseYRange;
var octaves;
var falloff;

// ------ mesh coloring ------
var midColor;
var topColor;
var bottomColor;
var strokeColor;
var threshold;

// ------ mouse interaction ------
var offsetX;
var offsetY;
var clickX;
var clickY;
var zoom;
var rotationX;
var rotationZ;
var targetRotationX;
var targetRotationZ;
var clickRotationX;
var clickRotationZ;

let port;
let connectBtn;
let connectionInitialized = false;

let microBitX = 0;
let microBitY = 0;
let microBitAState = false;
let microBitBState = false;

let prevmicroBitAState = false;
let prevmicroBitBState = false;

function setup() {
  createCanvas(600, 600, WEBGL);
  colorMode(HSB, 360, 100, 100);
  
  port = createSerial();
  connectBtn = createButton('Connect to micro:bit');
  connectBtn.position(10, 10);
  connectBtn.mousePressed(connectBtnClick);
  
  cursor(CROSS);

  // ------ mesh ------
  tileCount = 50;
  zScale = 150;

  // ------ noise ------
  noiseXRange = 10;
  noiseYRange = 10;
  octaves = 4;
  falloff = 0.5;

  // ------ mesh coloring ------
  topColor = color(0, 0, 100);
  midColor = color(75, 99, 63);
  bottomColor = color(0, 0, 0);
  strokeColor = color(180, 0);
  threshold = 0.30;

  // ------ mouse interaction ------
  offsetX = 0;
  offsetY = 0;
  clickX = 0;
  clickY = 0;
  zoom = -300;
  rotationX = 0;
  rotationZ = 0;
  targetRotationX = PI / 3;
  targetRotationZ = 0;
}

function draw() {
  background(180,100,50);
  ambientLight(150);
  
  // ------ microbit data ------
  
   if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
    microBitConnected = false;
  } 
  else {
    microBitConnected = true;
    connectBtn.html("Disconnect");
  }

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }
  
   if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;
          microBitY = int(values[1]) + windowHeight / 2;
          microBitAState = values[2].toLowerCase() === "true";
          microBitBState = values[3].toLowerCase() === "true";
          updateButtonStates(microBitAState, microBitBState);
        } else {
          print("No se están recibiendo 4 datos del micro:bit");
        }
      }
    }

  // ------ set view ------
  push();
  translate(width * 0.05, height * 0.05, zoom);
  
  //En esta parte es complejo hacer el cambio puesto que son inputs juntos, por lo que un solo botón no es suficiente, lo que voy a hacer es eliminar el check.

  rotationX += (targetRotationX - rotationX) * 0.25;
  rotationZ += (targetRotationZ - rotationZ) * 0.25;
  rotateX(-rotationX);
  rotateZ(-rotationZ);

  // ------ mesh noise ------
    noiseXRange = microBitX / 100;
    noiseYRange = microBitY / 100;


  noiseDetail(octaves, falloff);
  var noiseYMax = 0;

  var tileSizeY = height / tileCount;
  var noiseStepY = noiseYRange / tileCount;

  for (var meshY = 0; meshY <= tileCount; meshY++) {
    beginShape(TRIANGLE_STRIP);
    for (var meshX = 0; meshX <= tileCount; meshX++) {

      var x = map(meshX, 0, tileCount, -width / 2, width / 2);
      var y = map(meshY, 0, tileCount, -height / 2, height / 2);

      var noiseX = map(meshX, 0, tileCount, 0, noiseXRange);
      var noiseY = map(meshY, 0, tileCount, 0, noiseYRange);
      var z1 = noise(noiseX, noiseY);
      var z2 = noise(noiseX, noiseY + noiseStepY);

      noiseYMax = max(noiseYMax, z1);
      var interColor;
      colorMode(RGB);
      var amount;
      if (z1 <= threshold) {
        amount = map(z1, 0, threshold, 0.15, 1);
        interColor = lerpColor(bottomColor, midColor, amount);
      } else {
        amount = map(z1, threshold, noiseYMax, 0, 1);
        interColor = lerpColor(midColor, topColor, amount);
      }
      fill(interColor);
      stroke(strokeColor);
      strokeWeight(0);
      vertex(x, y, z1 * zScale);
      vertex(x, y + tileSizeY, z2 * zScale);
    }
    endShape();
  }
  pop();
  
  if (falloff > 1.0) falloff = 1.0;
  if (falloff < 0.0) falloff = 0.0;

  if (keyCode == LEFT_ARROW) octaves--; //INPUT A
  if (keyCode == RIGHT_ARROW) octaves++; //INPUT B
  if (octaves < 0) octaves = 0;

  if (zoom < -700) zoom = -700; // '+' //INPUT A + ALGO
  if (zoom > -340) zoom = -340; // '-' //INPUT B + ALGO

  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png'); //TOUCH PERO JUANFERFRANCO ME PEGA
  if (key == ' ') noiseSeed(floor(random(100000)));

}

function mousePressed() {
  clickX = microBitX;
  clickY = microBitY;
  clickRotationX = rotationX;
  clickRotationZ = rotationZ;
}

function keyReleased() {


}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}

function updateButtonStates(newAState, newBState) {
  
  if(microBitY <= 900)
    {
      
  if(newAState)
    {
      falloff += 0.1
      zoom += 20
    }
  else if(newBState)
    {
      falloff -= 0.1
      zoom -= 20
    }
      
    }
  else if ( microBitY > 900) {
    
    if(newAState)
      {
        offsetX += 50 - clickX;
      }
    if(newBState)
      {
        offsetX -= 50 - clickX;
      }
    
    targetRotationX = min(max(clickRotationX + offsetY / float(width) * TWO_PI, -HALF_PI), HALF_PI);
    targetRotationZ = clickRotationZ + offsetX / float(height) * TWO_PI;
  }

     else if ( microBitY<900){
       
       offsetY +=50
         console.log(offsetY)
    
    if(newAState)
      {
        offsetY -= 50 - clickX
      }
    if(newBState)
      {
        offsetY-= 50 - clickX
      }
    
    targetRotationX = min(max(clickRotationX + offsetY / float(width) * TWO_PI, -HALF_PI), HALF_PI);
    targetRotationZ = clickRotationZ + offsetX / float(height) * TWO_PI;
  }
  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}
```

## Proceso de construcción
