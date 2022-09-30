# Cas pràctic 2

## Índex
* Instalar Apache
* Instalem MariaDB
* Creem la base de dades per Owncloud
* Instalem PHP i tots els moduls necessaris
* Instalem Owncloud


### Instalar Apache
Instalem el servidor Apache amb la seguent comanda:
`sudo apt install apache2`

![captura1](caspr2cap1.png)

Desactivem el llista de directoris del servidor:
`sudo sed -i "s/Options Indexes FollowSymLinks/Options FollowSymLinks/" /etc/apache2/apache2.conf`

![captura1](caspr2cap2.png)

### Instalem MariaDB
Instalem el gestor de bases de dades MariaDB:
`sudo apt-get install mariadb-server mariadb-client -y`

![captura1](caspr2cap3.png)

I configurem la nostra instalació

`sudo mysql_secure_installation`

![captura1](caspr2cap4.png)

Tot seguit, ens demanarà unes opcións de configuració;
* Change the root password: no
* Remove anonymous users?: y
* Disallow root login remotely?: y
* Remove test databases and acces to it?: y
* Reload privilege tables now?: y

Totes aquestes són opcións de seguretat.

Per ultim reiniciem el servei de MariaDB
`sudo systemctl restart mariadb.service`

![captura1](caspr2cap5.png)

### Creem la base de dades per Owncloud
Entrem a MariaDB

`sudo mysql -u root -p`

![captura1](caspr2cap6.png)

Creem la base de dades

`CREATE DATABASE owncloud;`

![captura1](caspr2cap7.png)

Creem l'usuari "owncloud" amb la seva contrasenya "Admin1234".

`CREATE USER 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234';`

![captura1](caspr2cap8.png)

Li donem accés a l'usuari que acabem de crear a la base de dades de owncloud

`GRANT ALL ON owncloud.* TO 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234' WITH GRANT OPTION;`

![captura1](caspr2cap9.png)

Apliquem els cambis amb  `FLUSH PRIVILEGES;` i `EXIT;` i sortim.

![captura1](caspr2cap10.png)

### Instalem PHP i tots els moduls necessaris
`sudo apt-get install software-properties-common -y`

![captura1](caspr2cap11.png)

`sudo add-apt-repository ppa:ondrej/php`

![captura1](caspr2cap12.png)

Actualitzem els paquets que acabem d'afegir amb
`sudo apt update`

Instalem PHP amb tots els moduls que necessitarem
`sudo apt install php7.4 libapache2-mod-php7.4 php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-apcu php7.4-smbclient php7.4-ldap php7.4-redis php7.4-gd php7.4-xml php7.4-intl php7.4-json php7.4-imagick php7.4-mysql php7.4-cli php7.4-mcrypt php7.4-ldap php7.4-zip php7.4-curl -y`

Després de la instalació editem el fitxer php.ini i cambiem alguns dels seus valors
`sudo nano /etc/php/7.1/apache2/php.ini`

Els valors a cambiar són els seguents:
`file_uploads = On`
`allow_url_fopen = On`
`memory_limit = 256M`
`upload_max_filesize = 100M`
`display_errors = Off`
`date.timezone = Europe/Madrid`

### Instalem Owncloud
Descarregem la ultima versió del programa i descomprimim els fitxers, amés movem aquestos fitxers d'Owncloud a "/var/www/html/owncloud"

`cd /tmp && wget https://download.owncloud.com/server/stable/owncloud-complete-latest.zip`

`unzip owncloud-10.0.8.zip`

`sudo mv owncloud /var/www/html/owncloud/`

Cambiem el propietari i permís dels directoris d'Owncloud. www-data per a que els pugui utilitzar Apache, 755 para que els puga executar i llegir cualsevol usuari de linux.

`sudo chown -R www-data:www-data /var/www/html/owncloud/`

`sudo chmod -R 755 /var/www/html/owncloud/`
