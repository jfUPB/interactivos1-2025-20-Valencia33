# Unidad 1

## 🛠 Fase: Apply

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 5 🐟

En este sistema el input sería el botón A desde el micro:bit y su output sería la pantalla en p5.js. Sin embargo también se podría ver como desde el punto de vista del microbit este tiene un input que sería el botón A y un output que sería el cable y desde el punto de vista de p5.js sería input el cable y output los cambios en el canva.

- El microbit tiene un loop infinito en el que chequea si el botón A es presionado, en caso de que lo sea, posteriormente le manda una "A" a p5js.
- En p5js se crea un botón que abre el puerto para recibir información, y posteriormente en cada frame chequea si le llegó la "A" que mandó el microbit.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 6 🐟

Código de micro:bit Python Editor

```python
# Imports go at the top
from microbit import *

uart.init(baudrate=115200); #la velocidad a la que se manda info
display.show(Image.HEART);

# Code in a 'while True:' loop repeats forever
while True:
        if button_a.was_pressed():
                uart.write('A'); #uart es para comunicarse con el cosito        
        elif button_b.was_pressed():
                uart.write('B');
    
sleep(100)
```
Código de p5.js

```javascript
let port;
  let connectBtn;
  let connectionInitialized = false;
  let increment = 200;

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
        fill('green')
        increment = increment - 10;
      } else if (dataRx == "B") {
        fill('blue')
        increment = increment + 10;
      }else if (dataRx == "N") {
        fill('red')
        increment = 0;
      }
    }
    
    let x = 200 + increment    

    circle(increment, height/2, 50);

    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }
```
