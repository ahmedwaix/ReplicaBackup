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

# **ACTIVITAT 6 -- BACKUP**
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/backup.png)

**Mitjançant l’eina XtraBackup de Percona realitza una còpia completa de la BD i una restauració**

Primer el que farem es descargar el paquet de xtrabackup

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image45.png)

Ara extraiem el tar 

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image46.png)


Com es veu en la captura hi ha 4 rpms

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image47.png)

Instal·lem el paquet marcat en la captura anterior

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image48.png)

Ara que ja tenim el xtrabackup instalat anem al mysql i creem un usuari
backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image49.png)

Li donarem permissos al usuari backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image50.png)

Una vegada fet aixo surtim del mysql i creem la carpeta per guardar el
backup

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image51.png)

Ara que ja esta creada la carpeta fem la seguent comanda amb els
paràmetres següents per crear un full backup de la màquina.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image52.png)

Una vegada ja creada anem a la carpeta ***tmp***.

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image53.png)

Com es veu el backup esta creat amb tota la informació de la
màquina

![Interfaz de usuario gráfica Descripción generada automáticamente con
confianza media](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image54.png)

Ara farem la restauració per que es veigi que funciona. Primer pararem el
mysql

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image55.png)

Anirem al directori de dades de mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image56.png)

Eliminarem el contingut, i com es veu esta buit

![Imagen de la pantalla de un video juego Descripción generada
automáticamente con confianza
baja](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image57.png)

Per fer una bona restauració primer fem el prepare per veure quins
canvis fara a la màquina

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
i tal com es veu están totes.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image64.png)
