Esta guía paso a paso proporciona las soluciones detalladas para los ejercicios propuestos, diseñadas para facilitar un **aprendizaje significativo** en alumnos de ASIR, integrando los conocimientos del manual del curso y los estándares de certificación del Linux Professional Institute (LPI).

### Guía de Soluciones: Automatización y Shell Scripting 

Para todos los scripts, es fundamental recordar que un script es un archivo de texto que el sistema interpreta como un programa. El proceso general para cada ejercicio debe ser: 

1\. Crear el archivo (ej. nano script.sh).  
2\. Escribir el código con el **shebang** correspondiente.  
3\. Guardar y asignar **permisos de ejecución** con chmod \+x script.sh. 

--------------------------------------------------------------------------------

### Ejercicio 1: Gestión de Procesos y Entorno 
**Objetivo:** Identificar procesos de un usuario y manipular el PATH.
* **Paso 1: Definir el intérprete.** Inicie con #!/bin/bash.
* **Paso 2: Capturar el argumento.** Use $1 para recibir el nombre de usuario.
* **Paso 3: Validar existencia.** Use id para verificar si el usuario existe en el sistema.
* **Paso 4: Modificar el entorno.** Añada el directorio de forma temporal a la variable PATH.

**Solución monitor\_procs.sh:** 
```bash
USUARIO=$1

if id "$USUARIO" >/dev/null 2>&1; then
    echo "Procesos actuales para el usuario: $USUARIO"
    ps -u "$USUARIO" -o user,comm
    # Añadir bin local al PATH temporalmente
    export PATH="$PATH:~/bin"
    echo "PATH actualizado temporalmente: $PATH"
else
    echo "Error: El usuario $USUARIO no existe en /etc/passwd"
    exit 1
fi

```

--------------------------------------------------------------------------------

### Ejercicio 2: Auditoría de Seguridad y Filtrado 
**Objetivo:** Buscar archivos SUID pertenecientes a root y generar un informe.
* **Paso 1: Búsqueda avanzada.** Use find con el parámetro \-perm para localizar el bit SUID (4000).
* **Paso 2: Filtrado y Redirección.** Use una tubería (|) hacia grep y el operador \>\> para añadir datos al informe sin borrar lo anterior.*
* **Paso 3: Verificación.** Imprima $? para confirmar que la operación se realizó con éxito.

**Solución auditoria\_suid.sh:**

```bash
#!/bin/bash
# Auditoría de archivos con bit SUID de root
echo "Iniciando auditoría de seguridad..."
find /usr/bin -perm -4000 -user root | grep "root" >> ~/informe_seguridad.txt

if [ $? -eq 0 ]; then
    echo "Informe actualizado correctamente. Código de salida: $?"
else
    echo "Hubo un problema durante la búsqueda."
fi
```

### Ejercicio 3: Lógica DevOps y Bucles 
**Objetivo:** Verificar dependencias de software mediante una matriz y estructuras de control.
* **Paso 1: Declarar la matriz.** Use la sintaxis de paréntesis para definir la lista de paquetes.
* **Paso 2: Iterar.** Use un bucle for para procesar cada elemento.
* **Paso 3: Lógica de selección.** Use case para gestionar los mensajes según el estado de instalación.

**Solución check\_dependencies.sh:**

```bash
#!/bin/bash
# Simulación de verificación de dependencias (SBOM)
PAQUETES=(curl git python3 figlet)

for PKG in "${PAQUETES[@]}"; do
    if which "$PKG" >/dev/null 2>&1; then
        ESTADO="instalado"
    else
        ESTADO="faltante"
    fi

    case $ESTADO in
        "instalado")
            echo "Software: $PKG - OK: Instalado"
            ;;
        "faltante")
            echo "Software: $PKG - Faltante - Alerta DevOps"
            ;;
    esac
done
```


### Ejercicio 4: Automatización Administrativa y Red 
**Objetivo:** Comprobar conectividad periódica y gestionar logs. 
* **Paso 1: Definir funciones.** Cree limpiar\_logs para reutilizar código de mantenimiento.
* **Paso 2: Bucle infinito.** Use while para la comprobación recurrente.
* **Paso 3: Mensajes estructurados.** Use un **Here Document** para redirigir bloques de error al log.

**Solución monitor\_red.sh:**

```bash
#!/bin/bash
# Monitoreo de conectividad y limpieza de logs

limpiar_logs() {
    echo "Limpiando archivos temporales..."
    rm /tmp/*.log 2>/dev/null
}

limpiar_logs

while true; do
    if ping -c 1 8.8.8.8 >/dev/null 2>&1; then
        echo "$(date): Conexión activa"
    else
        # Redirección mediante Here Document
        cat <<EOF >> ~/error_red.log
ALERTA DE RED:
Fecha: $(date)
Estado: Servidor DNS 8.8.8.8 inalcanzable.
EOF
    fi
    sleep 60
done
```

### Ejercicio 5: Personalización del Entorno (.bashrc) 

**Objetivo:** Configurar alias, funciones y el prompt de forma persistente.
* **Paso 1: Localización.** Estas líneas deben añadirse al archivo \~/.bashrc del usuario.
* **Paso 2: Crear Alias.** Use alias para comandos cortos.
* **Paso 3: Definir el Prompt.** Configure la variable PS1 con caracteres de escape.

**Contenido para añadir a \~/.bashrc:** 

```bash
# Personalización profesional del entorno

# Alias para listado detallado
alias ll='ls -al' 

# Función para navegación rápida
goto() {
    cd "$1" && ls -F
}

# Configuración del Prompt personalizado
export PS1="\u@\h:[\w]\$ " 

# Aplicar cambios inmediatamente: source ~/.bashrc
```
Para que estos ejercicios resulten efectivos, se recomienda que los alumnos utilicen el comando bash \-x para **depurar** sus scripts y observar cómo se expanden las variables y se ejecutan las estructuras paso a paso. 
