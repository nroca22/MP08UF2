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

- Instal·lar PHP 8.0, php8.0-curl i php8.0-zip

![image](https://user-images.githubusercontent.com/114423065/204081197-33b93682-f691-44bf-ad64-46bbef43f7af.png)


## Descarrega i configuració de moodle
Amb la comanda `wget` descarregarem l'ultima versiò de moodle des-de la pàgina oficial.

`wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip`

![image](https://user-images.githubusercontent.com/114423065/203131762-9817a25f-821e-46f1-ab3f-b335f1745143.png)

Descomprimirem el fitxer amb unzip i el fitxer que acabem de descarregar a la carpeta `/var/www/html/moodle`. (nota, cal tenir el paquet zip instal·lat) 

![image](https://user-images.githubusercontent.com/114423065/203132543-8e7c6a23-8ed3-4563-bb46-5ae6b9ef96b5.png)

![image](https://user-images.githubusercontent.com/114423065/203132694-747b81d0-6747-4681-9cb8-9dd66264f8a6.png)

Ara canviarém els propietaris de la carpeta moodle que hem descomprimit, tant el grup com l'usuari

![1](https://user-images.githubusercontent.com/114423065/204079242-17233f84-f1e7-4381-bbd5-d938391854f6.png)

## Crar directoris de fitxers
Ara crearém la carpeta que contindrà les dades d'usuari a la home i li canviarém el grup i usuari propietari:

![image](https://user-images.githubusercontent.com/114423065/204079280-db593123-41d1-4dd7-915d-0e65549b50d3.png)


## Configuració de la base de dades

Accedirém a la consola de configuració de la base de dades com a root:

![image](https://user-images.githubusercontent.com/114423065/204079400-a5d0ce92-7046-4fee-9588-dd1a04e3c21c.png)

Crearém l'usuari amb la seva contrasenya per a moodle:

![image](https://user-images.githubusercontent.com/114423065/204079420-a483da59-cf77-4d0b-9b0a-152a0a545b55.png)

Crearém la base de dades de moodle

![image](https://user-images.githubusercontent.com/114423065/204079458-5cd99b2d-af9d-4991-bb91-584932077545.png)

I li donarém control a la base a l'usuari que hem creat anteriorment

![image](https://user-images.githubusercontent.com/114423065/204079475-660606c9-0721-49b1-a157-4a782efd6294.png)

I sortirem de la consola

![image](https://user-images.githubusercontent.com/114423065/204079509-16d4e013-f6be-44e4-a670-55a6c74bcd60.png)


## Configuració de Moodle

Per començar a configurara moodle necessitarém entrar a la ip de la màquina seguit de `/moodle/moodle/install.php`

![image](https://user-images.githubusercontent.com/114423065/204079565-8906baa1-c462-4216-82ad-9d0ed5f379d8.png)

Sel·leccionarém l'idioma:

![image](https://user-images.githubusercontent.com/114423065/204079591-976ad32c-d017-4d51-b5e0-186b17139429.png)


Comprovarém quines extensions ens fan falta

![image](https://user-images.githubusercontent.com/114423065/204079609-7682ccf5-17c7-4029-9a07-93936597270d.png)

Instal·larém cURL i zip

![image](https://user-images.githubusercontent.com/114423065/204079726-d675c06e-fb7e-4a48-b69c-9e90bad17b99.png)

Després reiniciarém el servei apache2, i ja no auria de sortir el missatge d'avís

I configurarém la ruta del directori de dades amb la carpeta que hem creat anteriorment

![image](https://user-images.githubusercontent.com/114423065/204079807-44e1a531-d479-4a7c-99cb-5dad65f6d88c.png)

Sel·leccionarém el servidor de base de dades

![image](https://user-images.githubusercontent.com/114423065/204079886-a444c302-b5bd-4eef-88ab-f4b8bbca4a5c.png)

I li donarém l'informació necessaria

![image](https://user-images.githubusercontent.com/114423065/204079902-5fb56c6f-51ef-4cc3-b007-b615bab443bc.png)

#### Un error amb l'informació de login
Un problema que he tingut ha sigut el següent, m'he equivocat amb la contrasenya de la base de dades al introduïrla a moodle i sortia aquest error:

![image](https://user-images.githubusercontent.com/114423065/204260519-6ba940d3-666f-4294-a332-977c45f52b0a.png)


Una vegada arreglat, m'ha sortit aquest error:

![image](https://user-images.githubusercontent.com/114423065/204326854-35bc80a1-8bd9-4c34-a00f-334dbe8e0da5.png)

L'arreglem instal·lant l'extensió XML de php amb la seva versió corresponent:

![image](https://user-images.githubusercontent.com/114423065/204327672-351c42cd-1cc1-4d2a-b287-dd1b9802af1d.png)

Torna a sortir un altre error de mbstring i l'arreglem instal·lant-lo

![image](https://user-images.githubusercontent.com/114423065/204328379-eef1a243-d194-4f65-99d6-3b54224e450b.png)

![image](https://user-images.githubusercontent.com/114423065/204328214-f0d73a75-c634-482e-bdcb-b69cfbee4bc5.png)

I ja sortirá aquesta pantalla on ja podrém configurar moodle

![image](https://user-images.githubusercontent.com/114423065/204328739-4c062e8b-2bd6-4a6c-9382-caf2bb5c2dae.png)


Ara surt que ens falten les següents extensións

![image](https://user-images.githubusercontent.com/114423065/204329309-51568090-98ae-481b-92fc-2e037bb37dab.png)

![image](https://user-images.githubusercontent.com/114423065/204331036-7d3e2288-706e-4f83-ac79-f213d49a8f5f.png)

I després reiniciarem apache

![image](https://user-images.githubusercontent.com/114423065/204331415-8f88f0ad-1b2c-46db-870c-ac7a6045bed8.png)


Una vegada apache reiniciat i la pàgina recarregada no auriem de tenir més errors de servidor:

![image](https://user-images.githubusercontent.com/114423065/204331505-c6bfcbe5-6402-4da9-8af7-8609c2d53490.png)


Una vegada tinguessim les extensions requerides, a la part de baix de la pàgina, ens sortiràn altres errors:

![image](https://user-images.githubusercontent.com/114423065/204332003-3d319236-6ab7-4e62-8426-eb20ba5547e6.png)

Per sol·lucionar el error max_input_vars editarem el fitxer php.ini d'apache:

![image](https://user-images.githubusercontent.com/114423065/204332473-81ebbf4c-00a2-4530-b846-202f95008b28.png)

Buscarém la línia del max_input_vars i el canviarém al valor que ens demani, també la descomentarém treient el `;` de l'inici de línia

![image](https://user-images.githubusercontent.com/114423065/204333595-f295864a-e709-4639-9c7f-5aa7656c29a7.png)

Després reiniciarém el servei apache2

![image](https://user-images.githubusercontent.com/114423065/204333088-99433aca-c31e-460c-bd63-2a1d46913258.png)

Una vegada fet aixó l'apartat de "other errors" ens auria de sortir buida, o amb errors que ens recomana sol·lucionar i un botó per continuar

![image](https://user-images.githubusercontent.com/114423065/204334263-6977d737-5576-4bb1-bfa8-89597b961068.png)


Una vegada li doném al botó de continuar ens auria de sortir aquesta pantalla:

![image](https://user-images.githubusercontent.com/114423065/204334542-1be73606-8a33-44ce-8816-cca661a7aa60.png)

Una vegada l'instal·lació acabada ens sortirà una pantalla de checks:

![image](https://user-images.githubusercontent.com/114423065/204353904-38788bd9-2df9-4134-bf83-6e88b5551764.png)

### Configuració d'administrador moodle:

Configurarém l'usuari admin:
![image](https://user-images.githubusercontent.com/114423065/204355489-50e098a4-5e9a-4837-ab2a-505e9f2c1581.png)


![image](https://user-images.githubusercontent.com/114423065/204356030-1d8b464c-90c9-4bd1-956c-6d176aceddd9.png)

![image](https://user-images.githubusercontent.com/114423065/204356591-8c16aa55-e5d2-4b94-934d-d74e686c236c.png)


### Creació de categories i cursos:

![image](https://user-images.githubusercontent.com/114423065/204356704-103e40a8-1f24-482c-8695-0565a34c951c.png)

Per crear cursos i categories tenim d'entrar al moodle amb usuari administrador, i anar a l'apartat de "Administración de sitio" després a "Cursos" i a "Administrar cursos y categorias":

![image](https://user-images.githubusercontent.com/114423065/205688251-b009b396-0498-4e3c-b4a8-2f09a18fe9f1.png)

Crearém una nova categoria, la seva categoria pare serà "Superior", repetirem fins tenir totes les categories:

![image](https://user-images.githubusercontent.com/114423065/205690606-17fb2230-80e1-4e03-ba0c-f8817fecb30d.png)

Aquest serà el resultat de categories i sub-categories:

![image](https://user-images.githubusercontent.com/114423065/207098376-8eb7703e-5b98-4444-951d-d1614426ad49.png)


Ara crearém nous cursos:

![image](https://user-images.githubusercontent.com/114423065/205694783-8b24b746-ef91-4f0d-aa44-a6ccc2b1e9a7.png)

Crearém els cursos i repetirém fins a tenir tots els cursos:

![image](https://user-images.githubusercontent.com/114423065/205695239-af8cbc4e-0705-4190-b791-771bf12ce228.png)

Aques és el resultat dels cursos:

![image](https://user-images.githubusercontent.com/114423065/205706935-9906bc9d-9943-479e-9adb-7678346e546d.png)


### Usuaris

Preguntes:

- **Quins tipus d'usuaris (rols diferents) existeixen a Moodle?**

1. Admins
2. Creadors de cursos
3. Professors
4. Estudiants
5. Convidats

- **Quins rols poden assignar cada tipus d'usuaris?**


- **Crea tres usuaris:**

![image](https://user-images.githubusercontent.com/114423065/205710323-6db1684e-a90b-45c8-a5f2-04f6947af965.png)

Un Professor anomenat Cognom_1_profe.

![image](https://user-images.githubusercontent.com/114423065/205710602-0dde70a5-8c43-4624-9791-9dcbffab9ccd.png)


Un Professor anomenat Cognom_2_profe.

![image](https://user-images.githubusercontent.com/114423065/205710809-a390d47e-ebc3-47ff-b078-fc27936c10d4.png)


Un professor No editor anomenat Cognom_3_profe.
![image](https://user-images.githubusercontent.com/114423065/205712579-2c4f2f13-6f68-4c98-ba40-c39463ce0f2f.png)

Després anirém a "Pagina principal" i després a "Participantes" dintre d'aquesta categoria podrém editar els rols de cadascun dels usuaris

![image](https://user-images.githubusercontent.com/114423065/205712515-66954238-e663-402f-b7c0-ef77c5196b7d.png)

![image](https://user-images.githubusercontent.com/114423065/205713232-2062114c-9a31-4c6f-a5d7-93df76e42f31.png)

- **Crea un alumne anomenat Cognom_1_alumne.**

Anirém al llistat d'alumnes i després a "crear nuevo usuario"

![Selecció_031](https://user-images.githubusercontent.com/114423065/207115757-6215c226-472b-4e69-a513-ca3a72dd1047.png)


I després omplirem les dades de l'usuari:

![Selecció_032](https://user-images.githubusercontent.com/114423065/207115834-2796fe8a-7b1b-4e14-b27d-5143f2daeb53.png)


- **Afegeix un fitxer d'usuaris des de fitxer (4 companys/es de classe) simultàniament carregant un fitxer de dades, com es veu a la imatge.**

Crearém l'arxiu amb l'informació requerida:

![image](https://user-images.githubusercontent.com/114423065/207119995-a8793cfe-2d16-423c-9309-baadea48aca7.png)

Penjarém el fitxer:

![image](https://user-images.githubusercontent.com/114423065/207118160-24c4dad8-fa34-4c41-a35b-91088932c218.png)


I aquesta és la pantalla de comprovació de dades

![image](https://user-images.githubusercontent.com/114423065/207120313-72ba4782-5b7b-439d-a503-6374de701ae4.png)

Aquesta és la següent pantalla, ens hem de fixar si ens dona cap error:

![image](https://user-images.githubusercontent.com/114423065/207120788-19076f26-1aa5-41dd-860a-88a2faeee1ac.png)


Revisant la llista d'usuaris podem veure si s'han afegit:

![image](https://user-images.githubusercontent.com/114423065/207120973-25311458-ce2f-4aa7-a856-3791e6db478c.png)

- **Fes que Cognom_1_profe sigui professor dels cursos: MP04, MP12, MP08 i MP07.**

Anirém a la configuració del curs i després a matricular usuarios:

![image](https://user-images.githubusercontent.com/114423065/207122014-a41fa983-41cd-485d-aee3-f984024b4d06.png)

Després sel·leccionarém l'usuari i el seu rol:

![image](https://user-images.githubusercontent.com/114423065/207122254-96a0a026-6874-493d-8a47-7413e9546921.png)

![image](https://user-images.githubusercontent.com/114423065/207122428-8636fa5c-2019-407c-a465-540be2756eb3.png)

![image](https://user-images.githubusercontent.com/114423065/207122561-a8429584-c757-4853-b259-e69f476b3f7e.png)


- **Fes que Cognom_2_profe sigui professor dels cursos: MP10, MP06 i TUTORIA.**

![image](https://user-images.githubusercontent.com/114423065/207122831-cb5a7c67-006f-4b48-bcec-4d9c3b628d07.png)

![image](https://user-images.githubusercontent.com/114423065/207122885-1071e2e2-9650-4833-8d47-21ecd8fedee6.png)

![image](https://user-images.githubusercontent.com/114423065/207122948-a563e523-d6f1-4971-8167-efdc5e1ba08b.png)


- **Fes que Cognom_3_profe sigui professor de tots els cursos.**

![image](https://user-images.githubusercontent.com/114423065/207123785-7e9cda95-cf3c-4590-9ead-6aa9c10e9f4e.png)
![image](https://user-images.githubusercontent.com/114423065/207123855-a1204b60-fcae-4345-beb3-12135741eeda.png)
![image](https://user-images.githubusercontent.com/114423065/207123900-994a0870-7fb4-4f52-9e80-f87f5b12259f.png)
![image](https://user-images.githubusercontent.com/114423065/207123957-7d7308d8-6c57-491a-bc13-229b7914029d.png)
![image](https://user-images.githubusercontent.com/114423065/207124013-58f944a7-c0db-4690-b9f3-2b72dbac8f42.png)
![image](https://user-images.githubusercontent.com/114423065/207124116-75856f32-9f4f-4c1e-9918-83aee3157582.png)
![image](https://user-images.githubusercontent.com/114423065/207124228-1e628f5d-2cce-41be-8adc-6dd27989819c.png)



- **Afegeix a tots els alumnes a tots els cursos (els 5).**

- **Mostra l'apartat Participants de cada curs.**

- **Què són les Cohorts?**

Les cohorts són grups a tota l'amplada del lloc o de tota una categoria de cursos. 


- **Perquè serveixen?**

El propòsit de les cohorts és permetre a tots els membres de la cohort ser inscrits (matriculats) fàcilment en un curs. 


- **Què són els grups?**

- **Perquè serveixen?**

- **Fes dos grups de Aplicacions Web, el A i el B. Mostra els dos grups.**
