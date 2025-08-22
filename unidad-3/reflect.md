# Unidad 3


## 🤔 Fase: Reflect

__Parte 1: recuperación de conocimiento__

- Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?
  - Los componentes fundamentales de una máquina de estados son las acciones, eventos, estados y las condiciones de guarda. La máquina de estados es un proceso que dicta que hace por medio de estados y también realiza acciones al mismo tiempo.
- Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?
  - Le permite realizar varias tareas al mismo tiempo, de esta forma se pueden añadir nuevas funcionalidades sin ningún problema. Sleep() por otro lado apaga todo el sistema y evita que se realicen otras tareas al mismo tiempo
- Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?
  - La misma funcionalidad que la contraseña pero en vez de cambiar de estado y reiniciar el conteo lo divide entre dos.
- Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.
  - Un vector de prueba es una herramienta utilizada para predecir el comportamiento del programa e identificar errores.

__Parte 2: reflexión sobre tu proceso__

- ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?
  - Implementar la contraseña en p5js, más que todo por que eran las 11 de la noche y estaba muy cansado.
- Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?
  - El error principal que tuve fue a la hora de implementar la contraseña pues no estaba seguro de la sintaxis del for en js.
- El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?
  - Monté dos funciones, una que dicta los comportamientos internos de la clase y otra que dibuja en el canvas, e iba implementado por estado.
- Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?
  - En un artefacto dígital que esté chequeando constantemente diferentes inputs y realizando acciones superpuestas.
 
__Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?__

Cuando implementamos la contraseña por que ahí realmente noté que una máquina de estados es capaz de realizar varias tareas complejas al mismo tiempo.

__Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?__

No realmente, yo creo que lo que más se acerca fue la primera de la bomba, pero solamente por que en micro:bit editor existen funciones que no sabiamos que eran como un sleep() entonces lo único sería explicar eso.

La actividad de p5js y microbit me parece que habría que darle prioridad. No todos tienen un microbit :(

__Empezar a hacer: ¿Qué te habría ayudado a entender mejor?__

Una explicación sobre como se maneja el tiempo en estos programas, pienso que sigue siendo un concepto muy abstracto.

__Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?__

2, me parece más fácil esta sucesión, esto debido a que de esa forma ya se entiende el programa y es mucho más fácil implementarlo.

__Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?__

Pasé muy bueno haciendo ambas bombas, me pareció un excelente ejercicio ese de traducción por que pienso que integra muchas cosas que vimeos adicionando incluso más.
