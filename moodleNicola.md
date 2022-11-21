# Instal·lació de Moodle
Per instal·lar moodle necessitem: Apache, PHP i MariaDB

## Instal·lació de complements

### Apache

- Instal·lació de Apache


![image](https://user-images.githubusercontent.com/114423065/203127704-afe933bb-88cb-4b1f-afb0-26ab1d84a810.png)

- Comprovar que Apache funciona correctament des-de la maquina host


![image](https://user-images.githubusercontent.com/114423065/203127966-26bb4465-fb92-437f-a7d0-3059af31b8ae.png)

### MariaDB

- Instal·lació de MariaDB


![image](https://user-images.githubusercontent.com/114423065/203129660-c78df4dd-f018-4ab1-aa06-3d6589f0ac95.png)


- Configuració de MariaDB

![image](https://user-images.githubusercontent.com/114423065/203130285-8db94184-317b-4481-81b4-3d2544f9d4be.png)

- Reiniciarem el serveri de MariaDB

![image](https://user-images.githubusercontent.com/114423065/203130850-ec62543d-90e3-4f8a-9143-1045e500d0a3.png)


### PHP

- Afegir el repositori `ppa:ondrej/php`

![image](https://user-images.githubusercontent.com/114423065/203126632-1db1a4e4-9aa6-400d-974d-2c1b5bd68c91.png)

- Actualitzar `amb apt update`

- Instal·lar PHP 7.3

![image](https://user-images.githubusercontent.com/114423065/203127038-5be54abd-75df-4f6e-91d4-c0f1d3ba52f0.png)


## Descarrega i configuració de moodle
Amb la comanda `wget` descarregarem l'ultima versiò de moodle des-de la pàgina oficial.

`wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip`

![image](https://user-images.githubusercontent.com/114423065/203131762-9817a25f-821e-46f1-ab3f-b335f1745143.png)

Descomprimirem el fitxer amb unzip i el fitxer que acabem de descarregar. (nota, cal tenir el paquet zip instal·lat) 

![image](https://user-images.githubusercontent.com/114423065/203132044-556ae30a-9de7-49d1-961d-1ac238ee0963.png)

