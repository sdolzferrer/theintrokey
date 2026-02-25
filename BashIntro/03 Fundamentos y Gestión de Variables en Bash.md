En el entorno de Bash, la **gestión de variables** es fundamental para almacenar información temporal, como texto o números, que influye en el comportamiento del shell y de los programas.

### Tipos de Variables

Bash clasifica las variables principalmente en dos categorías según su alcance:

* **Variables locales (o de shell):** Están disponibles únicamente en la sesión de shell actual donde fueron creadas 3, 4\. No son heredadas por subprocesos o shells hijos 5, 6\. Por convención, suelen escribirse en minúsculas.  
* **Variables de entorno (o globales):** Están disponibles tanto en la sesión actual como en todos los procesos e hijos generados desde ella. Se utilizan comúnmente para pasar datos de configuración a los comandos. Por convención, se escriben en mayúsculas (ej. PATH, USER).

### Manipulación Básica

* **Asignación:** Se utiliza la sintaxis nombre=valor. Es crucial **no incluir espacios** antes ni después del signo igual.  
* **Referencia:** Para acceder al valor de una variable, se antepone el signo de dólar ($) al nombre (ej. $nombre).  
* **Exportación:** Para convertir una variable local en una de entorno y que sea visible para subprocesos, se utiliza el comando export nombre.  
* **Eliminación:** El comando unset nombre borra tanto el valor como la definición de la variable de la sesión actual.  
* **Sólo lectura:** Se puede usar readonly nombre para que una variable sea inmutable y no se pueda modificar su valor.

### Uso de Comillas y Caracteres Especiales

El uso de comillas afecta significativamente cómo Bash interpreta las variables:

* **Comillas dobles (" "):** Permiten la **sustitución de variables**, interpretando el signo $ para expandir su valor.  
* **Comillas simples (' '):** Son "fuertes" y revocan el significado especial de todos los caracteres, tratando el contenido de forma estrictamente literal (no expanden variables).  
* **Carácter de escape (\\):** Elimina el significado especial de un solo carácter, como el $ para evitar la expansión de una variable.

### Variables Especiales incorporadas

Bash incluye parámetros automáticos que almacenan información útil:

* **$0**: Nombre del script o del shell actual.  
* **$\#**: Número de argumentos pasados a un script o función.  
* **$@ y $\***: Representan todos los argumentos pasados.  
* **$?**: Código de salida del último comando ejecutado (0 indica éxito).  
* **$$**: Identificador de proceso (PID) del shell actual.

### Persistencia y Configuración

Las variables creadas en la línea de comandos no son persistentes; se pierden al cerrar la sesión 36\. Para hacerlas permanentes, deben añadirse a los **archivos de configuración** de inicio, como \~/.bashrc (para shells interactivos) o \~/.profile.

### Visualización de Variables

Existen comandos para listar las variables activas:

* **env o printenv**: Muestran exclusivamente las variables de entorno.  
* **set**: Es más exhaustivo, mostrando todas las variables (locales y de entorno) y las funciones de la sesión actual.

