La **configuración y personalización** de Bash permite a los usuarios adaptar el entorno del shell a sus necesidades específicas mediante el uso de scripts de inicio, variables, alias y funciones.

### Archivos de Inicio y Persistencia

Bash personaliza la sesión ejecutando una serie de **scripts de inicio** según el tipo de shell que se inicie 1:

* **Scripts Globales:** Ubicados en /etc/, afectan a todos los usuarios del sistema. Entre ellos destacan /etc/profile (para shells de inicio de sesión) y /etc/bash.bashrc (para shells interactivos).  
* **Scripts Locales:** Se encuentran en el directorio personal del usuario (\~) y tienen **prioridad sobre los globales** 4, 7\. Los más comunes son \~/.bash\_profile, \~/.profile y \~/.bashrc.  
* **Aplicación inmediata:** Para que los cambios realizados en estos archivos surtan efecto sin necesidad de reiniciar la sesión, se utiliza el comando **source** o el punto (.).  
* **Plantillas para nuevos usuarios:** El directorio **/etc/skel** funciona como una plantilla; su contenido se copia automáticamente al directorio de inicio de cada cuenta de usuario nueva que se cree.

### Elementos de Personalización

El entorno de shell se constituye principalmente por tres elementos:

1. **Variables de Entorno:** Definen características globales. Por ejemplo, **PATH** determina los directorios donde el shell busca programas ejecutables, y **PS1** define la apariencia del indicador de comandos (prompt).  
2. **Alias:** Son nombres sustitutos que permiten abreviar comandos largos o complejos 18, 19\. Para mantenerlos de forma permanente, se suelen almacenar en \~/.bashrc o en un archivo dedicado llamado \~/.bash\_aliases.  
3. **Funciones:** Son bloques de código más flexibles que los alias, capaces de implementar lógica compleja, bucles y procesar parámetros posicionales.

### Configuración del Interfaz y Comportamiento

* **Prompt (PS1):** El indicador de comandos es altamente personalizable y puede configurarse para mostrar información como el nombre del usuario, el host y el directorio de trabajo actual.  
* **Historial de Comandos:** Bash utiliza variables como HISTSIZE para definir cuántos comandos se guardan en memoria y HISTFILE para especificar el archivo donde se almacenan permanentemente (normalmente \~/.bash\_history).  
* **Accesibilidad:** Los entornos de escritorio en Linux también ofrecen módulos de personalización para adaptar el teclado, el mouse y la pantalla a usuarios con necesidades específicas.
