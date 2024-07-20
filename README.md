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

# AGREGAR ARCHIVOS CON COMMIT

- Se suben los archivos "sin un mensaje" (posteriormente nos va a pedir que agreguemos un mensaje y se va a abrir el editor de codigo que hayamos configurado, y para guardar ese mensaje basta con cerrar el editor)
* git commit

- Se suben los archivos con un mensaje
* git commit -m "(mensaje del commit)" 

- Subimos todos los archivos aunque no esten en el area de "staging"
* git commit -a

# ELIMINAR ARCHIVOS DEL REPOSITORIO

* rm (archivo)
- De esta manera estamos indicando que queremos eliminar ese archivo pero este cambio tiene que ser subido al area de "staged" por lo cual deberiamos hacer un "commit add (archivo)"

# RESTAURAR UN ARCHIVO BORRADO

- Hay que tener en cuenta que sea un archivo que borramos pero no enviamos el cambio a git, es decir, que el archivo eliminado este en el area de staging y querramos desacer esa eliminacion

* git restore (archivo)

# VOLVER AL ULTIMO CAMBIO

- Si queremos desacer los cambios que hicimos y volver al ultimo commit de un archivo (siempre y cuando no haya un cambio subido al area de stage)

- Si el archivo existe, lo sobre escribe, pero si no existe lo crea

* git checkout (archivo)

- Si lo que queremos es volver si o si al ultimo cambio, descartando si hay algun cambio en el area de stage (esto tambien descarta lo guardado en el area de staging)

* git reset --hard

# CAMBIAR NOMBRE DE UN ARCHIVO

- Este cambio se agrega directamente al area de staging por lo que tendriamos que hacer un commit y agregar este cambio al repo

* git mv (archivo a cambiar) (nuevo nombre)

# CAMBIAR LA FORMA EN QUE GIT STATUS MUESTRA LOS DATOS

- Mostrarlos de manera resumida

* git status -s
* git status --short

# VER LO QUE CONTIENE UN ARCHIVO COMMITED

- Muestra lo que contiene el ultimo commit de ese archivo, pero solo los cambios que tiene ese archivo

* git show (archivo)