#Práctica_Git_Francisco_Clemente_Fernández

Examen Domingo 15/09/2024 GIT/GITHUB Francisco_Clemente_Fernández

- ¿Qué comando utilizaste en el paso 11? ¿Por qué?
 
$ git reset --hard HEAD~1 

Este comando deshace el ultimo commit realizado eliminando también los cambios que teníamos en el WORKING COPY.

- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
  
En este punto usamos un  git reflog
para ver todos los identificadores de los comits que hemos realizado :

f499a8b (HEAD -> styled, main) HEAD@{0}: reset: moving to HEAD~1
681b680 HEAD@{1}: commit: Añado actualización del archivo git-nuestro.md al repo
f499a8b (HEAD -> styled, main) HEAD@{2}: checkout: moving from main to styled
f499a8b (HEAD -> styled, main) HEAD@{3}: commit: Añado archivo git-nuestro.md al repositorio
27c314a (origin/main, origin/HEAD) HEAD@{4}: clone: from https://github.com/franfernandez93/Pr-ctica_Git_Francisco_Clemente_Fern-ndez.gitf499a8b (HEAD -> styled, main) HEAD@{0}: reset: moving to HEAD~1

Acto seguido copiamos el identificador del commit que deseamos en este caso es  f499a8b y usamos el siguiente código:

$ git reset --hard f499a8b

esto nos recupera el commit que habíamos deshecho

- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
  
Situados en la rama **style** realizamos :

$ git merge main

Ahora la rama **styled** ha absorbido a la rama **main** 
 

- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

En mi caso no ha habido conflictos por que he realizado un git add de la modifciación del archivo y después he realizado un nuevo commit, una vez en este paso, he realizado un merge desde **styled** a **htmlify**

$ git merge htmlify
Updating f499a8b..f59628d
Fast-forward
*git-nuestro.md* | 21 ++++++++++-----------
 1 file changed, 10 insertions(+), 11 deletions(-)

En este paso la consola me muestra que ha realizado cambios en el archivo *git-nuestro.md* por que ha hecho un merge fast-forward realizando un total de 21 cambios en el archivo , añadiendo 10 inserciones y eliminando otras 11.


- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
  
$ git merge styled
Updating f499a8b..f59628d
Fast-forward
git-nuestro.md | 21 ++++++++++-----------
1 file changed, 10 insertions(+), 11 deletions(-)

En este paso la consola me muestra que ha realizado cambios en el archivo *git-nuestro.md* por que ha hecho un merge fast-forward realizando un total de 21 cambios en el archivo , añadiendo 10 inserciones y eliminando otras 11.

- ¿Qué comando o comandos utilizaste en el paso 25?

Para dibujar el grafo utilice el comando

$ git log --graph --decorate 

esto me muestra el grafo actual de la rama sin mostrarme fechas ni horas de una manera más ordenada. 
 
- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

Sí podría ser fast fordware, por que en la rama **main** , no teníamos un commit por encima que se quedase fuera y provocase una bifurcación , sino que, directamente en la rama **main** , creamos una rama nueva llamada **title** , con un posterior commit , esto hace que pudieses haber escalado por esa misma rama usando el fast forward , pero hemos forzado un no fast forward .
 
- ¿Qué comando o comandos utilizaste en el paso 27?

Para deshacer el merge sin perder los cambios del WORKING COPY he usado el comando:

$ git revert -m 1 (con el identificador del commit que realizamos al hacer el merge de **title** no fast forware ) 

Podría haber usado el comando: 

$ git reset --hard HEAD~1 , pero esto hubiese borrado lo que había en mi WORKING COPY

- ¿Qué comando o comandos utilizaste en el paso 28?
- 
Para descartar los cambios depués de haber  deshecho el merge anterior usamos el cogido:

$git reset --hard HEAD , esto descarta lo que hemos hecho anteriormente 

HEAD is now at 3ae2dc6 Revert "Merge branch 'title'no fast forware"para no borrar los cambios en el working copy

- ¿Qué comando o comandos utilizaste en el paso 29?
  
Para eliminar la rama title usamos :

$ git branch -D title
Deleted branch title (was 4b4646c).

- ¿Qué comando o comandos utilizaste en el paso 30?
 
Para rehacer el merge que hemos hecho primero debemos recuperar la rama **title** , que posteriormente hemos eliminado , para ello hacemos un reflog y buscamos el commit que realizamos al hacer el cambio al rama **title** , buscamos su identificador y usamos el sigueinte código:

$ git checkout -b title 4b4646c 

esto nos recupera  la rama **title** y nos cambia a dicha rama , una vez hecho esto, volveremos a la  rama main , y desde allí ejecutaremos el merge 
en mi caso me dice que los cambios están ya actualizados.
  
- ¿Qué comando o comandos usaste en el paso 32?
  
Para este paso haremos un reflog y buscaremos el commit donde inciamos por primera vez el archivo del poema, posteriormente usaremos 
$ git reset --hard (identificador del commit donde queremos ir)
  
- ¿Qué comando o comandos usaste en el punto 33?
  
Para volver al commit final donde le pusimos titulo al poema , hacemos un reflog y vemos el ID del commit donde añadimos el titulo final , posteriormente  usamos el comando:

$ git checkout ( id del commit donde añadimos el titulo del poema).




