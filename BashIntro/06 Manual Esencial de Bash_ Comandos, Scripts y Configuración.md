**Bash (Bourne-Again Shell)** es un programa que permite la comunicación basada en texto entre el sistema operativo y el usuario, actuando como el intérprete de comandos predeterminado en la gran mayoría de las distribuciones de Linux 1-3. No es solo un lenguaje de programación, sino una **interfaz interactiva** diseñada para ejecutar otros programas y automatizar tareas repetitivas mediante **shell scripts** 4, 5\.  
A continuación se detallan sus características y funcionalidades principales según las fuentes:

### Estructura y Comandos

* **Sintaxis básica:** La mayoría de los comandos siguen la estructura: comando \[opción(es)\] \[argumento(s)\] 6, 7\.  
* **Tipos de comandos:** Bash distingue entre comandos **internos** (built-ins), que son parte del propio shell (como cd o export), y comandos **externos**, que son archivos ejecutables que el shell busca utilizando la variable de entorno PATH 8-10.  
* **Comillas (Quoting):** Se utilizan para manejar espacios y caracteres especiales. Las **comillas dobles (" ")** permiten la sustitución de variables, mientras que las **comillas simples (' ')** suprimen el significado especial de todos los caracteres, tratándolos literalmente 11-13. El carácter de **escape (\\)** se usa para anular el significado especial de un solo carácter siguiente 12, 14\.

### Gestión de Variables

Bash utiliza variables para almacenar datos temporalmente 15\.

* **Locales:** Disponibles solo en la sesión de shell actual 16\.  
* **De entorno (Globales):** Heredadas por subprocesos y programas secundarios. Se crean o convierten usando el comando export 16, 17\.  
* **Variables especiales:** Incluyen $0 (nombre del script), $\# (número de argumentos), $@ (todos los argumentos) y $? (código de salida del último comando, donde 0 indica éxito) 18, 19\.

### Automatización y Scripts

Un **script de Bash** es un archivo de texto que contiene una secuencia ordenada de comandos 20, 21\.

* **Shebang:** La primera línea debe ser \#\!/bin/bash para indicar al sistema que use Bash como intérprete 21, 22\.  
* **Permisos:** Para ejecutarse como un programa, el archivo debe tener activado el bit de ejecución (mediante chmod \+x) 23, 24\.  
* **Estructuras de control:** Permite el uso de lógica condicional (**if/then/else**, **case**) y bucles (**for**, **while**, **until**) para realizar tareas complejas y repetitivas 25-27.

### Redirección y Filtrado

Bash puede reasignar los canales de comunicación estándar:

* **Redirección:** El operador \> envía la salida a un archivo (sobrescribiendo), mientras que \>\> añade la información al final del archivo 28-30.  
* **Tuberías (Pipes):** El símbolo | permite conectar la salida de un comando directamente a la entrada de otro, facilitando el filtrado de datos con herramientas como grep, sed o cut 31, 32\.  
* **Globbing:** El uso de comodines como \* (cualquier número de caracteres) y ? (un solo carácter) permite referirse a múltiples archivos simultáneamente 33, 34\.

### Configuración y Personalización

Al iniciar una sesión, Bash lee archivos de configuración para establecer el entorno del usuario 35\.

* **Nivel Global:** /etc/profile y /etc/bash.bashrc 36, 37\.  
* **Nivel Local:** \~/.bash\_profile, \~/.profile y \~/.bashrc 38-40.  
* **Alias:** Permiten crear nombres sustitutos cortos para comandos largos o complejos (ej. alias ll='ls \-l') 41-43.  
* **Funciones:** Son bloques de código reutilizables más flexibles que los alias, capaces de aceptar parámetros posicionales y ejecutar lógica compleja 44, 45\.

