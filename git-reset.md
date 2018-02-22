# Git Reset

Es muy buena práctica hacer  un respaldo de su bitácora de logs, sobre todo si vamos a hacer uso en cualquier momento de git reset, lo podemos hacer desde nuestra terminal de la siguiente forma:
`git log > bitacora_log.txt`


Hay 3 tipos de reset en git que son:

`git reset --soft [SHA 1]`: Elimina los cambios y nos lleva hasta el staging.

`git reset --mixed [SHA 1]`: Elimina los cambios y los mantiene en el working directory, osea todavía no están agregados no han pasado por git add.

`git reset --hard [SHA 1]`: Elimina absolutamente todo hasta el commit que desee o hasta el inicio de los tiempos del primer SHA1,pudiendo borrar incluso la carpeta enla que están contenidos los archivos de nuestro proyecto, por lo que tener un respaldo de los logs es altamente recomendable.


## git reset --soft <SHA1>

Elimina el commit, pero los archivos se mantienen en el **staging área** (en este paso puedes añadir mas archivos con git add -A), listo para hacer commit.

Por ejemplo, si tienes 20 commits y se quiere resetear desde el commit 15, el commit 16, 17, 18, 19 y 20 se "perderán, podrás visualizar en el stating area las modificaciones de esos commits, por lo tanto, si vuelves a realizar un commit con todos esas modificaciones se agregará en un solo commit, en este caso el commit numero 16.


## git reset --mixed <SHA1>

El funcionamiento es similar al reset --soft solo que con **--mixed** los archivos no se mantienen en el Staging Area y hay que vovler a añadirlos para hacer un commit, es decir, descarta cambios y quita commits dejando los archivos en el directorio de trabajo.


## git reset --hard <SHA1>

Elimina los cambios incluso del **working directory**, es el más peligroso de todos porque podemos perder parte de nuestro trabajo.

Cuando decimos que podemos perderlos es porque si tenemos los archivos en el **staging area** y hacemos un **reset --hard** sin más, perderíamos todo lo que tuviéramos, incluso del directorio de trabajo.

**Si y solo si** tenemos archivos en **untracked files** que son recientemente agregados, el **reset --hard** no los podra manipular, por lo que si ejecutamos el comando los mantendrá en el working directory.

Es importante tener siempre un respaldo de los **hash** de los commits porque podemos volver a nuestro último commit con un **reset --hard <ULTIMO_COMMIT>** y tener toda nuestra historia.

En conclusión, **reset --hard** hace lo siguiente:

1. Devolver al commit indicado.
2. Quitar archivos de staging.
3. Quitar archivos del working directory.

