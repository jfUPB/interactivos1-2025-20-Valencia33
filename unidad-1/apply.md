# Unidad 1

## 🛠 Fase: Apply

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 5 🐟

En este sistema el input sería el botón A desde el micro:bit y su output sería la pantalla en p5.js. Sin embargo también se podría ver como desde el punto de vista del microbit este tiene un input que sería el botón A y un output que sería el cable y desde el punto de vista de p5.js sería input el cable y output los cambios en el canva.

- El microbit tiene un loop infinito en el que chequea si el botón A es presionado, en caso de que lo sea, le manda una "A" a p5js.
- En p5js se crea un botón que abre el puerto para recibir información, y posteriormente en cada frame chequea si le llegó la "A" que mandó el microbit.

```python
from microbit import *

uart.init(baudrate=115200)

while True:

    if button_a.is_pressed():
        uart.write('A')
    else:
        uart.write('N')

    sleep(100)
```

Desde python el se lee los inputs del micro:bit, chequeando si el botón A fue presionado, en caso de que si sea oprimido manda una "A", y en caso de que no manda constantemente una "N" en un loop infinito, se manda una "N" por que se quiere que el color verde del cuadrado solo se mantenga en los frames en los que el botón A es presionado. Es importante hacer mención de las funciones que cumple las demás líneas de código.

- __from microbit import *__
  
   Se refiere a la biblioteca que da acceso a todas las funciones para el micro:bit.
  
- __uart.init(baudrate=115200)__

  Hace referencia a la velocidad a la que se van a mandar datos. Tengo entendido que uart se refiere a ese transmisor de información.

```javascript
  let port;
  let connectBtn;
  let connectionInitialized = false;

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
        fill("red");
      } else if (dataRx == "N") {
        fill("green");
      }
    }

    rectMode(CENTER);
    rect(width / 2, height / 2, 50, 50);

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
En p5.js se debe de añadir la biblioteca del micro:bit, esta permite utilizar la función de createSerial(), que es lo que nos va a permitir que el micro:bit se comunique con nuestro computador, además de poder también modificar otros parámetros cómo el estado del serial (abierto/cerrado) o leer algún puerto en especial.

- __setup()__

 - Aparte de crear el serial para la comunicación, acá tambien se crea un botón que va a estar encargado de abrir o cerrar el serial, sin embargo esto no es completamente responsabilidad del serial, si no que más bien, este botón al ser presionado llama la función __connectBtnClick()__.

- __draw()__

 - Tiene un if que se encarga de limpiar la información del puerto si y solo si la conexión ya ha sido establecida, de tal forma que siempre que se abra el puerto se va a limpiar la información.
 - Tiene otro if que por lo que entiendo mira a ver si hay bytes disponibles para que se pueda leer, en caso de que si los haya entonces lee el puerto 1 (que sería el que recibe la "A" desde python) y mira que información llegó, si dataRx == "A" entonces fill("red") y si dataRx == "N" entonces hace fill("green").
 - Cambia el pivote del rectángulo y lo crea en la mitad de la pantalla, donde su base y altura son iguales.
 - Por último hay un if encargado del feedback para el usuario, pues cambia la información que presenta el botón dependiendo del estado de conexión al serial.

- __connectBtnClick()__

 - Una vez el botón es presionado se llama esta función que chequea si el puerto está abierto: En caso de que no lo esté, lo abre, le indica la velocidad a la que va a recibir la información y pone connectionInialized = false para realizar la limpieza de datos al principio de la próxima iteración de draw(). En caso de que si lo esté, lo cierra.
   
♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 6 🐟

Este programa es similar al anterior, difieren más que todo en lo que sucede una vez se recibe la información en p5.js. Donde se crea un circulo cuyo color y posición en x dependen del dato recibido en el puerto 1, si la información recibida es "A" entonces hace fill("green") e increment = increment - 10, donde increment reemplaza la posición en X del circulo. Si el dato recibido es "B" entonces hace fill("blue") e increment = increment + 10,

Sin embargo hay un pequeño cambio en micro:bit Python Editor y es que en vez de mandar constantemente la N si no hay un input del botón A, este está constantemente chequeando los botones A y B y si ninguno es presionado no manda ningún dato.

__Código de micro:bit Python Editor__

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
[__Código de p5.js__](https://editor.p5js.org/Valencia33/sketches/diPEWCXJH)

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
