
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

 
