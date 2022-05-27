# ReplicaBackup
**CFGS Administració de Sistemes Informàtics a la Xarxa**

**Mòdul 10:** Administració de sistemes gestors de base de dades (ASIX)

**UF 3:** Llenguatges SQL: DCL i extensió procedimental SGBD corporatiu


***


**Activitat 4 - Rèplica i Backup**


***

**Gaurav Pal**

**Ahmed Belhadi**

**ASIX**

**27/05/2022**
***


#**CONFIGURACIO MÁSTER**

Verifica que el paràmetre server-id té un valor numèric (per defecte és
1). ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image1.png)

• Fes un FLUSH DELS LOGS utilitzant la comanda FLUSH LOGS dins del MySQL

![Interfaz de usuario gráfica, Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image2.png)

• Realitza una comprovació dels logs com a master mitjançant SHOW MASTER
LOGS

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image3.png)

CONFIGURACIÓ SLAVE i MASTER

Realitza una còpia de la màquina virtual a on tinguis SGBD MySQL.
Aquesta nova màquina serà que farà d\'eslau

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image4.png)

• Esbrina quina IP tenen cadascuna de les màquines (master, slave).

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image5.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image6.png)

Crea un backup de la BD a la màquina master utilitzant:

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image7.png)

Transpasem el archiu

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image8.png)

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image9.png)

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image10.png)

Edita el fitxer master_backup.sql i busca la línia que comenci per
\--CHANGE MASTER TO\.... i busca els valors MASTER_LOG_FILE i
MASTER_LOG_POS.

![Interfaz de usuario gráfica Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image11.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image12.png)

[SLAVE]{.underline}

Para el servei de MySQL.

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image13.png)

Modifica el fitxer de configuració /etc/my.conf

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image14.png)

Torna engegar el servei MySQL.

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image15.png)

[MASTER]{.underline}

Afegeix l\'usuari slave amb la IP de la màquina slave

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image16.png)

Afegix el permís de REPLICATION SLAVE a l\'usuari que acabes de crear.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image17.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image18.png)

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image19.png)

• A la màquina SLAVE executa la següent comanda ajudant-te de les dades
del pas 3 i 4:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image20.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image21.png)

Aixi es veu en el slave la base de dades creada

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image22.png)

Ara li introduuim nos valors en el salave per que repliqui en el slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image23.png)

Mirem al slave si se ha replicat , i com es veu en la captura esta
replicat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image24.png)

ACTIVITAT 5 -- EINES PERCONA TOOLKIT

Primer instalem el toolkit amb aquesta comanda al Master

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image25.png)

Una vegada ja tenim instalat el toolkit creearem una base de dades i la
iniciarem i despres crearem una taula

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image26.png)

Ara li insertarem valors a dins de la taula

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image27.png)

Ara com ja tenim creat una estructura anem al slave a veure que esta
replicat. I com es veu esta replicat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image28.png)

Ara farem una inconsistencia de dades, En el slave borrem un registre de
la taula sri

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image29.png)

I com es veu esta borrat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image30.png)

Ara farem un update en el id 2 en el master

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image31.png)

Com es veu se ha cambiat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image32.png)

Fem un SHOW SLAVE STATUS en el slave i veurem que surt un error per la
inconsistencia de dades

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image33.png)

Farem la seguent sentencia msql per saltar el problema

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image34.png)

Anem un altre cop al show slave status I veiem que ya no esta el error
momentaniment i tenim una inconsistencia

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image35.png)

Una vegada fet aixo en el master creem una base de dades

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image36.png)

Creem una taula dsns en el que guardarem la ip del slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image37.png)

Introduiim dades amb el insert a la taula dsns i aixi que da al
visualizar-ho

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image38.png)

Ja que esta tot configurat per utilizar les eines primer utilitzem la
primera eina que serveix per detectar inconsistencias entre el master i
el salve per fer-ho hem de utilizar las seguent comanda
pt-table-checksum amb els seus paramentres corresponents I com veiem hi
ha inconsistencia en la taula on posa DIFFS ens diu el numero de
inconsistencias que hi ha

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image39.png)

En el paramentre de la replica ens ha creat una taula el checksum i com
es veu la Esquerra que es el master on pose this cnt hi ha un 3 y en el
salave un 2 aixo vol dir que el master conta 3 rows metres que el slave
conta 2 rows.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image40.png)

Ara que ja hem detectat la inconsistencia amb la seguent eina que es el
pt-table-sync la ultilitzarem per sycronitzar les dades .Per fer-ho hem
de utiltzar aquesta comanda amb els seus paramentres en aquest cas
utilitzarem el print per veure els canvis que fara

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image41.png)

Ara que ja seabe els cambis que fara executem un altre vegada pero en
lloc de posar print posarem exexute per fer la sycronitsacio. Com es veu
fara un replace en la taula del slave

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image42.png)

Ara veiem en el mysql la taula sri en el master. Com es veu esta com
abans

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image43.png)

Ara anem al slave a veure si la taula sri s' ha modificat i aixi elimina
la inconsistencia. Com es veu en la captura en el slave s' ha
syncronitzat les dades que tenia el master.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image44.png)

ACTIVITAT 6 -- BACKUP

Primer el que farem es descargar el paquet de xtrabackup

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image45.png)

Ara extraiem el tar i hauran 4 rpm

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image46.png)

![Texto Descripción generada
automáticamente]([./images/media](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes)/image47.png)

i instal·lem el paquet marcat en la captura anterior

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image48.png)

Ara que ja tenim el xtrabackup instalat anem al mysql i creem un usuari
backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image49.png)

Li donarem permissos al usuari backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image50.png)

Una vegada fet aixo surtim de l mysql i creem la carpeta per guardar el
backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image51.png)

Ara que ja esta creada la carpeta fem la seguent comanda amb els
parametres seguents per crear un full backup de la maquina.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image52.png)

Una vegada ja creada anem a la carpeta tmp

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image53.png)

Ara a la carpeta on esta el backup creat amb tota la informacio de la
maquina

![Interfaz de usuario gráfica Descripción generada automáticamente con
confianza media](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image54.png)

Ara farem la restauracio per que es veigi que funciona primer pararem el
mysql

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image55.png)

Anirem al directori de dades de mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image56.png)

Ara eliminarem el contingut, i com es veu esta buit

![Imagen de la pantalla de un video juego Descripción generada
automáticamente con confianza
baja](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image57.png)

Ara per fer una bona restauracio primer fem el prepare per veure quins
canvis fara a la maquina

![Texto Descripción generada automáticamente con confianza
baja](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image58.png)

Una vegada fet el prepare anirem on es guarda el backup i veure que ha
creat dos fitxers que serán els que se executaran per fer el restore

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image59.png)

Ara que ja tenim consistencia per fer un restore utilitzem la seguent
comanda per realizar la restauracio de la maquina

![Texto Descripción generada automáticamente con confianza
media](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image60.png)

Una vegada ja esta feta la restauracio anem al directori de dades de
mysql on estaba eliminada i veiem que esta totalment restaurada com
abans

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image61.png)

Ara li donem el permis a la ruta al mysql per no fer el secure
installation

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image62.png)

Iniciem el servei de mysql

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image63.png)

Entrem al mysql fem un show databases per veure si están totes les bases
i com es veu están totes.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image64.png)
