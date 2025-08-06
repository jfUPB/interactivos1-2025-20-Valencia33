# Unidad 2

## 🔎 Fase: Set + Seek

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 01 🐟

En un principio crea la clase Pixel, donde va a definir los atributoss que tiene un objeto de tipo pixel. En este caso, tiene los siguientes atributos 
 - __state__: que es inicializado como "Init", este será utilizado para definir el estado del pixel, utilizando un if que chequea si el tiempo actual sigue dentro de un intervalo. Por último se cambia su valor a "WaitTimeout" (El otro estado). Un objeto de tipo Pixel tiene dos estados, es decir, dos condiciones de espera. Este "Init" no es un estado de espera por lo que es un pseudoestado.

> __Estado:__ es una condición de espera.

> __Evento:__ es un chequeo.

> __Acciones:__ son actualizaciones y lecturas de variables, basicamente realizar cambios.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

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
- __ESTADOS:__ Las condiciones de espera en este programa son los valores que toma self.state, pues son lo que define las carácteristicas del programa en esa porción de código y cambian después de cierta cantidad de tiempo.
- __EVENTOS:__ Son los if que identifican el estado e indican que acciones siguen.
- __ACCIONES:__ Son todas esas instrucciones que realizan cambios en las variables, entonces cuando se asigna un nuevo estado o cuando se prende y apagan píxeles.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 03 🐟

__Controlando la pantalla con una máquina de estados y concurrencia__

- ¿Cómo es posible estructurar una aplicación usando una máquina de estados para poder atender varios eventos de manera concurrente?

 La forma que se me ocurre es 
  
- ¿Cómo haces para probar que el programa está correcto?

Al iniciar, se muestra una cara feliz durante un segundo y medio. Después, el micro:bit cambia a una expresión sonriente que dura un segundo. Luego, aparece una cara triste durante dos segundos, y el ciclo vuelve a comenzar.

Sin embargo, si en cualquier momento se presiona el botón A mientras la cara feliz o la sonriente están en pantalla, el micro:bit interrumpe el ciclo y muestra inmediatamente la cara triste o feliz, respectivamente. Si se presiona el botón A mientras la cara triste está en pantalla, el dispositivo cambia a la expresión sonriente.

<img width="838" height="1022" alt="image" src="https://github.com/user-attachments/assets/9eba4c8f-4a6c-44b9-80fb-5efd8f566593" />

___

> __Vectores de prueba:__ Se utilizan para graficar esas condiciones que van a generar un cambio de estado.

 - __Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.__

En cada frame hace dos chequeos por estado; si el intervalo ya se cumplió y si el botón A fue presionado.

 - __Identifica los estados, eventos y acciones en el programa.__
   - __ESTADOS:__ Son las condiciones de espera representadas como happy, smile y sad.
   - __EVENTOS:__ Son las comparaciones del tiempo actual con el intervalo y si ya se presionó el botón A.
   - __ACCIONES:__ Cada que se actualiza el display o se hace un cambio en la variables interval.
 - __Describe y aplica al menos 3 vectores de prueba para el programa.__
 Por ejemplo cada vez que sucede un cambio de estado este ocurre o por el tiempo actual, que superó el intervalo (condición inicial), o porque se presionó el botón A. En ambos casos el resultado esperado es que se cambie de estado.
