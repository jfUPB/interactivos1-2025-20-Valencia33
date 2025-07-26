# Unidad 1

## 🤔 Fase: Reflect

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

___
___

### 🐟 Actividad 7 🐟

__Parte 1: recuperación de conocimiento__

1) __Basándote en los ejemplos que vimos de sistemas físicos interactivos al iniciar el curso, describe las tres características que definen a un sistema físico interactivo.__

 - Necesitan un input que sea un fenomeno físico, un algoritmo que utilice las carácteristicas de aquel estimulo, y el output que es fuertermente influenciado por esa entrada. 

2) __Explica el modelo input-process-output de Patrick Hübner usando como ejemplo el sistema que construiste con micro:bit y p5.js en la Actividad 06. ¿Cuál fue el input, cuál fue el proceso y cuál fue el output?__

 - En este sistema el input sería el botón A desde el micro:bit y su output sería la pantalla en p5.js. Sin embargo también se podría ver como desde el punto de vista del microbit este tiene un input que sería el botón A y un output que sería el cable y desde el punto de vista de p5.js sería input el cable y output los cambios en el canva. Mientras que el proceso es todo ese intercambio de datos entre el computador y el micro:bit, que no solo son esa comunicación si no que tambien son la interpretación de esos datos de llegada a p5.js o esos datos de devuelta en el micro:bit.

3) __¿Cuál es la función de la línea uart.write('A') en el código del micro:bit y qué función en p5.js se encarga de “escuchar” ese mensaje?__

 - Lo fundamental en esa línea de código es el indicador "uart" que se refiere a la forma del micro:bit de mandar información por el puerto serial, que es la parte que utiliza p5.js para escuchar aquellas instrucciones, y lo hace por medio de la función createSerial(), que permite abrir y cerrar el serial o leer los puertos de llegada, que sería donde leería la información que le manda el micro:bit.

4) __¿Cuál es la diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo?__

 - Que el arte generativo hace uso de un programa que lee la entrada del artista y a partir de algunos parametros predeterminados por el autor, afecta y genera arte. Es decir, es arte con el soporte de un programa.  

5) __Imagina que quieres que un círculo en p5.js cambie a un color aleatorio cada vez que sacudes el micro:bit. Describe qué tendrías que programar en el micro:bit y qué tendrías que programar en p5.js para lograrlo.__

 - desde el editor de python se debe de hacer una referencia a la función que detecta el acerelometro, no se que nombre tendra esa función o que valores devuelva, me imagino que un bool es suficiente. En todo caso, un if que detecte si el acerelometro está siendo activado para despues utilizar uart.write('A'), que va a ser el dato que va a recibir p5.js. Es importante considerar la posibilidad de que el micro:bit no esté siendo agitado, en cuyo caso debería mandar otro dato en vez de A, esto con el fin de que en p5.js, se evite que con solo agitar una vez el color cambie aleatoriamente indefinidamente.
 - desde p5.js se va a abrir el serial y se va a leer el puerto número 1, y cada frame se va a chequear si recibió la "A" que mandó el micro:bit, en caso de que si lo reciba entonces se va a correr la siguiente línea fill(random(0,255),random(0,255),random(0,255)). Se añade un else if para recibir todos los datos que no sean "A" y así dejar de cambiar el color. Se me ocurre que se pueden crear tres variables (r,g,b) que sean un random entre 0 y 255 para de esa forma mantener el último color cuando no esté siendo agitado.

___

__Parte 2: reflexión sobre tu proceso__

1) __¿Qué fue más desafiante para ti en esta unidad: la parte conceptual (entender qué es un sistema físico interactivo) o la parte técnica (hacer que el micro:bit y p5.js se comunicaran)? ¿Por qué?__

 - Lo más desafiante para mi de esta unidad fue comprender como realmente trabajan las funciones de la biblioteca del micro:bit tanto en python como en p5.js. Por ejemplo, vi que en el ejemplo de la actividad 5 hacia un check de si había bytes libres antes de recibir información, y a pesar de que pues suena cómo algo lógico en el marco del ejercicio para nosotros que lo vemos por primera vez es cuestión de aceptarlo y ya, lo mismo con la creación del serial, o por que se lee el puerto 1 y no otro, me pareció confuso, y aunque no puedo decir que lo comprendo por completo eventualmente lo acepto.

