
# Evidencias de la unidad 7

## Actividad 1

> abrir el codigo
> 
> fordward el port, ponerle que 3000, para mandarlo a internet
> 
> cambiar la visibilidad del puerto a pública

- **1.) ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**

  - Por que ya no todo pasa en el mismo computador, el celular se debe de conectar por internet. Entonces esa URL que sale es la dirección de ese servidor en internet.

- **2.) Describe brevemente qué hace npm install y npm start.**

  - npm install se encarga de instalar todos los paquetes de los que depende el proyecto y npm start se encarga de abrir el servidor (eso en nuestor caso) creo que en realidad lo que hace es que corre los scripts.

- **3.) ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

  - <img width="560" height="334" alt="image" src="https://github.com/user-attachments/assets/4c1259a4-dd49-40f3-bef8-a731cbd9e655" />

  - <img width="520" height="576" alt="image" src="https://github.com/user-attachments/assets/34994c34-d209-4a10-b441-60a7387acb0a" />

- **4.) Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

  - Yo lo noté medianamente inmediato, diría que como no se corre localmente debe ser un poquito más lento.
  - Sin embargo despues de correr la aplicación solamente en el computador si noté que había algún tipo de retraso puesto que localmente la respuesta es inmediata.
 
## Actividad 2

- **1.) Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

  - DevTunnels es necesario por que la conexión sucede por medio de internet, conceptualmente es como una especie de lugar que se encarga de redirigir información a lugares invisibles que solo el sabe donde está.

- **2.) Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

  - la función touchMoved() se encarga de detectar cuando se presiona la pantalla y se llama cada frame en lo que esto pase. La variable threshold es utilizada para identificar si hubo cambios significativos en la posición x/y del touch, de esta forma, si el cambio fue menor 5 entonces no hace nada.

-  **3.) Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**

    -  pues en un principio diría que todo lo local es mucho más rápido y seguro que cualquier otra cosa que se conecte a internet, entonces localmente diría que la IP local es mucho más rápida

-  **4.) Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

    -  <img width="1036" height="934" alt="image" src="https://github.com/user-attachments/assets/1b0ba905-f787-40b2-83f0-3d1835462092" />

