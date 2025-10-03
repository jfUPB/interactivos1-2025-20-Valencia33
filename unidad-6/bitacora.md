
# Evidencias de la unidad 6

___

## Actividad 1

**PASOS**

  - copiar la URL del repo para clonarlo.
  - abrir la carpeta donde lo quiero guardar con gitbash
  - usar el comando **pwd** para ver en que directorio está la terminal
  - clonarlo con **git clone URL**
  - usar el comando **ls** para ver el listado de cosas en el directorio
  - usar el comando **cd** para cambiar el directorio, completo sería **cd (nombre directorio)**
  - usar el comando **explorer .** para abrir el directorio desde windows
  - usar el comando **code .** para abrir el directorio desde VS
  - **clear** para borrar la consola
  - **npm install** para instalar todas las dependencias
  - hay que levantar el servidor con **npm start**
  - **el servidor se puede matar con ctrl + c**
  - 

___

- **1.) ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?**

  - Lo que hizo fue instalar todas las dependecias que tenía ese repositorio.

- **2.) ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?**

  - Server is listening on http://localhost:3000

significa que el servidor está escuchando los datos que va a mandar esa página web

- **3.) Describe lo que ves inicialmente en page1 y page2 en tu navegador.**

  - Inicialmente se observan dos bolitas rojas conectadas con una línea negra

- **4.) ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**

  - <img width="586" height="377" alt="image" src="https://github.com/user-attachments/assets/1f17be41-9635-4d31-9488-7a350942461a" />


- **5.)Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**

  - Sucede que están sincronizadas a pesar de estar separadas, entonces cuando muevo una se adapta y la línea que sale apunta al centro del circulo en la otra página. Los mensajes que aparecen en la consola del navegador son los siguientes:
    
    <img width="533" height="577" alt="image" src="https://github.com/user-attachments/assets/5473338d-3f60-4b2b-b819-68a1ce9b4a20" />

    <img width="517" height="560" alt="image" src="https://github.com/user-attachments/assets/7167eda7-141d-44a0-810c-223a44aec4be" />

___

## Actividad 2

### ¿Qué es Internet?

- **Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.**

  - Utilizo un cable de red, que tengo entendido es una fibra optica y eso es como magia negra que manda información con pulsaciones de luz pero creo que estoy completamente equivocado, si esa rampa se corta entonces me imagino que ya mi computador no manda ni recibe información por lo que no puede actualizar paginas ni mandar ningún tipo de dato como archivos y tales, todo debe ser interno.
 
### Navegador y servidor 

- **¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?**

  - Pues justo ahora para taller estoy montando un jueguito multiplayer y en últimas todo recae en esta relación cliente - servidor, de forma en la que los clientes tienen un par de "atributos" que le muestran al servidor y este se encarga de compartir esa información con todos, un ejemplo más específico es con la posición, pues un cliente la actualiza en todo momento pero es un proceso local, realmente solo está cambiando su posición propia por lo que para ver los cambios de posición de los demás debe pedirle esa información al servidor.

### ¿Qué es una URL?

<img width="1013" height="251" alt="image" src="https://github.com/user-attachments/assets/b0545bbe-9a13-4ce1-9c79-ad7213188fe4" />

