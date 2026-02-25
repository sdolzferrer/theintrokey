La **redirección y el filtrado** son pilares fundamentales de la filosofía de Linux, permitiendo que programas simples trabajen en conjunto para realizar tareas complejas mediante la transmisión de datos a través de canales estándar.

### Redirección de Entrada/Salida (E/S)

La comunicación en la línea de comandos se realiza a través de tres canales principales, conocidos como descriptores de archivos:

* **Entrada estándar (stdin / canal 0):** Normalmente el teclado.  
* **Salida estándar (stdout / canal 1):** Normalmente la pantalla.  
* **Error estándar (stderr / canal 2):** Canal destinado específicamente a mensajes de error o depuración, que también se muestra en pantalla por defecto.

#### Operadores de Redirección

Bash permite reasignar estos canales para leer desde archivos o escribir en ellos:

* **Salida (\> y \>\>):** El operador \> envía la salida a un archivo, creándolo o **sobrescribiéndolo**. El operador \>\> añade la información al final del archivo sin borrar el contenido previo.  
* **Error (2\> y 2\>\>):** Se utiliza para capturar específicamente los errores. Por ejemplo,> /dev/null descarta los errores enviándolos al "bit bucket" (un archivo especial que no almacena nada).  
* **Ambos (&\>):** Redirige tanto la salida estándar como el error estándar al mismo destino.  
* **Entrada (\<):** Pasa el contenido de un archivo a un comando como si se estuviera escribiendo desde el teclado.  
* **Documentos y cadenas "Here" (\<\< y \<\<\<):** Permiten redirigir bloques de texto de varias líneas (\<\<) o una sola línea de texto (\<\<\<) directamente a la entrada de un comando.

### Tuberías (Pipes)

El operador de tubería (**|**) conecta la salida estándar de un comando directamente con la entrada estándar del siguiente. A diferencia de la redirección, los datos fluyen de izquierda a derecha entre procesos, no hacia archivos. Esto permite encadenar múltiples programas para procesar información en etapas.

### Filtrado de Datos

Los comandos intermedios en una cadena de tuberías que reciben datos, los transforman y producen una salida se denominan **filtros**. Las herramientas más comunes mencionadas en las fuentes para este propósito son:

* **grep:** Busca patrones específicos (usando expresiones regulares) dentro de un flujo de texto o archivo.  
* **sed:** Un editor de flujo que permite transformar texto de forma no interactiva, como buscar y reemplazar cadenas.  
* **cut:** Extrae o elimina secciones específicas (campos o columnas) de cada línea.  
* **sort:** Ordena las líneas de texto alfabética o numéricamente.  
* **wc:** Cuenta líneas, palabras o bytes en un archivo o flujo.  
* **uniq:** Omite o cuenta líneas repetidas que sean adyacentes.  
* **head y tail:** Muestran las primeras o últimas líneas de un archivo, respectivamente.  
* **tee:** Es un comando especial que permite bifurcar la salida: la muestra en pantalla y, simultáneamente, la guarda en un archivo.  
* **tr:** Traduce, elimina o comprime caracteres repetidos (como espacios).  
* **xargs:** Permite construir y ejecutar comandos utilizando la salida de otro comando como argumentos.

