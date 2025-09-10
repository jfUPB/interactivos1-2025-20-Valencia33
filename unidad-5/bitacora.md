
# Evidencias de la unidad 5

## Actividad 1

- **Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

El microbit lo que hace es que manda un "array" de valores con el nombre **data**, realmente no es un array, es más un formato de texto que se le da a los siguientes atributos: xValue, yValue, aState y bState. Esta variable **data** es lo que se manda por el serial, un ejemplo de como se vería sería así: 1000, 900, true, false\n. Una vez p5.js recibe esa información entonces corta ese string cada vez que haya una coma y deja de hacerlo cuando encuentre "\n".

- **¿Cómo es la estructura del protocolo ASCII usado?**

No tengo ni idea a que se refiere con protocolo ASCII pero creo que es el como se pasan los datos. En este caso es un string como lo expliqué en el punto anterior, y los valores que se pasan van de -1024 a 1024 para xValue y yValue y de true a false en aState y bState donde ambos son pasados como strings.

- **Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**

En esta porción de código es donde se reciben los datos del microbit, lo que hace es que lee y separa la string que recibe cada que encuentre una coma, espera que esos datos vengan un orden predeterminado puesto que justo despues los mete en un array que se llama values, el cual almacena strings. Despues de dividir y guardar la string debe de hacer otros procesos puesto que xValue y yValue son enteros y aState y bState son booleanos, entonces le hace el parse a Int a los dos primeros y lo mismo con los dos últimos pero a bool.

Ya para xValue y yValue hace que sus valores correspondan con las dimensiones de la pantalla, sumandoles la mitad de la altura y el ancho. De esta forma ahora xValue y yValue pueden ser utilizados para representar coordenadas en la pantalla.

<img width="546" height="300" alt="image" src="https://github.com/user-attachments/assets/81ee256b-d888-4cbf-8505-87358df450e4" />

- **¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**

Para ambos hace uso de una variable adicional que sirve para chequear el estado de los botones en el frame anterior, de esta forma se sabe si fueron presionados o si los soltaron. Esos son los chequeos que se realizan. Para **Apressed** lo que hace es que mira si newAState es true y precNewAState es falso, como el valor de prevNewAState es definido al final de cada frame entonces se entiende que si esa condición es true entonces A acaba de ser presionado.

Para **Bpressed** es lo mismo pero se chequea si newBState == false y prevNewBState == true, de esta forma se sabe que en el frame anterior B estaba presionado pero en este no, lo que significa que B fue soltado.

Aunque realmente la pregunta la pude haber respondido que se hacía con un print().

<img width="594" height="328" alt="image" src="https://github.com/user-attachments/assets/1d648c8f-55bf-42e4-bbe4-2ef9904d0466" />

- **Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.**

<img width="984" height="855" alt="20250910_171838" src="https://github.com/user-attachments/assets/e4f89c64-c748-466d-9e77-ba116fcfc173" />

<img width="984" height="855" alt="20250910_172304" src="https://github.com/user-attachments/assets/d5b84bbc-aa73-4d2e-a842-addfc7e794f8" />

<img width="984" height="855" alt="20250910_172603" src="https://github.com/user-attachments/assets/366498ad-7ad1-49af-a20f-29524f2e798c" />
