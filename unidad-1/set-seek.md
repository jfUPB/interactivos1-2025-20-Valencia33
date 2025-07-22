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

Además tambien utilizo mouseX y mouseY para controlar la "perspectiva" y el tiempo. 

Este es el código:
```javascript
var colores = [];
let e;
let moonSpeed;
let s;
let m;

function setup() 
{
  createCanvas(800, 800);
  colores = {c1:random(150,255),c2:random(150,255),c3:random(150,255),c4:random(50,255),c5:random(10,200)}
  e = random(150,200);
  moonSpeed = random(0.02,0.05)
}

function draw() 
{
  background('rgba(0, 10, 60, 0.4)');
  noStroke();
  
  if(mouseX > 0 && mouseX < width && mouseY > 0 && mouseY < height)
    {
      s = (mouseY/200)*0.5+0.5
    }
  else
    {
      s=1;
    }
  
  m = (mouseX/400)+0.75
  
  fill(colores.c5,255,colores.c3)
  textAlign(CENTER)
  textSize(29)
  textFont('Comic Sans MS')
  text(int(s*(frameCount/120)) + " AÑOS",70,40)
  
  //son usadas antes de dibujar los planetas
  let x3 = 400 + cos(frameCount*0.02*s)*200;
  let y3 = 400 + sin(frameCount*0.02*s)*(150/m);    
  
  //ellipse
  fill(0,0)
  stroke(255,255,255, 30)
  strokeWeight(1)
  setLineDash([3, 3]);
  
  ellipse(400,400,80,60/m)
  ellipse(400,400,160,120/m)
  ellipse(400,400,400,300/m)
  ellipse(x3,y3,60,60/m)
  ellipse((400 +(e-60)) ,400,2*e,2*(50/m))
  
  noStroke();
  
  //★
  drawingContext.shadowBlur = 10;
  drawingContext.shadowColor = color(255,255,50)
  let x4 = 400 + cos(frameCount*0.02*s)*4;
  let y4 = 400 + sin(frameCount*0.02*s)*2;
  fill(255,255,50);
  circle(x4,y4,30);
  
  
  drawingContext.shadowBlur = 4;
  drawingContext.shadowColor = color(255,255,255,70)
  
  //●
  let x = 400 + cos(frameCount*0.05*s)*80;
  let y = 400 + sin(frameCount*0.05*s)*(60/m);
  fill(colores.c5,255,colores.c3);
  circle(x,y,12);
  
  let x2 = 400 + cos(frameCount*0.1*s)*40;
  let y2 = 400 + sin(frameCount*0.1*s)*(30/m);
  fill(colores.c2,colores.c3,colores.c1);
  circle(x2,y2,7);
  
  
  fill(colores.c3,colores.c4,colores.c2);
  circle(x3,y3,20);
  
  //☄
  
  let c = sqrt((e*e)-(70*70))
  
  let x5 = (400 +(e-60)) + cos(frameCount*(e/10000)*s)*e;
  let y5 = 400 + sin(frameCount*(e/10000)*s)*(50/m);  
  fill(0,152,255);
  circle(x5,y5,5);
  
  //⏾
  translate(x3,y3)
  let x6 = cos(frameCount*(moonSpeed)*s)*30;
  let y6 = sin(frameCount*(moonSpeed)*s)*(30/m);  
  fill(255,colores.c2,colores.c1);
  circle(x6,y6,5);
  
  drawingContext.shadowBlur = 0;
  
  //⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆⋆⁺₊⋆s
  
  let x9 = cos(frameCount*0.02*s)*170;
  let y9 = sin(frameCount*0.02*s)*(100);  
  translate(x9,y9)
  let x7 = cos(frameCount*(random(100,200)*s))*25;
  let y7 = sin(frameCount*(random(100,200)*s))*25;  
  fill(colores.c5,colores.c2,colores.c1);
  circle(x7,y7,5);
}

function keyPressed() 
{
  if (key === 's') 
  {
    saveGif('sistema solar', 25);
  }
}

function setLineDash(list) 
{
  drawingContext.setLineDash(list);
}



```
##### __GIF:__
![sistema solar(4)](https://github.com/user-attachments/assets/f793c771-15ba-4a3a-b1c0-37f9ed907260)