2) __Describe el momento “¡Aha!” que tuviste cuando lograste que una acción en el micro:bit (presionar un botón, sacudirlo) tuviera un efecto visible en el canvas de p5.js por primera vez. ¿Qué fue lo que entendiste en ese instante?__

 - Los procesos del micro:bit me parecieron bastante intuitivos entonces realmente no tuve alguna dificultad de la que estuviera muy contento de haber resuelto. Sin embargo, si recuerdo que en la actividad 4 tuve que leer bastante de la documentación de p5.js para lograr el resultado que quería. Recuerdo en particular cuando intenté usar la función translate() por primera vez, pues a pesar de que es una función bastante intuitiva, a mi al principio se me complicó, en gran parte por que las coordenadas a las que estaba trasladando cambiaban con respecto al tiempo, por lo que entender ese cambio de coordenadas en cualquier acción posterior fue complejo, pero una vez lo descifré me puse muy contento.

3) __Al inicio de la unidad te pregunté: “¿Este curso para qué me sirve?”. Después de experimentar y construir tu primer prototipo, ¿Cómo ha cambiado o se ha vuelto más concreta tu respuesta a esa pregunta?__

 - No ha cambiado mucho, si algo me entusiasma más la idea de aprender por que pienso que tiene mucho más potencial del que le di crédito en un principio, sin embargo no fue una respuesta equivocada, más bien fue falta de visión por que este tipo de sistemas se pueden implementar en cualquier campo.

4) __El tutorial de la Actividad 05 te llevó paso a paso. ¿Cómo te sentiste con ese método de aprendizaje? ¿Te dio seguridad o preferirías haberlo intentado por tu cuenta desde el principio?__

 - Pienso que se justifica pero solo por el uso de las bibliotecas adicionales de micro:bit, sin embargo si me parece mejor cuando los ejercicios son autónomos por que dan la posibilidad de explorar más las documentaciones y la oportunidad de equivocarse, que en mi opinión, es una parte fundamental del aprendizaje.

___
___

### 🐟 Actividad 9 🐟

1) __Continuar: ¿Qué actividad, video o ejemplo de esta unidad te resultó más inspirador o te ayudó más a entender el potencial de los sistemas físicos interactivos?__

 - Me gustó bastante el video sobre el logo de la filarmonica de Frankfurt, no tanto por que la visualización me haya parecido super wow, sino mas por las versatilidad que tienen los sistemas físicos interactivos, se pueden aplicar en muchas áreas, incluso en aquella que no requieran un toque artistico.

2) __Dejar de hacer: ¿Hubo alguna parte que te pareció demasiado abstracta, muy rápida o confusa? ¿Hay algo que crees que podríamos cambiar para que sea más claro?__

 - Personalmente la parte física del micro:bit no me quedó tan claro pienso que las partes de este que se explicaron en clase estaban muy centradas en lo que ibamos a hacer, cuando me parece mejor mostrar un producto final que sea impresionante, que demuestre el potencial del micro:bit para incrementar las posibilidades de aprender por cuenta propia.

3) __Empezar a hacer: ¿Qué te genera más curiosidad ahora? ¿Te gustaría explorar más sensores del micro:bit (luz, temperatura), crear visualizaciones más complejas en p5.js o ver más ejemplos de proyectos artísticos?__

 - Me gustaría explorar más en p5.js, me encantó cómo funciona, super versatil, de por si con ninguna librería tiene un potencial gigantesco y ahí viendo los ejemplos que están en la pagina principal me diero ganas de llevar al máximo este programa. La pasé excelente haciendo el programa de la actividad 4 y me encantaría ver más actividades utilizando esa plataforma.

4) __Balance inspiración vs. técnica: ¿Cómo sentiste el equilibrio entre ver los videos inspiradores de la Actividad 01 y la parte técnica de conectar las herramientas en las actividades 03-06?__

 - Me gusta el balance que hubo, sin embargo me encantaría que el profesor presentara más trabajos de compañeros nuestros, siento que eso hace que tengamos expectativas más realistas del curso.

5) __Comentario adicional: ¿Hay algo más que quieras compartir sobre tu experiencia en esta unidad introductoria?__

 - Que posterior a las actividades prácticas tengo expectativas altas de lo que sigue del curso, que me interesa bastante.

___
___
___

