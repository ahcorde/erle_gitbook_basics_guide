# Installing Codiad in your BBB


#####Prerequisites

In order to install Codiad, you need some software in your board: apache2, php5, git, ... You can install
this software executing this command in the shell:

 `sudo apt-get update `
 `sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mcrypt git `
	
###Installation

Once, you have installed all the necessary software, change `apache2` `dir.conf`file:

` sudo vim /etc/apache2/mods-enabled/dir.conf`

and make the next change, mode index.php to the front:

(Press `shift` `I` to enter in the edit mode, make the changes, press `ESC` button and then write `:wq` to safe
and exit from vim)

`<IfModule mod_dir.c>`

`         DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm `

`</IfModule> `

Now, we have to configure Apache Virtual Hosts. To do so, move to:

`cd /etc/apache2/sistes-available `

and open `default` file:

`vim default`

Add `Alias ... </Directory>` lines:

` 
	. . .
    <Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all
    </Directory>

    Alias /codiad /home/demouser/Codiad
    <Directory "/home/demouser/Codiad">
            Options -Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    . . .
`
restart apache2:

`sudo service apache2 restart `

Now, let's clone Codiad. Firstly, go to `/var/www`using `cd` command in your board. Once you are there:

`git clone https://github.com/Codiad/Codiad.git `
`cd Codiad `

and copy the example configuration file:

` cp config.example.php config.php `

Give the needed permissions to the folders that are going to be used:

`sudo chown -R www-data config.php workspace/ plugins/ themes/ data/ `

restart again apache, 

`sudo service apache2 restart `

and open your favourite browser, type the next ip: `192.16.7.2:8080/Codiad/` ,
follow the instalaion process!

If you would like to add [plugins] (http://market.codiad.com/) , download, unzip them and place it in Codiad/plugins.

You can [set] (https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-codiad-a-web-based-ide-on-an-ubuntu-vps)
password protection, putting another layer. (Password Protect the IDE Interface section)

Sources:

https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-codiad-a-web-based-ide-on-an-ubuntu-vps
https://github.com/Codiad/Codiad/wiki/Installation