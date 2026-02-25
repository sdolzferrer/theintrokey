La mayoría de los comandos en Bash siguen una **estructura básica** compuesta por: comando \[opción(es)/parámetro(s)...\] \[argumento(s)...\]. El **comando** es el programa que el usuario ejecuta y representa la única parte obligatoria de esta estructura.

### Componentes de la Estructura

* **Comando:** Es el archivo ejecutable o la instrucción interna que se desea correr, como ls o cd.  
* **Opción(es):** También llamadas "switches", modifican el comportamiento del comando. Pueden aparecer en forma corta (un guion seguido de una letra, ej. \-l) o larga (dos guiones seguidos de una palabra, ej. \--format=long) 2\. Es posible combinar varias opciones cortas en una sola cadena, como \-al.  
* **Argumento(s):** Son los datos adicionales que el programa requiere para operar, tales como nombres de archivos o rutas de directorios (ej. /home).

### Tipos de Comandos

Bash admite dos categorías de comandos según su origen:

1. **Internos (Built-ins):** Son parte integral del shell y no programas independientes; existen alrededor de 30, como cd, set y export 4\. Estos no tienen una página de manual (man) propia por ser parte del shell.  
2. **Externos:** Son archivos individuales (binarios o scripts) que residen en el sistema de archivos 6\. Cuando se invocan, el shell utiliza la variable de entorno PATH para localizarlos. El comando type permite determinar si una instrucción es interna o externa.

### Manejo de Caracteres Especiales (Quoting)

Para que el shell interprete correctamente comandos que incluyen espacios o caracteres especiales, se utilizan las **comillas**:

* **Comillas dobles (" "):** Permiten que casi todos los caracteres se interpreten literalmente, pero mantienen el significado especial del signo de dólar ($), la barra invertida (\\) y la comilla invertida ( \` ), permitiendo la **sustitución de variables**.  
* **Comillas simples (' '):** Son consideradas "fuertes" porque revocan el significado especial de todos los caracteres, tratando el contenido de forma estrictamente literal.  
* **Carácter de escape (\\):** Se antepone a un solo carácter para eliminar su significado especial y que Bash lo lea literalmente.

### Interacción entre Comandos

La estructura de los comandos se puede extender mediante mecanismos de comunicación:

* **Redirección:** El operador \> envía la salida de un comando a un archivo (sobrescribiéndolo), mientras que \>\> añade la información al final del archivo existente.  
* **Tuberías (Pipes):** El operador | conecta directamente la salida de un comando con la entrada del siguiente, permitiendo encadenar programas para tareas complejas.  
* **Sustitución de comando:** Permite usar la salida de un comando como argumento de otro o almacenarla en una variable, utilizando la sintaxis $(comando) o  \`comando\`.

