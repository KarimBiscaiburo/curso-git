### NOTAS DEL CURSO DE GIT Y GITHUB

> [!IMPORTANT]
> https://www.youtube.com/watch?v=9ZJ-K-zk_Go


## GIT

# CONFIGURACION INICIAL DE ALIAS Y EMAIL

- Acceder a todas las configuraciones:
* git config

- Accedemos a la configuracion global, system y local:
* git config --global (scope de usuario de una computadora)
* git config --system (scope total de la computadora)
* git config --local (scope de un repositorio)

- Vamos a la configuracion, dentro del scope que elijamos, y seleccionamos el nombre del usuario (el scope mas comun es --global)
* git config --global user.name ("nombre")

> [!NOTA]
> El nombre que elijamos tiene que estar entre comillas

- Vamos a la configuracion, dentro del scope que elijamos, y seleccionamos el email del usuario
* git config --global user.email ("email")


# VER TODAS LA CONFIGURACIONES QUE ESTAN LISTAS O YA ESTAN POR DEFECTO

* git config --list

- Para ver la lista de configuraciones dentro de un scope determinado:
* git config --(scope) --list


# CONFIGURACION DEL EDITOR DE CODIGO

* git config --(scope) core.editor ("code --wait")

> [!NOTA]
> "code" es el que se usa para el visual studio code (es como una palabra reservada)
> El --wait sirve para indicar que los cambios no se guarden hasta que se cierre el editor

# ACTIVAR COLORES

* git config (scope) color.ui true

# CONFIGURACION DE SALTO DE LINEA

> [!NOTA]
> Min 21:50 del curso

- Basicamente esta configuracion lo que hace es automatizar el salto de linea hacia abajo cuando llegamos al limite en una linea (solamente es necesario en Windows) 

- Esto es para evitar conflictos con distintos sistemas operativos

* git config (scope) core.autocrlf true (windows)
* git config (scope) core.autocrlf input (Mac, Linux o sistema basado en Unix)

# COMANDOS DE REPOSITORIO

- Inicializar un repositorio:

* git init

- Agregar archivos al area de "preparacion" (staging)

* git add (nombre archivo)
* git add . (sube todos los archivos de la carpeta)

> [!NOTA]
> Cuando ponemos el nombre del archivo debemos incluir la terminacion, es decir, .js, .css, etc

- Ver estados de los archivos

* git status

- Devolver un archivo del area staged

* git rm --cached (archivo)