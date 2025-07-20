# _Unidad 1_

## 🔎 Fase: Set + Seek

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 1 🐟

- ¿Qué es un sistema __físico interactivo__?

Un sistema físico interactivo se refiere a aquellos programas que reciben como input cualquier fenómeno físico con el que el usuario tenga la capacidad de interactuar. Posteriormente, este es procesado por un algoritmo y dependiendo de los parámetros definidos dentro del programa el output está fuertemente relacionado con aquellos sucesos físicos.

- ¿Cómo podrías aplicar lo que has visto en tu __perfil profesional__?

En el marco de la animación se me ocurren varios casos en los que un sistema físico interactivo puede ser útil. De por si los ejemplos que el profesor presentó en clase se me ocurre que se pueden lograr cosas maravillosas con una animación en tiempo real que depende de las acciones de un usuario, asimismo, me parece que tambien es una excelente herramienta para lograr efectos o experiencias fuertemente personalizadas, en este caso se me ocurre que un proyecto parecido al de la compañera con la canción de AURORA se presta para muchas cosas en una animación común y corriente, donde se reciba la música y esta devuelva una experiencia única.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 2 🐟

- __¿Qué es el diseño/arte generativo?__

Es una práctica donde se hace uso de un programa que sigue una serie de parametros e instrucciones ingresadas por el humano y que tiene como output muchas variaciones donde los parametros son alterados.

- __¿Cómo podrías aplicar lo que has visto en tu perfil profesional?__

En el campo de la animación el arte generativo puede ser utilizado para lograr variaciones infinitas en las animaciones, es decir lograr animación procedural y de esa forma integrarlo en los diferentes proyectos, en especial animación para videojuegos, sin embargo, se me ocurre que es una herramienta útil siempre y cuando se quiera lograr un resultado único.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 3 🐟

♦︎ _Inputs_

Los inputs de este programa son los botones del microbit y el acelerometro que tiene, además tambien en p5.js tambien el botón "send love" es considerado un input puesto que abre el puerto y manda la instrucción, el cable tambien sería el input por medio del serial que lo abre

♦︎ _Outputs_

Los outputs de este programa sería tanto los LEDs del microbit como el circulito en p5.js

♦︎ _Proceso_

El proceso empieza una vez se corre el prgrama en el microbit donde muestra la imagen de la mariposa, posteriormente está chequeando el input de los botones A, B, C y el acelerometro, que van directamente a la pantalla de LEDs.
Además tambien esta conectado en p5.js donde se crea el canva y se maneja el input del botón creado en ese mismo canva, que si es precionado le manda por el serial al microbit, que lo detecta como otro input. Y a su vez tambien actualiza el canva.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 4 🐟

Aquí está [mi programa.](https://editor.p5js.org/Valencia33/sketches/hzRt0JF7i)

En este programa utilicé cos() y sen() para hacer las orbitas de todos los planetas, esto junto con random() para modificar parametros tanto de la velocidad con la que giran, como sus colores y la excentricidad del cometa. También intenté hacer un cinturón de asteroides pero quedó más como un radar, igual me gustó entonces lo dejé así.

Este es el código:
```javascript
var colores = [];
let e;
let moonSpeed;

function setup() {
  createCanvas(800, 800);
  colores = {c1:random(100,255),c2:random(100,255),c3:random(100,255),c4:random(50,255),c5:random(10,200)}
  e = random(170,200);
  moonSpeed = random(0.02,0.05)
}

function draw() {
  background('rgba(10, 10, 50, 0.10)');
  noStroke();
  
  //★
  let x4 = 400 + cos(frameCount*0.02)*4;
  let y4 = 400 + sin(frameCount*0.02)*4;
  fill(255,255,0);
  circle(x4,y4,30);
  
  //●
  let x = 400 + cos(frameCount*0.05)*80;
  let y = 400 + sin(frameCount*0.05)*80;
  fill(colores.c5,255,colores.c3);
  circle(x,y,10);
  
  let x2 = 400 + cos(frameCount*0.1)*40;
  let y2 = 400 + sin(frameCount*0.1)*40;
  fill(colores.c2,colores.c3,colores.c1);
  circle(x2,y2,10);
  
  let x3 = 400 + cos(frameCount*0.02)*160;
  let y3 = 400 + sin(frameCount*0.02)*160;  
  fill(colores.c3,colores.c4,colores.c2);
  circle(x3,y3,25);
  
  //☄
  let x5 = 470 + cos(frameCount*(e/10000))*e;
  let y5 = 400 + sin(frameCount*(e/10000))*70;  
  fill(colores.c5,colores.c4,colores.c1);
  circle(x5,y5,5);
  
  //⏾
  translate(x3,y3)
  let x6 = cos(frameCount*(moonSpeed))*30;
  let y6 = sin(frameCount*(moonSpeed))*30;  
  fill(255,colores.c2,colores.c1);
  circle(x6,y6,5);
  
  //⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆
  
  let x9 = cos(frameCount*0.02)*120;
  let y9 = sin(frameCount*0.02)*120;  
  translate(x9,y9)
  let x7 = cos(frameCount*(random(100,200)))*30;
  let y7 = sin(frameCount*(random(100,200)))*30;  
  fill(colores.c5,colores.c2,colores.c1);
  circle(x7,y7,5);
}
```
##### __GIF:__

![sistema solar](https://github.com/user-attachments/assets/5405b1e4-b787-4b12-8fed-d3fb49684e70)

