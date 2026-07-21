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

Restaura un fichero modificado al estado del ultimo commit realizado.

        git restore </fichero>

* comando nuevo separado de git checkout.
* funciona cuando el fichero esta marcado como modificado. 

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

***git stash***, guarda todos los ficheros modificados (Work In Progress) sin hacer un commit en la rama.

Guardado de stash con un mensaje **(Recomendado)**:

        git stash push -m "<>"

Listar todos los stash guardados:

        git stash list

Aplicar un stash especifico en base a su numero sin borrarlo de la lista de stash:

        git stash apply </numero>

Recupera el ultimo stash realizado (stash 0) sin borrarlo de la lista.

        git stash apply

#### Los siguientes comandos borran los stash de la lista y no se pueden recuperar.

* Borrar toda la lista de stash realizados:
        
        git stash clear


* Recupera el ultimo stash realizado y lo borra de la lista:

        git stash pop

* Eliminar un stash especifico de la lista:

        git stash drop stash@{</numero>}

Log completo de aciones.

        git reflog

### Comando de git reset

git reset <fichero>, reset/quitar cambios añadidos al stage con git add.

git reset --hard <hash> , remover/devolver commits a la rama main.

### Como hacer ***Merge*** entre ramas

1) Hacer **checkout** (moverse) a la rama en donde se quiere colocar los cambios.
2) Usar el comando:

        git merge --no-ff </rama/>

    donde:
    
    * </rama/>: nombre de la rama donde estan los cambios.

    *  (--no-ff): para que el merge tenga commit y aparezca en el arbol de cambios.


3) Para este caso se abrira un archivo de texto donde se debe escribir el commit. Despues de escribir el commit guardar el archivo y cerrar la pestaña del archivo  para que Git continue con el merge.

Si el merge es exitoso en el terminal aparece un resumen de los ficheros actualizados con los lineas añadidas y lineas eliminadas.



## Comandos para interactuar entre ficheros locales y Github

### Subir ficheros locales a github por primera vez
Asociar repositorio local con un reporitorio en github.

        git remote add origin (url del repositorio)

Subir los ficheros al repositorio de github.

        git push -u origin (branch)

* nombre **origin** por estandar pero puede cambiarse.
* **(brach)** nombre de la rama que se quiere cargar al repositorio.

### Comandos para sincronizar ficheros en Github

Descargar solo los cambios del arbol de commits.

        git fetch

Descargar ficheros del reporsitorio en github.

        git pull

Sincronizar los ficheros locales con el repositorio de github.

        git push

### Clonar repositorio desde github

        git clone </URL/>

* direccion https del repositorio a clonar

Para sincronizar cambios locales al repositorio clonado ejecutar los comandos:

1) fetch
2) pull
3) push

** Aplica para solo repositorios propios.

### Reutilizar un repositorio ya creado en Github con un nuevo proyecto y subir nuevos ficheros

1) En el proyecto enlazado al repositorio remover el "origin" para desincronizar:

            git remote rm origin

2) En el nuevo proyecto añadir "origin" con el URL del repositorio:

            git remote add origin (url del repositorio ya creado)

3) forzar el push del nuevo repo a Github con la rama deseada:

            git push -f origin (branch)

### Prueba de merge de rama de desarrollo a rama de release

Este texto fue añadido en la rama "main" de desarrollo.

Segundo texto añadido en la rama "main" de desarrollo.

Prueba de cambio de nombres.
