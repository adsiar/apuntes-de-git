### ssh

## Configuración SSH en Windows. 

Importante en linux hacer todo esto como usuario.
N o como root o te dara errores de autenticacion al subir por que las rutas son distintas. 
En caso de Windows si te d algun error la ruta de usuarios poir eu tenga espacion puedes crear la ruta en /c/[ruta].

comprobamos si ya tenemos una llave ssh en la ruta de nuestro home. 
```
cd ~/.ssh
ls
```
si salen ficheros *_rsa y *.rsa_pub es qua ya tenemos claves configuradas.
en tal caso decidimos si queremos usar esa misma o crear una nueva. 
crearemos una nueva. 

Por defecto las claves ssh se generan en  la carpeta oculta ~/.ssh/ pero podemos cambiar la ruta. 
en este ejemplo la cambiaremos a la carpeta ~/.keys/

1. creamos la carpeta oculta en `~/.keys/` 
Si eres de windows y pusiste caracteres expeciales en tu nombre de usuario te puede dar error la ruta 
en tal caso puedes crear la carpeta en `/c/.keys`
```
mkdir ~/.keys
cd ~/.keys
pwd
```
el comando pwd nos dirá en que ruta absoluta estamos. 
en mi caso de windows es.
`/c/Users/fitopaisa/.keys`

2. Creamos la llave con el comando
`ssh-keygen -t rsa -C "fitopaisa@hotmail.com"`
El correo a de ser el mismo que usaste en github
dejamos frase y contraseña vacíos para que no nos pida contraseña. 

Cuando nos pida la ruta y archivo ponemos la nuestra en vez de la que nos sugiere.
en mi caso esta.
`/c/Users/fitopaisa/.keys/github_rsa`
```
ssh-keygen -t rsa -C "fitopaisa@hotmail.com

/c/Users/fitopaisa/.keys/github_rsa

```
En caso de windows te genera la clave sin mas. 
en caso de linux te pedira que abras alguna ventanas mas y que navegues para generar entropia.

3. Para configurar ssh en una ruta especifica 
usamos ssh-agent en segundo plano con `eval "$(ssh-agent -s)"`
agregamos la ruta de la llave ejecuando `ssh-add /[ruta]/[archivo_rsa]`
```
$ eval "$(ssh-agent -s)"
$ ssh-add /c/Users/fitopaisa/.keys/github_rsa
```

## Codigo completo
```
mkdir ~/.keys
cd ~/.keys
pwd
ssh-keygen -t rsa -C "fitopaisa@hotmail.com"
/c/Users/fitopaisa/.keys/github_rsa
$ eval "$(ssh-agent -s)"
$ ssh-add /c/ruta-ssh/github_rsa

```
