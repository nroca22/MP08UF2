# Cas pràctic 2

## Índex
* Instalar Apache
* Instalar MariaDB
* Crear la base de dades d'Owncloud
* Instalar PHP amb els seus moduls
* Instalar Owncloud


# Instalar Apache
Instalem el servidor Apache amb la seguent comanda:
`sudo apt install apache2`

Desactivem el llista de directoris del servidor:
`sudo sed -i "s/Options Indexes FollowSymLinks/Options FollowSymLinks/" /etc/apache2/apache2.conf`

# Instalar MariaDB
Instalem el gestor de bases de dades MariaDB:
`sudo apt-get install mariadb-server mariadb-client -y`

I configurem la nostra instalació

`sudo mysql_secure_installation`

Per ultim reiniciem el servei de MariaDB
`sudo systemctl restart mariadb.service` o `sudo service mariadb.service restart`

# Creem la base de dades per Owncloud
Entrem a MariaDB
`sudo mysql -u root -p`

Creem la base de dades
`CREATE DATABASE owncloud;`

Creem l'usuari "owncloud" amb la seva contrasenya "Admin1234".
`CREATE USER 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234';`

Li donem accés a l'usuari que acabem de crear a la base de dades de owncloud
`GRANT ALL ON owncloud.* TO 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234' WITH GRANT OPTION;`
