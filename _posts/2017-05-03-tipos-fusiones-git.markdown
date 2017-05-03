

# Fusiones  en Git: Merge y Rebase #
---

## 01 Introducción

Cuando un usuario utiliza Git, tarde o temprano, debera utilizar ramas, que son un conjunto de commit en una línea de tiempo.

El esquema clásico de desarrollo con ramas en un repositorio de _Git_, es tener una rama principal, denominada _master_, donde tendremos código de forma estable, y conjunto de ramas con diferentes nombre como _desarrollo_ o _hostfix_, que se utilizaran para el desarrollo de código.

En algún momento debemos unir las ramas. ya sea entre varias ramas de _desarrollo_ o de una rama _desarrollo_ con la rama _master_. Este proceso se denomina  fusión o _merge_. Que consistira en mover un conjunto de _commit_ desde una rama a otra.

Existen varios formas de hacer de fusionar dos ramas, el resultado será el mismo. La diferencia sera en como lo hace.

Principalmente tendremos dos formas de realizar fusionar ramas.


## 02 Merge

 Tenemos dos ramas, por ejemplo rama _master_ y _desarrollo_, queremos fusionar la rama desarrollo sobre la rama _master_


![](/home/pepe/Descargas/Blog/AprendiendoGit/RepoGit/img/20170502-165541.png) 


Nos situamos en la rama hacia donde se dirige la fusión, en este caso la rama_master_, y realizamos el _merge_.


		git checkout master
		git merge desarrollo

Esta fusión realiza una "mezcla" , genera un nuevo _commit_ con el contenido de la rama _desarrollo_ en la rama _master_.

![](/home/pepe/Descargas/Blog/AprendiendoGit/imgs/merge2.jpg) 

Ahora podemos borrar las rama _desarrollo_ o seguir utilizandola para seguir desarrollando código.


## 03 Rebase

Es el otro tipo de fusión con un funcionamiento diferente, aunque tiene el mismo resultado. Este tipo de fusión lo que realiza es reorganización de los commits. 

Por ejemploi, tenemos las dos ramas del ejemplo anterior, _master_ y _desarrollo_.

![](imgs/20170503-012232.png)

Realizamos el  mismo proceso anterior, fusionar  la rama _desarrollo_ en la rama _master_.

Cuando ejecutamos un _rebase_, nos debemos situar en la rama que vamos a fusionar, al contrario que ocurria con el _merge_. Y ejecutamos.

	git checkout desarrollo
	git rebase master
	
Este comando mueve todos los commit de la rama _desarrollo_ a continuación de la rama _master_, el resultado sería.

![](imgs/20170503-012728.png)

El resultado es  un historial de commit mas limpio.

En el proceso de reorganización, a los commits se le ha asignado un nuevo identificador (hash). En algunos escenario, repositorios públicos, no es aconsejable utilizar _rebase_, 

Cuando realizas un _push_ descargas commits a tu repositorio local, si realizas un _rebase_, modificas los id de los commit, si realizas un _pull_ estos commits, con sus identificadores cambiados, se subiran al repositorio público. Si  otro desarrollador realiza un _pull_, obtendra un conjunto de commit con los id cambiado, que se integraran en su repositorio local y provocara muchos dolores de cabeza.

## 04 Rebase interactivo

Es una opción de _Rebase_ y permite realizar la reorganización de una forma manual. Continuando con el ejemplo anterior, si ejecutamos.

	git rebase -i desarrollo

Se nos abrira el editor que tenga configurado Git, por defecto vi, mostrando todos los commit de la rama desarrollo.

![](imgs/20170503-161445.png)

En la parte superior veremos los _commit_ con sus identificadores, y una opción que indica la acción que vamos a realizar sobre ese _commit_.

Entre las acciones que podemos realizar tenemos:

- **pick**: Sin modificación , no realizamos acción sobre ese commit.
- **squash**: Permite unir _commits_, el seleccionado con el anterior. El _commit_ debera tener un nuevo mensaje.
- **fixup**: Permite unir _commit_, utilizando el mensaje del primero.
- **edit**: Para editar el mensaje del _commit_.
- **drop**: Borra un commit, también eliminado la línea directamente.
- **exec**: Permite ejecutar un comando usando shell.

También podemos escoger un conjunto de commit, no toda la rama, para reorganizar. Como ejemplo.

	git rebase -i master~3

Selecciona los útimos 3 commits de la rama _master_ para reorganizar.


## 05 Conclusión

Normalmente se usa _merge_ para fusionar dos ramas, pero el comando _rebase_ debido a su limitación de no usarse en repositorios públicos, no es tan común, aunque tiene su utilidad para dejar un historial mas limpio.

El comando _rebase_ interactivo es muy útil para limpiar aquellos _commit_ que no aportan valor al historial, se pueden unir con otros, modificar su mensaje. Es un comando muy útil para que el historial de una rama sera mas comprensible.
