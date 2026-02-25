La **redirección y el filtrado** son pilares fundamentales de la filosofía de Linux, permitiendo que programas simples trabajen en conjunto para realizar tareas complejas mediante la transmisión de datos a través de canales estándar 1-3.

### Redirección de Entrada/Salida (E/S)

La comunicación en la línea de comandos se realiza a través de tres canales principales, conocidos como descriptores de archivos 1, 4:

* **Entrada estándar (stdin / canal 0):** Normalmente el teclado 1, 5\.  
* **Salida estándar (stdout / canal 1):** Normalmente la pantalla 1, 5\.  
* **Error estándar (stderr / canal 2):** Canal destinado específicamente a mensajes de error o depuración, que también se muestra en pantalla por defecto 1, 6\.

#### Operadores de Redirección

Bash permite reasignar estos canales para leer desde archivos o escribir en ellos:

* **Salida (\> y \>\>):** El operador \> envía la salida a un archivo, creándolo o **sobrescribiéndolo** 7, 8\. El operador \>\> añade la información al final del archivo sin borrar el contenido previo 9, 10\.  
* **Error (2\> y 2\>\>):** Se utiliza para capturar específicamente los errores. Por ejemplo, 2\> /dev/null descarta los errores enviándolos al "bit bucket" (un archivo especial que no almacena nada) 11-13.  
* **Ambos (&\>):** Redirige tanto la salida estándar como el error estándar al mismo destino 14, 15\.  
* **Entrada (\<):** Pasa el contenido de un archivo a un comando como si se estuviera escribiendo desde el teclado 12, 16\.  
* **Documentos y cadenas "Here" (\<\< y \<\<\<):** Permiten redirigir bloques de texto de varias líneas (\<\<) o una sola línea de texto (\<\<\<) directamente a la entrada de un comando 17-19.

### Tuberías (Pipes)

El operador de tubería (**|**) conecta la salida estándar de un comando directamente con la entrada estándar del siguiente 3, 20, 21\. A diferencia de la redirección, los datos fluyen de izquierda a derecha entre procesos, no hacia archivos 22\. Esto permite encadenar múltiples programas para procesar información en etapas 23, 24\.

### Filtrado de Datos

Los comandos intermedios en una cadena de tuberías que reciben datos, los transforman y producen una salida se denominan **filtros** 24\. Las herramientas más comunes mencionadas en las fuentes para este propósito son:

* **grep:** Busca patrones específicos (usando expresiones regulares) dentro de un flujo de texto o archivo 25-27.  
* **sed:** Un editor de flujo que permite transformar texto de forma no interactiva, como buscar y reemplazar cadenas 27-29.  
* **cut:** Extrae o elimina secciones específicas (campos o columnas) de cada línea 30-32.  
* **sort:** Ordena las líneas de texto alfabética o numéricamente 31, 33, 34\.  
* **wc:** Cuenta líneas, palabras o bytes en un archivo o flujo 30, 31, 34\.  
* **uniq:** Omite o cuenta líneas repetidas que sean adyacentes 35, 36\.  
* **head y tail:** Muestran las primeras o últimas líneas de un archivo, respectivamente 31, 33, 37\.  
* **tee:** Es un comando especial que permite bifurcar la salida: la muestra en pantalla y, simultáneamente, la guarda en un archivo 38, 39\.  
* **tr:** Traduce, elimina o comprime caracteres repetidos (como espacios) 32, 40, 41\.  
* **xargs:** Permite construir y ejecutar comandos utilizando la salida de otro comando como argumentos 38, 42\.

