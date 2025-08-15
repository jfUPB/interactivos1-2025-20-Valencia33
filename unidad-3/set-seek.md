# Unidad 3

## 🔎 Fase: Set + Seek

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 01 🐟

```py
from microbit import *
import utime


class Semaforo:
    
    def __init__(self,x,y,rInterval,yInterval,gInterval):
        self.x = x
        self.y = y
        self.rInterval = rInterval
        self.yInterval = yInterval
        self.gInterval = gInterval
        
        self.startTime = utime.ticks_ms()
        self.interval = self.gInterval
        self.state = "Verde"

    def update(self):
        if self.state == "Verde":
            if utime.ticks_diff(utime.ticks_ms(), self.startTime) >= self.interval:
                display.set_pixel(self.x,self.y,0)
                display.set_pixel(self.x,self.y+1,9)
                self.startTime = utime.ticks_ms()
                self.interval = self.yInterval
                self.state = "Amarillo"
            
        elif self.state == "Amarillo":

            if utime.ticks_diff(utime.ticks_ms(), self.startTime) >= self.interval:
                
                display.set_pixel(self.x,self.y+1,0)
                display.set_pixel(self.x,self.y+2,9)
                self.startTime = utime.ticks_ms()
                self.interval = self.rInterval
                self.state = "Rojo"

        elif self.state == "Rojo":        

            if utime.ticks_diff(utime.ticks_ms(), self.startTime) >= self.interval:
                
                display.set_pixel(self.x,self.y+2,0)
                display.set_pixel(self.x,self.y,9)
                self.startTime = utime.ticks_ms()
                self.interval = self.gInterval
                self.state = "Verde"

semaforo1 = Semaforo(0,0,4000,2000,5000)
semaforo2 = Semaforo(2,0,1000,5000,6000)
semaforo3 = Semaforo(4,0,6000,1000,8000)

while True:
    semaforo1.update()
    semaforo2.update()
    semaforo3.update()
```

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 02 🐟

__En este caso se deben de añadir 3 eventos uno anidado dentro del otro, los eventos detectarían si los botones fueron presionados.__

No sé que tan bien funcione, pues creo que se tendrían que hacer todos los chequeos en un mismo frame, por eso pienso que se pueden añadir una variable bool, que cambie su valor cuando se presione la A durante el estado ARMADO.

Esto se lograría de la siguiente forma:

```py

bool clave = false;

if button_a.was_pressed()
  boton clave = true;
```
Y así por cada botón, de pronto se tendría que añadir más bools entonces puede que no sea la mejor solución.

Pensandolo mejor un bool no sería la mejor opción, mejor un int, entonces si se presiona a tiene un valor, despues un evento que cheque que tiene ese valor o no y chequee por el botón b.


🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 05 🐟

__Crear una tabla con los vectores de prueba.__

| Estado inicial | Evento disparador | Acciones | Estado final|
|----------------|-------------------|----------|-------------|
| |


🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 RETO 🐟

__Utilizar la radio del micro:bit para recibir y mandar instrucciones entre ellos.__

```py
# Imports go at the top
from microbit import *
import utime
import radio

display.clear()

class Event:
    def __init__(self):
        self.value = 0

    def set(self,_val):
        self.value = _val

    def clear(self):
        self.value = 0

    def read(self):
        return self.value


class ReceiveTask:
    def __init__(self):
        radio.config(group=123)
        radio.on()
        pass
    
    def update(self):
        message = radio.receive()
        if message:
            if message == 'A':
                event.set('A')
            elif message == 'B':
                event.set('B')
            elif message == 'S':
                event.set('S')
            elif message == 'T':
                event.set('T')

class BombTask:
    def __init__(self):
        self.PASSWORD = ['A','B','A']
        self.key = ['']*len(self.PASSWORD)
        self.keyindex = 0
        self.count = 20
        self.startTime = utime.ticks_ms()
        self.state = 'CONFIG'
        display.clear()
        display.show(self.count,wait=False)

    def update(self):
        if self.state == 'CONFIG':
            if event.read() == 'A':
                event.clear()
                self.count = min(self.count+1,60)
                display.show(self.count,wait=False)

            if event.read() == 'B':
                event.clear()
                self.count = max(10,self.count-1)
                display.show(self.count, wait=False)

            if event.read() == 'S':
                event.clear()
                self.startTime = utime.ticks_ms()
                self.state = 'ARMED'

        elif self.state == 'ARMED':
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > 1000:
                self.startTime = utime.ticks_ms()
                self.count = self.count - 1
                display.show(self.count,wait=False)
                if self.count == 0:
                    display.show(Image.SKULL)
                    self.state = 'EXPLODED'

            if event.read() == 'A':
                event.clear()
                self.key[self.keyindex] = 'A'
                self.keyindex = self.keyindex + 1

            if event.read() == 'B':
                event.clear()
                self.key[self.keyindex] = 'B'
                self.keyindex = self.keyindex + 1

            if self.keyindex == len(self.key):

                passIsOK = True
                for i in range(len(self.key)):
                    if self.key[i] != self.PASSWORD[i]:
                        passIsOK = False
                        break;
                if passIsOK == True:
                    self.count = 20
                    display.show(self.count,wait=False)
                    self.keyindex = 0
                    self.state = 'CONFIG'
                else:
                    self.keyindex = 0

        elif self.state == 'EXPLODED':
            if event.read() == 'T':
                event.clear()
                self.count = 20
                display.show(self.count,wait=False)
                self.startTime = utime.ticks_ms()
                self.state = 'CONFIG'

bombTask = BombTask()
buttonTask = ReceiveTask()
event = Event()

while True:
    buttonTask.update()
    bombTask.update()
```