- **Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?**

  - mi sitio web favorito es el [perfil de p5js de juanferfranco](https://editor.p5js.org/juanferfranco/sketches) cuyo link es el siguiente https://editor.p5js.org/juanferfranco/sketches, donde el **https://** son las reglas del idioma con el que van a hablar, **editor.p5js.org** es la dirección física de donde estoy y el **/juanferfranco/sketches** es la dirección de donde estoy dentro de ese lugar.
 
### Protocolo HTTP

**Compara HTTP con los protocolos seriales que usaste.**

- **¿Qué similitudes encuentras?**

  - Pues encuentro que en ambos hay un envio de datos y que no existe ninguna traducción puesto que ambos hablan el mismo "idioma". 

- **¿Qué diferencias clave ves?**

  - Más allá de que son lenguajes diferentes lo que más me llama la atención es que se debe de pedir la información y el servidor lo debe de aprobar. 

- **¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**

  - Yo diría que es por que debe de seguir una especie de "jerarquía" de ver que le manda o que no al cliente, a la misma vez que debe evaluar quien es el cliente y de donde viene, por lo que mandar inforamción a la loca sin verificar no sería lo ideal. Además de esto el semestre pasado nos mostraron que una página es una melcocha de varios lenguajes, por lo que me imagino que tendrá que hacer algo distinto para mandar toda la información correspondiente a cada elemento.
 
### HTML, CSS y JavaScript

<img width="833" height="381" alt="image" src="https://github.com/user-attachments/assets/323c4c06-df6d-4de4-b41a-e9cc255d26c4" />
 
**Piensa en una página web simple, como un formulario de login.**

-**¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?**

  - Diría que los titulos e información que ponga ahí en la caja de texto, los botones y los inputs field.

-**¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?**

  - Toda la parte visual como el header, la fuente, el color del fondo y demás efectos como el feedback de si se equivoca.

-**¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?**

  - El chequeo de que no esté vacio, sea correcto y todo eso se debe hacer desde acá puesto que pide información de una base de datos adicional.

### ¿Cómo se ejecuta JavaScript?

- **¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?**

  - Pues la ventaja principal que se me ocurre es que solamente está funcionando cuando debería funcionar, y no está constantemente actualizando incluso si no hay cambios, encima solo reacciona cuando hay algo relevante. 

- **¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?**

  - No lo sería para nada, sería mucho trabajo para esencialmente mostrar la misma información que el frame pasado. 

### ¿Qué es Node.js?

- **¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?**

  - Pues me imagino que lo principal son dos cosas; la primera es la utilización de un modelo basado en eventos, y lo otro es que debe de haber algún tipo de ventaja en utilizar el mismo lenguaje en esa relación cliente - servidor.

### WebSockets y Socket.IO

- **Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**

  - Pues HTTP tiene que pedir PERMISO para hacer algo, entonces si se necesita recibir información cada segundo pedir permiso siempre no es lo ideal, por eso se usa websockets, que establece una relación constante con la información que se necesite. Y en que tipo de apliación me puedo imaginar eso, sería en cualquier videojuego competitivo, donde se necesita conocer la posición exacta de todos los jugadores cada segundo para que sea justo para todos, me imagino que ahí el cliente comparte información con el servidor y viceversa sin pedir permiso.
 
## Actividad 3 

### 🧐🧪✍️ Experimento 1

- **Intenta acceder a http://localhost:3000/page1. ¿Funciona?**

  - Si

- **Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?**

  - No

- ¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código.

  - Pues me da a entender que es totalmente comprensible que el cliente esté en la dirección que debe estar para solicitar cierta información, mi predicción es que el cliente llega a la dirección que es, pide permiso con HTTP y despues de eso son puros WebSockets.

### 🧐🧪✍️ Experimento 2

- **Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.**

  -  A user connected - ID: xf4drihvAkxir066AAAJ

- **Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?**

  - A user connected - ID: KS_ILIa6d863UpXyAAAN
 
- **Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?**

  - User disconnected - ID: HSRvE1Gz8iNomJTeAAAL 

- **Cierra la pestaña de page2. Observa la terminal.**

  - User disconnected - ID: KS_ILIa6d863UpXyAAAN

### 🧐🧪✍️ Experimento 3

- **Inicia el servidor y abre page1 y page2.** 

- **Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?**

  -  Received win1update from ID: fWJWdmaFLYw2DpGrAAAB Data: { x: 937, y: 361, width: 958, height: 987 }

- **Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?**

  - Received win2update from ID: dZsHSLSNiLGb-GJJAAAD Data: { x: 187, y: 22, width: 958, height: 987 }

- **Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.**

  -  

## Actividad 5

Mi idea para esta actividad es hacer un acuario por que me gustan mucho los pescados, entonces lo que tengo pensado hacer es una pecera que tiene varios pescados y estos pueden viajar entre las pestañas, esto no tiene absolutamente nada de interactivo entonces voy a ahcer que si el mouse le pasa por encima entonces voltean y cambian su velocidad brevemente.

COMO VOY A HACER ESTO? ni idea, hasta ahora se me ocurre una clase pescado donde sobreescribo update y draw, y en setup tengo un array de pescados y cada frame llama update y draw, ni idea como van a viajar entre pestañas pero eso es un problema para despues.
 
Bueno lo primero y más importante sería la clase Pescado, en general me gustaría que se moviera de izquierda a derecha (o al revés), que tengan diferentes tamaños y colores. En ese caso las variables que se me ocurren son x, y, color, size, speed y direction.

<img width="451" height="175" alt="image" src="https://github.com/user-attachments/assets/6b82a39b-844c-456c-8675-996cd901228c" />

Lo siguiente sería decirle que va hacer cada frame en update y draw. en update diría que solo va la lógica de movimiento, es decir, incrementar la posición en x cierta cantidad, que sería speed. IMPORTANTE, que casi se me olvida y es q se multiplique por direction, que idealmente solo tiene dos valores: 1 y -1.

<img width="363" height="71" alt="image" src="https://github.com/user-attachments/assets/6798cf97-75b8-4853-ab78-03dd51cfadea" />

Y despues sigue el draw, que me da miedo pq no se me ocurre una forma de mover la ellipse (no quiero dibujar un pescado aún) entonces voy a buscar. 

se me ocurre una forma muy rara de hacerlo pero se la voy a copiar a un señor y es que el man basicamente usa push(), translate() y pop() para que solo afecte la transformación a ese pescadito, mi otra opción era mover cada cordenada de la elipse por x, PERO en un futuro quiero que hagan como una función seno entonces me parece mejor translate.

<img width="378" height="183" alt="image" src="https://github.com/user-attachments/assets/92246342-8805-489d-b0fa-30fbffcc8c29" />

tengo un problemita y es que direction lo iba a crear con un random() pero entonces eso puede provocar que sea cero entonces se me ocurrio un pequeño if

<img width="326" height="196" alt="image" src="https://github.com/user-attachments/assets/3bb65312-8253-403c-9ad9-501ee3c7b048" />

BUENO, ahora hay que crear los pescados en setup y llamar sus metodos draw y setup cada frame, AFORTUNADAMENTE, juanferfranco ya ha hecho esto entonces le voy a copiar.

<img width="1249" height="113" alt="image" src="https://github.com/user-attachments/assets/aaa5e89e-6613-4a7e-b30b-0af17dfa095d" />

por mas que me doliera gemini me enseño a poner un "foreach" en p5js

<img width="295" height="88" alt="image" src="https://github.com/user-attachments/assets/a0a8dc15-78b8-463a-9b48-188174073739" />

Ahora toca que un pescado pase de una página a otra ![87e65f7510d7349e2f3e45210c8a60f1](https://github.com/user-attachments/assets/2668352b-871e-46a7-8e40-d6f8792d0af5)

ENTONCES, en mi mente hay que tener en cuenta alguna cositas para poner un pescado en la otra pantalla.

- es un pescado totalmente nuevo para la otra página entonces en algún momento va a tener que instanciar un pescado.
- ese pescado va a tener que ser identico al que salió de la otra página, lo que significa que de alguna forma voy a tener QUE tener acceso al pescado que salió de la pantalla.
- no solo eso sino que (idealmente mi aplicación corre en dos ventanas del mismo tamaño) pero la posición del pescado tendrá que tener una posición proporcional al anterior pescado (yo me entiendo).
- voy a tener que saber cuando un pescado sale de una pantalla para eliminarlo.

para hacer esto tengo q saber como manda datos esto, ya más temprano comentando esa línea de codigo medio intuí que socket es el responsable de esa relación cliente-servidor.

<img width="560" height="157" alt="image" src="https://github.com/user-attachments/assets/72e8a04e-8b20-44f0-9f38-21255a953e9e" />

<img width="480" height="186" alt="image" src="https://github.com/user-attachments/assets/2357816b-957f-4cbd-abcb-03559859c11c" />

lo anterior era mentira estoy haciendo el apply antes q el final de la otra actividad PERO para mandar info se usa emit y la nomenclatura es como  "tintintin", data, y data en este caso sería la info del pescado. No sé si haya alguna forma de empaquetarlo para que no mas sea mandar data pero ahí mismo en elcaso de estudio manda mucha información como parametro entonces voy a hacer justo eso, PERO PRIMERO, la página necesita saber cuando mandar un pescado, y ese cuando va a ser cuando esté por fuera de la pantalla.

eso es muy facil no mas es coger el widht, sumarle el tamaño del bicho y si eso es true entonces sale.

importante tener en cuenta que en su eje mayor un rectangulo tiene dos lados, tambien hay q poner que si es menor q su tamaño por el otro lado devuelve true.

por últime juanferfranco estaría orgulloso de que hice un método completamente nuevo 

<img width="319" height="117" alt="image" src="https://github.com/user-attachments/assets/1f680df9-eccf-4f1e-b4af-83bc182a94a3" />

ahora lo que sigue es llamar este método cada frame, y si devuelve true entonces LLAMA el método que manda la información.

<img width="275" height="67" alt="image" src="https://github.com/user-attachments/assets/cc3e7bd8-5d85-4dd2-b311-4e14600591d1" />

es la mejor forma de implementarlo que se me ocurrió, no creo que sea tan pesado.

<img width="289" height="113" alt="image" src="https://github.com/user-attachments/assets/aa38f5bf-1546-460c-b969-923c9fcbd612" />

el tema con el color es que al parecer tratar un color como normalmente lo trataría en p5js no es posible, hay que dividirlo, aofrtunamaete p5js tiene un cosito que es color.levels que devuelve un array con los valores rgb (o de cualquier otra configuracion de color).

otra cosa importante q dejé a lo último pq me da miedo es que hay que encontrar la forma de saber a q "altura" va a spawnear el otro pescado, entonces yo diría que sería transformar la altura actual del pescado a un valor entre 1 y 0, y depsues multiplicar la altura del otro cosito por ese número.

esto si lo he hecho mil veces pq me niego a usar la función que especificamente hace eso, pero basicamente sería como (número en el rango / total del rango) * total del otro rango. en mi caso eso sería, la posición del bicho y las alturas de cada pagina.

<img width="630" height="23" alt="image" src="https://github.com/user-attachments/assets/244a9be0-ae89-42fb-9f5b-49d05e8d6b7f" />

<img width="584" height="206" alt="image" src="https://github.com/user-attachments/assets/a889b36a-f54c-47e0-ba7c-a8eefcce9144" />

ahora, lo que falta es que la otra pagina lo reciba y lo spawnee

pero pa eso hay que hacer que cuando el servidor lo reciba lo mande.

<img width="417" height="76" alt="image" src="https://github.com/user-attachments/assets/942d3d39-25a3-4a70-8e7f-e603d5dd541e" />

bueno se me olvidó un detalle y es que tambien le tengo q dar una posición en x al pescadito, pero es facil pq la dirección me dice por que lado salío, entonces si x > 0 eso significa que salió por la derecha entonces su salida en x debería ser instanciado por el lado izquierdo. tambine hay que tener en cuenta que no quiero que aparezacn asi de la nada entonces los voy a soawnear un poquito mas afuera.

como su tamaño es máximo 60 entonces los voy a mandar a 70 pq no quiero q se vean ahí mismo.

<img width="548" height="318" alt="image" src="https://github.com/user-attachments/assets/fc9b388a-b743-4954-9062-ace5b473ff6b" />

<img width="1286" height="856" alt="image" src="https://github.com/user-attachments/assets/3e2b7434-b005-4112-b4f7-faa98a3009cc" />

maravilloso, no pasa nada, justo lo que quería.

me equivoqué en el constructor, ya si spawnean PERO se dejan de mover despues de que destruye el primer (o eso creo).

<img width="1297" height="860" alt="image" src="https://github.com/user-attachments/assets/d244a952-0f5d-4eec-8566-bb3857d73b41" />

encontré un error a la hora de mandar y recibir cositas pero me sigue dando error AHHHHHHHHHHHHHHHHHHHHHHHHHHH

<img width="1284" height="855" alt="image" src="https://github.com/user-attachments/assets/a383bb8e-5676-4bc1-a15a-ce441253b199" />

mas o menos solucionado, pasa UN solo pescado.

<img width="1284" height="859" alt="image" src="https://github.com/user-attachments/assets/5f2b151e-aa1c-4492-88da-ae6a9cc25095" />

FUNCIONA (puse una coma donde no debía)

<img width="1290" height="864" alt="image" src="https://github.com/user-attachments/assets/f1fbe0c9-853b-4e88-a60f-c075e9231cc6" />

listo genial pero no tiene nada de interactivo y los pescados son muy feos, entonces voy a hacer que si el mouse les pasa por encimita les cambie la dirección, gracias a dios p5js tiene una funcion de distancia, ent si esa distancia es menos al tamaño del pescado se gira

<img width="613" height="263" alt="image" src="https://github.com/user-attachments/assets/33863def-e69d-4513-8d61-d49c30e2513b" />


**page 1**
```js
let currentPageData = {
  x: window.screenX,
  y: window.screenY,
  width: window.innerWidth,
  height: window.innerHeight
};

let previousPageData = { ...currentPageData };

let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let point1 = [currentPageData.width / 2, currentPageData.height / 2];
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;

let pescados = [];
let nextFishId = 0;

class Pescado {
  constructor(id, x, y, size, color, speed, direction) {
    this.id = id;
    this.x = x;
    this.y = y;
    this.size = size;
    this.color = color;
    this.speed = speed;
    this.direction = direction;
  }

  update() {
    this.x += this.speed * this.direction;
  }

  draw() {
    push();
    translate(this.x, this.y);
    scale(this.direction < 0 ? -1 : 1, 1);
    fill(this.color);
    ellipse(0, 0, this.size * 2, this.size);
    triangle(-20, 0, -this.size, -this.size / 2, -this.size, this.size / 2);
    fill(255);
    circle(10, 0, 30);
    fill(0);
    circle(10, 0, 10);
    pop();
  }

  IsOffScreen() {
    return (
      this.x > width + this.size * 2 ||
      this.x < -this.size * 2
    );
  }

  checkHover(mx, my) {
    let distance = dist(mx, my, this.x, this.y);
    return distance < this.size;
  }

  flipDirection() {
    this.direction *= -1;
  }

}

function setup() {
  createCanvas(windowWidth, windowHeight);
  frameRate(60);
  socket = io();

  socket.on('connect', () => {
    console.log('Connected with ID:', socket.id);
    isConnected = true;
    socket.emit('win1update', currentPageData, socket.id);

    setTimeout(() => {
      socket.emit('requestSync');
    }, 500);
  });

  socket.on('getdata', (response) => {
    if (response && response.data && isValidRemoteData(response.data)) {
      remotePageData = response.data;
      hasRemoteData = true;
      console.log('Received valid remote data:', remotePageData);
      socket.emit('confirmSync');
    }
  });

  socket.on('fullySynced', (synced) => {
    isFullySynced = synced;
    console.log('Sync status:', synced ? 'SYNCED' : 'NOT SYNCED');
  });

  socket.on('peerDisconnected', () => {
    hasRemoteData = false;
    isFullySynced = false;
    console.log('Peer disconnected, waiting for reconnection...');
  });

  socket.on('disconnect', () => {
    isConnected = false;
    hasRemoteData = false;
    isFullySynced = false;
    console.log('Disconnected from server');
  });

  socket.on('recibirPescado', (data) => {
    let startX = (data.direction > 0) ? -50 : width + 50;

    let fishColor = color(data.color[0], data.color[1], data.color[2]);

    let _pescaoNuevo = new Pescado(
      data.id,
      startX,
      data.y,
      data.size,
      fishColor,
      data.speed,
      data.direction
    );
    pescados.push(_pescaoNuevo);
  });

   for (let i = 0; i < 20; i++) {
    let size = random(20, 60);
    let pescadito = new Pescado(nextFishId++, random(width), random(height), size, color(0, random(50, 255), random(50, 120)), random(1, 3), random([1, -1]));
    pescados.push(pescadito);
  }
}

function isValidRemoteData(data) {
  return (
    data &&
    typeof data.x === 'number' &&
    typeof data.y === 'number' &&
    typeof data.width === 'number' &&
    data.width > 0 &&
    typeof data.height === 'number' &&
    data.height > 0
  );
}

function checkWindowPosition() {
  currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
  };

  if (
    currentPageData.x !== previousPageData.x ||
    currentPageData.y !== previousPageData.y ||
    currentPageData.width !== previousPageData.width ||
    currentPageData.height !== previousPageData.height
  ) {
    point1 = [currentPageData.width / 2, currentPageData.height / 2];
    socket.emit('win1update', currentPageData, socket.id);
    previousPageData = currentPageData;
  }
}


function draw() {
  background(0, 100, 200);

  checkWindowPosition();

  if (!isConnected) {
    showStatus('Conectando al servidor...', color(255, 165, 0));
    return;
  }

  if (!hasRemoteData) {
    showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
    return;
  }

  if (!isFullySynced) {
    showStatus('Sincronizando datos...', color(255, 165, 0));
    return;
  }

  for (let pescadito of pescados) {
  if (pescadito.checkHover(mouseX, mouseY)) {
    pescadito.flipDirection();
  }
}

  for (let pescadito of [...pescados]) {
    pescadito.update();
    pescadito.draw();

    if (pescadito.IsOffScreen()) {
      SendFishToOtherPage(pescadito);
    }
  }
}

function showStatus(message, statusColor) {
  textSize(24);
  textAlign(CENTER, CENTER);
  noStroke();
  fill(0, 0, 0, 150);
  rectMode(CENTER);
  let textW = textWidth(message) + 40;
  let textH = 40;
  rect(width / 2, height / 6, textW, textH, 10);
  fill(statusColor);
  text(message, width / 2, height / 6);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}

function SendFishToOtherPage(pescadito) {
  let y = (pescadito.y / currentPageData.height) * remotePageData.height;
  let col = pescadito.color.levels;
  socket.emit('sendPescado', {
  id: pescadito.id,
  y: y,
  size: pescadito.size,
  color: [col[0], col[1], col[2]],
  speed: pescadito.speed,
  direction: pescadito.direction
});

  pescados = pescados.filter((p) => p.id !== pescadito.id);
}
```

**page 2**
```js
let currentPageData = {
  x: window.screenX,
  y: window.screenY,
  width: window.innerWidth,
  height: window.innerHeight
};

let previousPageData = { ...currentPageData };

let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let point1 = [currentPageData.width / 2, currentPageData.height / 2];
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;

let pescados = [];
let nextFishId = 0;

class Pescado {
  constructor(id, x, y, size, color, speed, direction) {
    this.id = id;
    this.x = x;
    this.y = y;
    this.size = size;
    this.color = color;
    this.speed = speed;
    this.direction = direction;
  }

  update() {
    this.x += this.speed * this.direction;
  }

  draw() {
    push();
    translate(this.x, this.y);
    scale(this.direction < 0 ? -1 : 1, 1);
    fill(this.color);
    ellipse(0, 0, this.size * 2, this.size);
    triangle(-20, 0, -this.size, -this.size / 2, -this.size, this.size / 2);
    fill(255);
    circle(10, 0, 30);
    fill(0);
    circle(10, 0, 10);
    pop();
  }

  IsOffScreen() {
    return (
      this.x > width + this.size * 2 ||
      this.x < -this.size * 2
    );
  }

  checkHover(mx, my) {
    let distance = dist(mx, my, this.x, this.y);
    return distance < this.size;
  }

  flipDirection() {
    this.direction *= -1;
  }

}

function setup() {
  createCanvas(windowWidth, windowHeight);
  frameRate(60);
  socket = io();

  socket.on('connect', () => {
    console.log('Connected with ID:', socket.id);
    isConnected = true;
    socket.emit('win2update', currentPageData, socket.id);

    setTimeout(() => {
      socket.emit('requestSync');
    }, 500);
  });

  socket.on('getdata', (response) => {
    if (response && response.data && isValidRemoteData(response.data)) {
      remotePageData = response.data;
      hasRemoteData = true;
      console.log('Received valid remote data:', remotePageData);
      socket.emit('confirmSync');
    }
  });

  socket.on('fullySynced', (synced) => {
    isFullySynced = synced;
    console.log('Sync status:', synced ? 'SYNCED' : 'NOT SYNCED');
  });

  socket.on('peerDisconnected', () => {
    hasRemoteData = false;
    isFullySynced = false;
    console.log('Peer disconnected, waiting for reconnection...');
  });

  socket.on('disconnect', () => {
    isConnected = false;
    hasRemoteData = false;
    isFullySynced = false;
    console.log('Disconnected from server');
  });

  socket.on('recibirPescado', (data) => {
    let startX = (data.direction > 0) ? -50 : width + 50;

    let fishColor = color(data.color[0], data.color[1], data.color[2]);

    let _pescaoNuevo = new Pescado(
      data.id,
      startX,
      data.y,
      data.size,
      fishColor,
      data.speed,
      data.direction
    );
    pescados.push(_pescaoNuevo);
  });

   for (let i = 0; i < 20; i++) {
    let size = random(20, 60);
    let pescadito = new Pescado(nextFishId++, random(width), random(height), size, color(0, random(50, 255), random(50, 120)), random(1, 3), random([1, -1]));
    pescados.push(pescadito);
  }
}

function isValidRemoteData(data) {
  return (
    data &&
    typeof data.x === 'number' &&
    typeof data.y === 'number' &&
    typeof data.width === 'number' &&
    data.width > 0 &&
    typeof data.height === 'number' &&
    data.height > 0
  );
}

function checkWindowPosition() {
  currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
  };

  if (
    currentPageData.x !== previousPageData.x ||
    currentPageData.y !== previousPageData.y ||
    currentPageData.width !== previousPageData.width ||
    currentPageData.height !== previousPageData.height
  ) {
    point1 = [currentPageData.width / 2, currentPageData.height / 2];
    socket.emit('win2update', currentPageData, socket.id);
    previousPageData = currentPageData;
  }
}


function draw() {
  background(0, 100, 200);

  checkWindowPosition();

  if (!isConnected) {
    showStatus('Conectando al servidor...', color(255, 165, 0));
    return;
  }

  if (!hasRemoteData) {
    showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
    return;
  }

  if (!isFullySynced) {
    showStatus('Sincronizando datos...', color(255, 165, 0));
    return;
  }

  for (let pescadito of pescados) {
  if (pescadito.checkHover(mouseX, mouseY)) {
    pescadito.flipDirection();
  }
}

  for (let pescadito of [...pescados]) {
    pescadito.update();
    pescadito.draw();

    if (pescadito.IsOffScreen()) {
      SendFishToOtherPage(pescadito);
    }
  }
}

function showStatus(message, statusColor) {
  textSize(24);
  textAlign(CENTER, CENTER);
  noStroke();
  fill(0, 0, 0, 150);
  rectMode(CENTER);
  let textW = textWidth(message) + 40;
  let textH = 40;
  rect(width / 2, height / 6, textW, textH, 10);
  fill(statusColor);
  text(message, width / 2, height / 6);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}

function SendFishToOtherPage(pescadito) {
  let y = (pescadito.y / currentPageData.height) * remotePageData.height;
  let col = pescadito.color.levels;
  socket.emit('sendPescado', {
  id: pescadito.id,
  y: y,
  size: pescadito.size,
  color: [col[0], col[1], col[2]],
  speed: pescadito.speed,
  direction: pescadito.direction
});

  pescados = pescados.filter((p) => p.id !== pescadito.id);
}
```

**server**
```js
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const path = require('path');
const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

let page1 = { x: 0, y: 0, width: 100, height: 100 };
let page2 = { x: 0, y: 0, width: 100, height: 100 };
let connectedClients = new Map();
let syncedClients = new Set();

app.use(express.static(path.join(__dirname, 'views')));

app.get('/page1', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
    console.log('A user connected - ID:', socket.id);
    connectedClients.set(socket.id, { page: null, synced: false });
    
    socket.on('disconnect', () => {
        console.log('User disconnected - ID:', socket.id);
        connectedClients.delete(socket.id);
        syncedClients.delete(socket.id);
        // Notificar a otros clientes que se perdió la sincronización
        socket.broadcast.emit('peerDisconnected');
    });

    socket.on('win1update', (window1, sendid) => {
        console.log('Received win1update from ID:', socket.id, 'Data:', window1);
        if (isValidWindowData(window1)) {
            page1 = window1;
            connectedClients.set(socket.id, { page: 'page1', synced: false });
            socket.broadcast.emit('getdata', { data: page1, from: 'page1' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('win2update', (window2, sendid) => {
        console.log('Received win2update from ID:', socket.id, 'Data:', window2);
        if (isValidWindowData(window2)) {
            page2 = window2;
            connectedClients.set(socket.id, { page: 'page2', synced: false });
            socket.broadcast.emit('getdata', { data: page2, from: 'page2' });
            checkAndNotifySyncStatus();
        }
    });

    socket.on('requestSync', () => {
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo?.page === 'page1') {
            socket.emit('getdata', { data: page2, from: 'page2' });
        } else if (clientInfo?.page === 'page2') {
            socket.emit('getdata', { data: page1, from: 'page1' });
        }
    });

    socket.on('confirmSync', () => {
        syncedClients.add(socket.id);
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo) {
            connectedClients.set(socket.id, { ...clientInfo, synced: true });
        }
        checkAndNotifySyncStatus();
    });    

  socket.on('sendPescado', (fishData) => {

    socket.broadcast.emit('recibirPescado', fishData);
  });

});

function isValidWindowData(data) {
    return data && 
           typeof data.x === 'number' && 
           typeof data.y === 'number' && 
           typeof data.width === 'number' && data.width > 0 &&
           typeof data.height === 'number' && data.height > 0;
}

function checkAndNotifySyncStatus() {
    const page1Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page1');
    const page2Clients = Array.from(connectedClients.entries()).filter(([id, info]) => info.page === 'page2');
    
    const bothPagesConnected = page1Clients.length > 0 && page2Clients.length > 0;
    const allClientsSynced = Array.from(connectedClients.keys()).every(id => syncedClients.has(id));
    const hasMinimumClients = connectedClients.size >= 2;

    console.log(`Debug - Connected clients: ${connectedClients.size}, Page1: ${page1Clients.length}, Page2: ${page2Clients.length}, Synced: ${syncedClients.size}`);

    
    if (bothPagesConnected && allClientsSynced && hasMinimumClients) {
        io.emit('fullySynced', true);
        console.log('All clients are fully synced');
    } else {
        io.emit('fullySynced', false);
        console.log(`Sync status: pages=${bothPagesConnected}, synced=${allClientsSynced}, clients=${connectedClients.size}`);
    }
}



server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```

<img width="1919" height="902" alt="image" src="https://github.com/user-attachments/assets/051ae408-2a18-4cb6-a235-8bf255c6eaed" />

<img width="1886" height="737" alt="image" src="https://github.com/user-attachments/assets/96835871-a21d-4ddf-8021-1e736603f8a2" />

