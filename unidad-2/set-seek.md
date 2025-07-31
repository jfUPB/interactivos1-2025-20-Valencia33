# Unidad 2

## 🔎 Fase: Set + Seek

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 01 🐟

En un principio crea la clase Pixel, donde va a definir los atributoss que tiene un objeto de tipo pixel. En este caso, tiene los siguientes atributos 
 - __state__: que es inicializado como "Init", este será utilizado para definir el estado del pixel, utilizando un if que chequea si el tiempo actual sigue dentro de un intervalo. Por último se cambia su valor a "WaitTimeout" (El otro estado). Un objeto de tipo Pixel tiene dos estados, es decir, dos condiciones de espera. Este "Init" no es un estado de espera por lo que es un pseudoestado.

> __Estado:__ es una condición de espera.

> __Evento:__ es un chequeo.

> __Acciones:__ son actualizaciones y lecturas de variables, basicamente realizar cambios.

### 🐟 Actividad 02 🐟

```python
from microbit import *
import utime

class Semaforo:
    def __init__(self):
        self.state = "Verde"
        self.startTime = 0

    def update(self):
        if self.state == "Verde":
            display.set_pixel(0,0,9)
            sleep(8000)
            self.state = "Amarillo"
            display.set_pixel(0,0,0)
            
        elif self.state == "Amarillo":
            display.set_pixel(0,1,9)
            sleep(3000)
            self.state = "Rojo"
            display.set_pixel(0,1,0)

        elif self.state == "Rojo":        
            display.set_pixel(0,2,9)
            sleep(8000)
            self.state = "Verde"
            display.set_pixel(0,2,0)

semaforo1 = Semaforo()

while True:
    semaforo1.update()
```
