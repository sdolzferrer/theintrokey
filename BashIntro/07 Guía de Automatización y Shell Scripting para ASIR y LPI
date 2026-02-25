Para alcanzar el dominio de la automatización y la lógica de shell scripting en el contexto de un ciclo de Grado Superior en ASIR, se proponen los siguientes ejercicios prácticos. Estos integran los conceptos de comandos esenciales, estructuras de control y configuración de Bash con las metodologías DevOps y el ecosistema de código abierto promovidos por el Linux Professional Institute (LPI) y el currículo de ASIR.
Ejercicio 1: Gestión de Procesos y Entorno (Fundamentos de ASIR y LPI 103.1/103.5)
Objetivo: Crear un script que identifique procesos en ejecución de un usuario específico y exporte variables de configuración.
Tarea: Escriba un script llamado monitor_procs.sh que:
Utilice un shebang correcto para Bash.
Reciba un nombre de usuario como primer argumento posicional ($1).
Verifique mediante una estructura if y el comando id si el usuario existe en /etc/passwd.
Si el usuario existe, liste sus procesos actuales usando ps con una sintaxis que muestre el usuario y el comando.
Añada el directorio ~/bin a la variable de entorno PATH de forma temporal para la ejecución del script.
Ejercicio 2: Auditoría de Seguridad y Filtrado (LPI Security Essentials y ASIR RA1)
Objetivo: Automatizar la búsqueda de posibles vulnerabilidades (archivos con permisos especiales) y generar informes.
Tarea: Desarrolle un script que:
Utilice el comando find para buscar archivos con el bit SUID activo en el directorio /usr/bin.
Use una tubería (pipe) para enviar el resultado a grep y filtrar solo aquellos que pertenezcan al usuario root.
Redirija la salida a un archivo llamado informe_seguridad.txt en el home del usuario, asegurándose de no sobrescribir si el archivo ya existe (operador >>).
Muestre al final el código de salida ($?) de la última operación para confirmar el éxito.
Ejercicio 3: Lógica DevOps - Software Bill of Materials (SBOM) y Bucles (LPI 701.5)
Objetivo: Simular un proceso de integración continua (CI) que verifique dependencias de software en un entorno de desarrollo.
Tarea: Cree un script que actúe sobre una lista de paquetes de código abierto (ej. curl, git, python3):
Defina una matriz (array) o una lista de variables con los nombres de los paquetes.
Use un bucle for para iterar sobre cada paquete.
Dentro del bucle, use type o which para comprobar si el binario del paquete está instalado en el sistema.
Utilice una estructura case para imprimir un mensaje personalizado: "Instalado" si se encuentra, o "Faltante - Alerta DevOps" si no se encuentra.
Este ejercicio refuerza la transparencia y el inventario de componentes necesarios en las metodologías modernas de desarrollo.
Ejercicio 4: Automatización de Tareas Administrativas y Red (ASIR Unidad 4 y LPI 109.1)
Objetivo: Programar una comprobación de conectividad de red y almacenamiento de logs.
Tarea: Escriba un script para verificar el estado de los servicios de red:
Utilice un bucle while que realice un ping a una dirección IP (ej. un servidor DNS de confianza como 8.8.8.8) cada 60 segundos.
Evalúe la conectividad. Si falla, debe usar un Here Document para enviar un mensaje de error simulado a un log o al administrador.
Implemente una función llamada limpiar_logs que use rm para borrar archivos temporales antiguos, aplicando los conocimientos de reutilización de código.
Planifique este script para que se ejecute en el futuro una sola vez usando el comando at.
Ejercicio 5: Personalización del Entorno de Trabajo (LPI 105.1 y ASIR RA1)
Objetivo: Configurar el entorno profesional del administrador de sistemas.
Tarea: Modifique los archivos de configuración de Bash del usuario (~/.bashrc):
Cree un alias para el comando ls que siempre muestre archivos ocultos y en formato de lista larga.
Defina una función en el archivo que acepte un argumento de directorio, cambie a ese directorio y liste su contenido automáticamente.
Configure la variable PS1 para que el prompt muestre el formato <usuario>@<host>:[directorio_actual]$.
Asegúrese de que estos cambios sean persistentes tras el reinicio del shell aplicando el comando source.
Estos ejercicios requieren que el alumno no solo escriba código, sino que también gestione permisos de ejecución (chmod +x) y comprenda la jerarquía del sistema de archivos de Linux.
