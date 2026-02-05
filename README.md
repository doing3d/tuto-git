## Apuntes de comandos Git

### Configuracion de usuario local
git config --global , configuracion global para la maquina local:
    user.name"nombre del autor"
    user.email"correo"

### Iniciar git

git init , iniciar repositorio git en directorio raiz.

#### Nombre de archivo para ignorar ficheros:
.gitignore , archivo donde se especifican los ficheros para ignorar del reporsitorio.

### Comandos mas usados

git add <> , añadir ficheros para hacer commit.

git commit -m "comentario para el commit" , hacer fotografia, guardar cambios.

git status , estado de los ficheros: con cambios, pendientes de añadir.

git log , linea de commits hechos en la rama.

git checkout <fichero/hash/tag> , restaurar cambios guardados del fichero al del ultimo commit, desplazamiento entre commits usando el hash o el tag.

git restore <fichero> , restaruar los cambios guardados del fichero que aun no sean añadido al stage (git add), comando nuevo separad de hit checkout.

git tag <name_n>, etiquetar un commit con un nombre, tag en donde se ubica el head.

git tag, listado de tags.

git branch <>, crear nuevo flujo.

git switch <>, cambiar a otro flujo con nombre <>.

git merge , combinar ficheros de un flujo a otro.

git branch -d <flujo>, eliminar una rama
- al eliminar se quita la referncia a la rama/flujo pero todos los commits siguen exitiendo y son solo acessibles por su hash.
- limpia el log para simplificar el arbol del proyecto.

### Comandos para guardar cambios sin lanzar commit

git stash, guardado temporal (WIP) de todos los ficheros aun no comiteados sin hacer un commit en la rama.

git stash push -m "<>", guardado de stash con un mensaje.

git stash list, listar todos los stash guardados.

git stash apply stash@{<>}, recupera un stash con el numero de la lista sin borrarlo de la lista.

git stash apply, recupera el ultimo stash realizado sin borrarlo de la lista.

git stash clear, borra toda la lista de stash y no se pueden recuperar (usar solo al final).


git stash pop, recupera el ultimo stash realizado y lo borra de la lista.

git stash drop stash@{<>}, eliminar un stash de la lista.

git reflog, log completo de aciones.

### Comando de git reset

git reset <fichero>, reset/quitar cambios añadidos al stage con git add.

git reset --hard <hash> , remover/devolver commits a la rama main.

## Comandos para interactuar entre ficheros locales y Github

### Subir ficheros locales a github por primera vez
***git remote add origin (url del repositorio)*** , asociar repositorio local con un reporitorio en github.

***git push -u origin (branch)***, subir los ficheros al repositorio de github.

### Comandos para sincronizar ficheros en Github

***git fetch***, descargar solo los cambios del arbol de commits.

***git pull***, descargar ficheros del reporsitorio en github.

***git push***, sincronizar los ficheros locales con el repositorio de github.

### Comando para sobreescribir los ficheros de un repositoro en Github por un nuevo proyecto

1) remover el "origin" del antiguo repositorio.

***git remote rm origin***

2) añadir un "origin" en el nuevo repositorio.

***git remote add origin (url del antiguo repo)***

3) forzar el push del nuevo repo a Github

***git push -f origin main***

### prueba de merge de rama de desarrollo a rama de release

Este texto fue añadido en la rama "main" de desarrollo.
