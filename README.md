# NOTAS DEL CURSO DE GIT Y GITHUB

> [!IMPORTANT]
> https://www.youtube.com/watch?v=9ZJ-K-zk_Go


## GIT

### CONFIGURACION INICIAL DE ALIAS Y EMAIL

- Acceder a todas las configuraciones:
* git config

- Accedemos a la configuracion global, system y local:
* git config --global (scope de usuario de una computadora)
* git config --system (scope total de la computadora)
* git config --local (scope de un repositorio)

- Vamos a la configuracion, dentro del scope que elijamos, y seleccionamos el nombre del usuario (el scope mas comun es --global)
* git config --global user.name ("nombre")

> [!NOTE]
> El nombre que elijamos tiene que estar entre comillas

- Vamos a la configuracion, dentro del scope que elijamos, y seleccionamos el email del usuario
* git config --global user.email ("email")


### VER TODAS LA CONFIGURACIONES QUE ESTAN LISTAS O YA ESTAN POR DEFECTO

* git config --list

- Para ver la lista de configuraciones dentro de un scope determinado:
* git config --(scope) --list


### CONFIGURACION DEL EDITOR DE CODIGO

* git config --(scope) core.editor ("code --wait")

> [!NOTE]
> "code" es el que se usa para el visual studio code (es como una palabra reservada)
> El --wait sirve para indicar que los cambios no se guarden hasta que se cierre el editor

### ACTIVAR COLORES

* git config (scope) color.ui true

### CONFIGURACION DE SALTO DE LINEA

> [!NOTE]
> Min 21:50 del curso

- Basicamente esta configuracion lo que hace es automatizar el salto de linea hacia abajo cuando llegamos al limite en una linea (solamente es necesario en Windows) 

- Esto es para evitar conflictos con distintos sistemas operativos

* git config (scope) core.autocrlf true (windows)
* git config (scope) core.autocrlf input (Mac, Linux o sistema basado en Unix)

### COMANDOS DE REPOSITORIO

- Inicializar un repositorio:

* git init

- Agregar archivos al area de "preparacion" (staging)

* git add (nombre archivo)
* git add . (sube todos los archivos de la carpeta)

> [!NOTE]
> Cuando ponemos el nombre del archivo debemos incluir la terminacion, es decir, .js, .css, etc

- Ver estados de los archivos

* git status

- Devolver un archivo del area staged

* git rm --cached (archivo)

### AGREGAR ARCHIVOS CON COMMIT

- Se suben los archivos "sin un mensaje" (posteriormente nos va a pedir que agreguemos un mensaje y se va a abrir el editor de codigo que hayamos configurado, y para guardar ese mensaje basta con cerrar el editor)
* git commit

- Se suben los archivos con un mensaje
* git commit -m "(mensaje del commit)" 

- Subimos todos los archivos aunque no esten en el area de "staging"
* git commit -a

### ELIMINAR ARCHIVOS DEL REPOSITORIO

* rm (archivo)
- De esta manera estamos indicando que queremos eliminar ese archivo pero este cambio tiene que ser subido al area de "staged" por lo cual deberiamos hacer un "commit add (archivo)"

### RESTAURAR UN ARCHIVO BORRADO

- Hay que tener en cuenta que sea un archivo que borramos pero no enviamos el cambio a git, es decir, que el archivo eliminado este en el area de staging y querramos desacer esa eliminacion

* git restore (archivo)

### VOLVER AL ULTIMO CAMBIO

- Si queremos desacer los cambios que hicimos y volver al ultimo commit de un archivo (siempre y cuando no haya un cambio subido al area de stage)

- Si el archivo existe, lo sobre escribe, pero si no existe lo crea

* git checkout (archivo)

### CAMBIAR NOMBRE DE UN ARCHIVO

- Este cambio se agrega directamente al area de staging por lo que tendriamos que hacer un commit y agregar este cambio al repo

* git mv (archivo a cambiar) (nuevo nombre)

### CAMBIAR LA FORMA EN QUE GIT STATUS MUESTRA LOS DATOS

- Mostrarlos de manera resumida

* git status -s
* git status --short

### VER LO QUE CONTIENE UN ARCHIVO COMMITED

- Muestra lo que contiene el ultimo commit de ese archivo, pero solo los cambios que tiene ese archivo

* git show (archivo)

### COMPARAR EL AREA DE STAGED CON LA COMMIT

- Lo rojo es lo que esta commited y lo verde lo que se agrego

* git diff --staged

### VER LOS DATOS DE LOS COMMITS

- Nos permite ver "id" del commit, el autor y la fecha

* git log
* git log --oneline (abreviado)
* git log --oneline --all (Nos muestra los de todas las ramas, aunque no estemos en ella)

- Cuando usamos la sentencia abreviada, podemos ver que el "id" del commit es de 7 caracteres (aunque en realidad el id en si es mas largo, solo que se muestra resumido). Esto no seria un problema si la cantidad de commits son poco, pero a medida que se van realizando mas es muy probable que esta id resumida coincida con la de otro commit. Por esto es que a veces deberemos configurar manualmente la cantidad de caracteres resumidos del id del commit que queremos ver:

* git config (scope) core.abbrev (cantidad que queremos en numero)

### VER DIFERENCIAS ENTRE COMMITS

- Es importante tener la configuracion de cantidad de digitos que se muestran cuando hacemos el "git log --oneline" para que cuando pongamos el numero del commit tambien sea de esa cantidad de digitos

- Para ver la diferencia entre 2 commits

* git diff (nro commit) (nro commit)

- Ver el nombre de los archivos que cambiaron en los commits

