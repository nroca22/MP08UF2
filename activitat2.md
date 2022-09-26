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
