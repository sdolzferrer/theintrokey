# Cuestionario de Autoevaluación: Shell Scripting Avanzado (ASIR/LPI)
## I. Fundamentos y Estructura
### 1. ¿Qué función cumple la línea #!/bin/bash al inicio de un script?
a) Es un comentario para el programador.  
b) Indica al sistema operativo qué programa debe interpretar las instrucciones del archivo.  
c) Borra el historial de comandos antes de empezar.  
### 2. Si creas un script llamado mantenimiento.sh, ¿cuál es el comando correcto para permitir su ejecución directa como ./mantenimiento.sh?
a) ls -l mantenimiento.sh.  
b) bash mantenimiento.sh.  
c) chmod +x mantenimiento.sh.  
### 3. ¿Cuál es la diferencia entre ejecutar un script con ./script.sh y hacerlo con source script.sh?
a) ./script.sh lo ejecuta en una sub-shell, protegiendo el entorno actual; source lo ejecuta en la sesión activa, permitiendo modificar variables de entorno.  
b) No hay ninguna diferencia, ambos son idénticos.  
c) source solo funciona para scripts que no tienen el shebang.  

--------------------------------------------------------------------------------
## II. Gestión de Variables y Entorno
### 4. ¿Qué comando utilizarías para que una variable local llamada MI_APP esté disponible para todos los subprocesos e hijos generados desde el shell?
a) set MI_APP.  
b) export MI_APP.  
c) env MI_APP.  
### 5. En un script, ¿qué almacena la variable especial $#?
a) El código de salida del último comando ejecutado.    
b) El nombre del script que se está ejecutando.  
c) El número total de argumentos pasados al script.  
### 6. Si ejecutas un comando y quieres saber inmediatamente si tuvo éxito o falló, ¿qué variable debes consultar y qué valor indica éxito?
a) $0 con valor "success".    
b) $@ con valor 1.  
c) $? con valor 0.  

--------------------------------------------------------------------------------
## III. Redirección y Lógica
### 7. ¿Qué operador usarías para guardar la salida de un comando en un archivo sin borrar el contenido que ya existe en él?
a) >.    
b) >>.  
c) |.  
### 8. En el script de auditoría de seguridad, se utilizó la redirección 2> /dev/null. ¿Cuál es su propósito?
a) Guardar los errores en un archivo llamado /dev/null.    
b) Descartar cualquier mensaje de error para que no aparezca en pantalla.  
c) Duplicar la salida de errores en la salida estándar.  
### 9. ¿Qué estructura de control es la más adecuada para realizar una tarea repetitiva sobre una lista definida de elementos, como una matriz de paquetes de software?
a) if / then / else.    
b) case.  
c) for.  

--------------------------------------------------------------------------------
## IV. Configuración y Personalización
### 10. Deseas crear un alias persistente llamado update que ejecute sudo apt update. ¿En qué archivo local del usuario deberías guardarlo?
a) /etc/profile.    
b) ~/.bashrc.  
c) /etc/skel.  

--------------------------------------------------------------------------------
Clave de Respuestas sugerida:
1. b | 2. c | 3. a | 4. b | 5. c | 6. c | 7. b | 8. b | 9. c | 10. b
