# Unidad 2


## 🤔 Fase: Reflect

### 🐟 Actividad 06 🐟

__Parte 1: recuperación de conocimiento__

- __Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?__

  - Una máquina de estados es aquella que dependiendo de unos eventos cambia de comportamientos y realiza ciertas acciones.

- __Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?__

  - Por que permite realizar varias acciones o chequeos a la vez. Una función como sleep() provoca que todo el sistema se apague cierta cantidad de tiempo, entonces incluso si un programa funciona con sleep(), esto no es lo ideal puesto que no permitiría realizar acciones de más.

- __Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?__

  - Lo pondría en STATE_SHAKE, sería un evento que detecta ese movimiento especifico del acelerometro y posteriormente realiza esa acción de dividir el contador por 2. En el diagrama esto estaría en una transición de STATE_SHAKE a el mismo.

- __Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.__

  - Un vector de prueba es utilizado para simular como un programa reaccionaría a una serie de inputs, hace parte principalmente de predecir como va a funcionar un programa y sirve para identificar cualquier comportamiento inesperado del programa.

__Parte 2: reflexión sobre tu proceso__

- __¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?__

  - Yo diría que encontrar la mejor forma de mostrar el tiempo, en un principio intenté hacer una barrita con todos los pixeles del display, eso fue muy complicado entonces hice lo del tiempo que pedía, fue complejo por que utilicé scroll y al parecer eso es como un sleep(), en el sentido en que apaga todo el programa solo para eso, entonces no es lo mejor.

- __Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?__

  - Que se me olvidó cambiar de estado, entonces incluso si el código en cuanto a eventos y acciones estaba bien al no cambiar de estado no pasaba nada, entonces identificar este error sirvió para reevaluar lo que había escrito.

- __El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?__

  - Empezar con el diagrama, de esa forma pude dimensionar el problema mejor, de forma más organizada, por lo que al empezar a escribir el código fue bastante directo, en el sentido que no tuve que parar a pensar generalidades del código, solo aquellas partes específicas.

- __Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?__

  - En general cualquier sistema que requiera tener en cuenta diferentes inputs del usuario. 