* git diff --name-only (nro commit) (nro commit)

- Si queremos ver los cambios a nivel de linea

* git diff --word-diff (nro commit) (nro commit)

### MODIFICAR COMMITS

- Se abriria nuestro editor de codigo y podriamos cambiar el nombre del commit en que estemos parados

* git commit --amend

- Modificamos el commit agregando un cambio

Tenemos, primero, que agregar al area de stage lo que querramos cambiar.
Luego cambiar el nombre del commit y ahi se van a guardar todos los cambios

### MODIFICAR COMMITS QUE NO SON EL ULTIMO

> [!NOTE]
> Es mas recomendable modificar el ultimo antes que tener que hacer esto

- Primero tenemos que decidir cuantos commits atras queremos volver

* git rebase -i head~(cantidad que queremos volver)

* git commit --ammend

- Cuando hayamos terminado con todos los cambios volvemos al ultimo commit (sin este paso, se pierden todos los ultimos commits)

* git rebase --continue

### DEVOLVER COMMITS AL AREA DE STAGING

- De esta manera estamos posicionando el puntero "HEAD" hacia otro commit anterior y devolviendo esos commits siguientes al area de staging por si queremos usarlos

* git reset --soft (nro commit)

Otra manera de hacer referencia a un commit es indicando cuantos commits atras del HEAD queremos volver 

* git reset --soft head~(cantidad a volver)

### DEVOLVER COMMITS AL AREA DE STAGING Y AL AREA DE TRABAJO

* git reset --mixed (nro commit)

### VOLVER AL ULTIMO COMMIT DESCARTANDO TODO LO ANTERIOR

- Es decir, volvemos al commit que seleccionemos de manera que no quede nada en el area de staging y el area de trabajo va a contener lo de ese commit

* git reset --hard (nro de commit)


### BRANCHES

### VER RAMAS

* git branch

### CREAR UNA RAMA

* git branch (nombre de la rama "convencion-de-escritura")

### CREAR UNA RAMA Y MOVER EL PUNTERO

* git checkout -b (branch)
* git switch -c (branch) !RECOMENDADA¡

### CAMBIAR ENTRE RAMAS

* git checkout (branch)
* git switch (branch) !RECOMENDADA¡

### BORRAR RAMAS

* git branch -d (rama)

> [!NOTE]
> No tenemos que estar parados en la rama que queremos borrar a la hora de hacerlo

### MODIFICAR RAMAS

- Modificar una rama que no es en la que estas ubicado

* git branch -m (rama a modificar) (nuevo nombre)

- Modificar la rama en la que estoy

* git branch -m (nombre nuevo)

### FUSIONAR RAMAS

- Primero necesito estar parado en la rama donde quiero que se fucione la rama a agregar

* git merge (rama a fusionar) 

- Si necesito desfusionar las ramas

* git reset --hard (nro commit)

> [!NOTE]
> Esto funciona igual que como esta explicado anteriormente, si sirve para desacer la fusion de las ramas, pero realmente estamos borrando parte de los cambios que hicimos

### MERGE CONFLICT

- Puede surgir un problema a la hora de hacer un merge si es que hay varios cambios que se solapan entre si cuando se van a juntar las ramas

- Hay varias opciones para solucionar esto y automaticamente cuando surge un error de estos, se abre el editor de codigo para que veamos las diferencias y como podemos solucionarlo

- Una vez resuelto ejecutamos el siguiente commando para continuar

* git merge --continue

### ETIQUETAR RAMAS

- git tag (nombre-tag)

- git tag (solo con este comando vemos todos los tags)

### GITIGNORE GLOBAL

- Para esto debemos hacer un archivo, en algun lado de la computadora, que sea .gitignore_global (creo que no hace falta que sea "_global") y dentro ponemos lo que nunca vamos a querer que se suba cuando hagamos un commit
 
- Configuramos para que por defecto lea ese archivo

* git config (scope) core.excludesfile (ruta del archivo)

### ALIAS EN GIT

- Cuando creamos un alias debemos indicar el comando a ejecutar pero sin el "git"

- El comando tiene que estar entre comillas dobles, pero si el comando ya incluye comillas, debemos cambiar estas por comillas simples

* git config (scope) alias.(nombre del alias que querramos crear) "(comando)"

- Para ejecutar el comando

* git (alias)


### GIT REFLOG

- Obtenemos las referencias de todos los lugares por los que el HEAD pasó

* git reflog


## GITHUB

### CLONAR UN REPOSITORIO REMOTO A LOCAL

- Primero necesitamos copiar la direccion del repositorio (por lo general se usa es HTTPS)

* git clone (direccion)

### CLONAR UN REPOSITORIO REMOTO DIRECTAMENTE A GITHUB

- Vamos a un repositorio que querramos agregar a nuestra cuenta y seleccionamos la opcion de "Fork"
- Vamos a tener pasos muy intuitivos para completarlo

### ACTUALIZAR EL REPOSITORIO LOCAL POR CAMBIOS EN EL REPOSITORIO REMOTO

* git pull

### SUBIR LOS CAMBIOS AL REPOSITORIO REMOTO

* git push

### MIGRAR REPOSITORIO LOCAL A UNO REMOTO

* git remote add origin (direccion del repositorio)
* git branch -M main 
* git push -u origin main

> [!NOTE]
> "main" es porque github tiene configurado como rama principal a "main", pero si nosotros lo cambiamos, tambien deberiamos cambiarlo en el comando
> El "-u" es para que se configure automaticamente para que no tengamos que hacer git push origin main cada vez que querramos subir los cambios

