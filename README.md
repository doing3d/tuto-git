## Apuntes de comandos Git

### Configuracion de usuario local
git config --global , configuracion global para la maquina local:

        git config --global user.name <"nombre usuario git">

user.name"nombre del autor"
user.email"correo"

### Iniciar git
iniciar repositorio git en directorio raiz.

    git init


#### Nombre de archivo para ignorar ficheros:
.gitignore , archivo donde se especifican los ficheros para ignorar del reporsitorio.

### Comandos mas usados
Añadir ficheros al stage.

    git add <>

Guardar cambios haciendo commit a los ficheros en stage.

    git commit -m "comentario para el commit" , 

Estado de los ficheros: con cambios, pendientes de añadir.

    git status

Linea de commits hechos en la rama.

    git log

Desplazamiento del head hacia commits usando el hash, el tag o al ultimo commit de la rama.

    git checkout <hash/tag/branch>

Restaruar el fichero que aun no sean añadido al stage (git add).

    git restore </fichero>

* comando nuevo separado de git checkout.

Etiquetar un commit con un nombre. El tag se aplica en el commit donde se ubica el head.

    git tag <name_n>

Listado de tags.

    git tag

Crear nueva rama.

    git branch <>

Cambiarse a otra rama.

    git switch <>

Eliminar una rama.

    git branch -d <flujo>

- al eliminar se quita la referncia a la rama/flujo pero todos los commits siguen exitiendo y son solo acessibles por su hash.
- limpia el log para simplificar el arbol del proyecto.

### Comandos para guardar cambios sin lanzar commit

***git stash***, guardado temporal (WIP) de todos los ficheros aun no comiteados sin hacer un commit en la rama.

***git stash push -m "<>"***, **(Recomendado)** guardado de stash con un mensaje.

***git stash list***, listar todos los stash guardados.

***git stash apply stash@{<>}***, recupera un stash con el numero de la lista sin borrarlo de la lista.

***git stash apply***, recupera el ultimo stash realizado sin borrarlo de la lista.

***git stash clear***, borra toda la lista de stash y no se pueden recuperar (usar solo al final).


***git stash pop*** - recupera el ultimo stash realizado y lo borra de la lista.

***git stash drop stash@{<>}*** - eliminar un stash de la lista.

***git reflog*** - log completo de aciones.

### Comando de git reset

git reset <fichero>, reset/quitar cambios añadidos al stage con git add.

git reset --hard <hash> , remover/devolver commits a la rama main.

### Como hacer ***Merge*** entre ramas

1) Hacer checkout (moverse) a la rama donde de quiere agregar los cambios.
2) Usar el comando:

    * ***git merge --no-ff </rama/>*** 

donde:
    
* </rama/>: nombre de la rama donde estan los cambios.

*  (--no-ff): para que el merge tenga commit y aparezca en el arbol de cambios.


3) Para este caso se abrira un archivo de texto donde se debe escribir el commit. Despues de escribir el commit guardar el archivo y cerrar la pestaña del archivo  para que Git continue con el merge.

Si el merge es exitoso en el terminal aparece un resumen de los ficheros actualizados con los lineas añadidas y lineas eleminadas.



## Comandos para interactuar entre ficheros locales y Github

### Subir ficheros locales a github por primera vez
***git remote add origin (url del repositorio)*** , asociar repositorio local con un reporitorio en github.

***git push -u origin (branch)***, subir los ficheros al repositorio de github.

### Comandos para sincronizar ficheros en Github

***git fetch***, descargar solo los cambios del arbol de commits.

***git pull***, descargar ficheros del reporsitorio en github.

***git push***, sincronizar los ficheros locales con el repositorio de github.

### Clonar repositorio desde github

**git clone </URL/>** - direccion https del repositorio a clonar

Para sincronizar cambios locales al repositorio clonado ejecutar los comandos:

1) fetch
2) pull
3) push

** Aplica para solo repositorios propios.

### Comando para sobreescribir los ficheros de un repositoro en Github por un nuevo proyecto

1) remover el "origin" del antiguo repositorio.

    ***git remote rm origin***

2) añadir un "origin" en el nuevo repositorio.

    ***git remote add origin (url del antiguo repo)***

3) forzar el push del nuevo repo a Github

    ***git push -f origin main***

### Prueba de merge de rama de desarrollo a rama de release

Este texto fue añadido en la rama "main" de desarrollo.

Segundo texto añadido en la rama "main" de desarrollo.

Prueba de cambio de nombres.
