# Installing Codiad in your BBB


#####Prerequisites

PAra instalar Codiad, necesitas cierto sotfware en la placa: apache2, php5, git, ... Puedes instalarlo ejecutando en el siguiente comando en la shell:

 `sudo apt-get update `
 `sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mcrypt git `
	
###Instalación

Una vez que tengas todo el software necesario instalado, cambia el fichero de `apache2` `dir.conf`:

` sudo vim /etc/apache2/mods-enabled/dir.conf`

y haz el siguiente cambio, modo index.php al frente:

(Presiona `shift` `I` para entrar en el modo edición, haz los cambios, presina el boton `ESC` y luego escribe `:wq` para guardar y salir de de vim)

`<IfModule mod_dir.c>`

`         DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm `

`</IfModule> `

Ahora, necesitamos configurar Apache Virtual Hosts. Para hacerlo, ve a:

`cd /etc/apache2/sistes-available `

y abre el fichero `default`:

`vim default`

añade ` Alias ... </Directory> ` :

`	. . . `

`    <Directory /var/www/> `

`            Options Indexes FollowSymLinks MultiViews `

`            AllowOverride None `

`            Order allow,deny `

`            allow from all `

`    </Directory> `

`    Alias /codiad /home/demouser/Codiad `

`    <Directory "/home/demouser/Codiad"> `

`            Options -Indexes FollowSymLinks MultiViews `

`            AllowOverride All `

`            Order allow,deny `

`            allow from all `

`    </Directory> `

`    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/`

`    . . . `

reinicia apache2:

`sudo service apache2 restart `

Ahora, vamos a clonar Codiad. Primero ve a `/var/www` usando el comando `cd` en tu placa. Una vez que entres:

`git clone https://github.com/Codiad/Codiad.git `
`cd Codiad `

y copia el fichero de configuración de ejemplo:

` cp config.example.php config.php `

Da permisos a las carpetas que van a ser usadas:

`sudo chown -R www-data config.php workspace/ plugins/ themes/ data/ `

Reinicia apache de nuevo,

`sudo service apache2 restart `

y abre tu navegador favorito, introduce la siguiente ip: `192.16.7.2:8080/Codiad/` , sigue el proceso de instalación!

Si quieres añadir algún [plugins](http://market.codiad.com/) , descargaló, descomprimelo y situalo en Codiad/plugins.

Puedes [poner](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-codiad-a-web-based-ide-on-an-ubuntu-vps) una protección de contraseña, añadiendo otra capa. 

##### Generado SSH Key para usar Git

Si quieres hacer push/pull, necesitas generar una `ssh key` y linzarla a tu cuenta de Git.

1.- Genera una nueva clave dentro de directorio `/var/www/.ssh `:

`ssh-keygen -t rsa -C "your_email@example.com" `

Siguiente, se le pedirá que introduzca una contraseña.

2.- Cambia el propietario de la clave a `www-data` (el grupo de apache2):

` chown www-data:www-data id_rsa `
` chown www-data:www-data id_rsa.pub `

3.- Luego añade tu nueva clave al ssh-agent:

`eval "$(ssh-agent -s)" `
`ssh-add var/www/.ssh/id_rsa `

4.- Añade la SSH Key a tu cuenta de GitHub: copia el contenido de `id_rsa.pub` y copialo en tu cuenta ( new SSH Key).

5.- Intenta : ` ssh -T git@github.com `

#####Recomendaciones

Cuando clonas un repositorio de git en Codiad. Primero crea un nuevo proyecto. Situate en el directoria del proyecto, y
`git clone `  el proyecto usando la URL con HTTPS. Luego, cambia el fichero `.git/config ` y reemplaza la URJ por la URL SSH. Esto significa  Esto significa hacer el siguiente cambio de valor de `url`:

De `url= https://github.com/... .git` a `url =git@github.com:... .git`

Ahora intenta hacer un `git pull `. Si estas usando `CodeGit`, haz click izquierdo en el directorio donde tengas clonado el proyecto y haz click en `Open Codegit`. Una nueva ventana aparecerá, haz click en `setting` y escribe tu nombre y tu dirección de email. Ahora, cierra la ventana e intenta hacer un `pull`.

Problema: Cuando reseteas la BBB la clace ssh se lee de `/etc/` de nuevo, si escribe en el Terminal de Codiad: `git pull `, verás un error de `Permission denied`. Pero, CodeGit esta funcionando correctamente. utiilza la interfaz CodeGit para hacer tus push/pulls.

Fuentes:

https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-codiad-a-web-based-ide-on-an-ubuntu-vps

https://github.com/Codiad/Codiad/wiki/Installation

https://help.github.com/articles/generating-ssh-keys/
