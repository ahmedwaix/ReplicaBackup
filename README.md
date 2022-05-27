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

# **[ÍNDEX]**
CONFIGURACIO MÁSTER

Verifica que el paràmetre server-id té un valor numèric (per defecte és
1). ![Texto Descripción generada
automáticamente](./images/media/image1.png){width="5.905555555555556in"
height="2.536111111111111in"}

• Fes un FLUSH DELS LOGS utilitzant la comanda FLUSH LOGS dins del MySQL

![Interfaz de usuario gráfica, Texto Descripción generada
automáticamente](./images/media/image2.png){width="3.3541666666666665in"
height="0.8020833333333334in"}

• Realitza una comprovació dels logs com a master mitjançant SHOW MASTER
LOGS

![Texto Descripción generada
automáticamente](./images/media/image3.png){width="4.020833333333333in"
height="1.6458333333333333in"}

CONFIGURACIÓ SLAVE i MASTER

Realitza una còpia de la màquina virtual a on tinguis SGBD MySQL.
Aquesta nova màquina serà que farà d\'eslau

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada
automáticamente](./images/media/image4.png){width="3.3333333333333335in"
height="1.2083333333333333in"}

• Esbrina quina IP tenen cadascuna de les màquines (master, slave).

![Texto Descripción generada
automáticamente](./images/media/image5.png){width="5.905555555555556in"
height="1.1965277777777779in"}

![Texto Descripción generada
automáticamente](./images/media/image6.png){width="5.905555555555556in"
height="1.4131944444444444in"}

Crea un backup de la BD a la màquina master utilitzant:

![](./images/media/image7.png){width="6.628144138232721in"
height="0.6172965879265092in"}

Transpasem el archiu

![Texto Descripción generada
automáticamente](./images/media/image8.png){width="5.905555555555556in"
height="1.1166666666666667in"}

![](./images/media/image9.png){width="3.3958333333333335in"
height="0.28125in"}

![](./images/media/image10.png){width="3.1770833333333335in"
height="0.40625in"}

Edita el fitxer master_backup.sql i busca la línia que comenci per
\--CHANGE MASTER TO\.... i busca els valors MASTER_LOG_FILE i
MASTER_LOG_POS.

![Interfaz de usuario gráfica Descripción generada
automáticamente](./images/media/image11.png){width="3.9895833333333335in"
height="0.875in"}

![Texto Descripción generada
automáticamente](./images/media/image12.png){width="5.905555555555556in"
height="1.3805555555555555in"}

[SLAVE]{.underline}

Para el servei de MySQL.

![](./images/media/image13.png){width="3.5208333333333335in"
height="0.19791666666666666in"}

Modifica el fitxer de configuració /etc/my.conf

![Texto Descripción generada
automáticamente](./images/media/image14.png){width="3.5in"
height="4.520833333333333in"}

Torna engegar el servei MySQL.

![](./images/media/image15.png){width="2.3020833333333335in"
height="0.3541666666666667in"}

[MASTER]{.underline}

Afegeix l\'usuari slave amb la IP de la màquina slave

![](./images/media/image16.png){width="5.905555555555556in"
height="0.7083333333333334in"}

Afegix el permís de REPLICATION SLAVE a l\'usuari que acabes de crear.

![Texto Descripción generada
automáticamente](./images/media/image17.png){width="3.3958333333333335in"
height="0.9895833333333334in"}

![Texto Descripción generada
automáticamente](./images/media/image18.png){width="5.1875in"
height="0.59375in"}

![](./images/media/image19.png){width="3.2083333333333335in"
height="0.4479166666666667in"}

• A la màquina SLAVE executa la següent comanda ajudant-te de les dades
del pas 3 i 4:

![Texto Descripción generada
automáticamente](./images/media/image20.png){width="4.28125in"
height="1.5625in"}

![Texto Descripción generada
automáticamente](./images/media/image21.png){width="4.15625in"
height="0.7604166666666666in"}

Aixi es veu en el slave la base de dades creada

![Texto Descripción generada
automáticamente](./images/media/image22.png){width="3.1145833333333335in"
height="2.0520833333333335in"}

Ara li introduuim nos valors en el salave per que repliqui en el slave

![Texto Descripción generada
automáticamente](./images/media/image23.png){width="4.0in"
height="0.53125in"}

Mirem al slave si se ha replicat , i com es veu en la captura esta
replicat

![Texto Descripción generada
automáticamente](./images/media/image24.png){width="3.3645833333333335in"
height="1.8229166666666667in"}

ACTIVITAT 5 -- EINES PERCONA TOOLKIT

Primer instalem el toolkit amb aquesta comanda al Master

![Texto Descripción generada
automáticamente](./images/media/image25.png){width="4.083333333333333in"
height="4.708333333333333in"}

Una vegada ja tenim instalat el toolkit creearem una base de dades i la
iniciarem i despres crearem una taula

![Texto Descripción generada
automáticamente](./images/media/image26.png){width="5.5625in"
height="1.3958333333333333in"}

Ara li insertarem valors a dins de la taula

![Texto Descripción generada
automáticamente](./images/media/image27.png){width="5.072916666666667in"
height="0.6666666666666666in"}

Ara com ja tenim creat una estructura anem al slave a veure que esta
replicat. I com es veu esta replicat

![Texto Descripción generada
automáticamente](./images/media/image28.png){width="2.46875in"
height="1.7083333333333333in"}

Ara farem una inconsistencia de dades, En el slave borrem un registre de
la taula sri

![](./images/media/image29.png){width="3.0625in"
height="0.5104166666666666in"}

I com es veu esta borrat

![Texto Descripción generada
automáticamente](./images/media/image30.png){width="2.8645833333333335in"
height="1.5in"}

Ara farem un update en el id 2 en el master

![Texto Descripción generada
automáticamente](./images/media/image31.png){width="3.5520833333333335in"
height="0.90625in"}

Com es veu se ha cambiat

![Texto Descripción generada
automáticamente](./images/media/image32.png){width="2.4166666666666665in"
height="1.6041666666666667in"}

Fem un SHOW SLAVE STATUS en el slave i veurem que surt un error per la
inconsistencia de dades

![Texto Descripción generada
automáticamente](./images/media/image33.png){width="5.905555555555556in"
height="2.747916666666667in"}

Farem la seguent sentencia msql per saltar el problema

![Texto Descripción generada
automáticamente](./images/media/image34.png){width="5.822916666666667in"
height="1.2083333333333333in"}

Anem un altre cop al show slave status I veiem que ya no esta el error
momentaniment i tenim una inconsistencia

![Texto Descripción generada
automáticamente](./images/media/image35.png){width="5.905555555555556in"
height="5.125694444444444in"}

Una vegada fet aixo en el master creem una base de dades

![Texto Descripción generada
automáticamente](./images/media/image36.png){width="3.4166666666666665in"
height="0.625in"}

Creem una taula dsns en el que guardarem la ip del slave

![Texto Descripción generada
automáticamente](./images/media/image37.png){width="4.21875in"
height="1.2395833333333333in"}

Introduiim dades amb el insert a la taula dsns i aixi que da al
visualizar-ho

![Texto Descripción generada
automáticamente](./images/media/image38.png){width="6.75in"
height="1.8229166666666667in"}

Ja que esta tot configurat per utilizar les eines primer utilitzem la
primera eina que serveix per detectar inconsistencias entre el master i
el salve per fer-ho hem de utilizar las seguent comanda
pt-table-checksum amb els seus paramentres corresponents I com veiem hi
ha inconsistencia en la taula on posa DIFFS ens diu el numero de
inconsistencias que hi ha

![Texto Descripción generada
automáticamente](./images/media/image39.png){width="6.8017246281714785in"
height="1.1173578302712162in"}

En el paramentre de la replica ens ha creat una taula el checksum i com
es veu la Esquerra que es el master on pose this cnt hi ha un 3 y en el
salave un 2 aixo vol dir que el master conta 3 rows metres que el slave
conta 2 rows.

![Texto Descripción generada
automáticamente](./images/media/image40.png){width="7.207502187226597in"
height="2.2985356517935256in"}

Ara que ja hem detectat la inconsistencia amb la seguent eina que es el
pt-table-sync la ultilitzarem per sycronitzar les dades .Per fer-ho hem
de utiltzar aquesta comanda amb els seus paramentres en aquest cas
utilitzarem el print per veure els canvis que fara

![](./images/media/image41.png){width="7.063403324584427in"
height="0.9925371828521434in"}

Ara que ja seabe els cambis que fara executem un altre vegada pero en
lloc de posar print posarem exexute per fer la sycronitsacio. Com es veu
fara un replace en la taula del slave

![](./images/media/image42.png){width="7.268055555555556in"
height="0.7993055555555556in"}

Ara veiem en el mysql la taula sri en el master. Com es veu esta com
abans

![Texto Descripción generada
automáticamente](./images/media/image43.png){width="3.125in"
height="1.9375in"}

Ara anem al slave a veure si la taula sri s' ha modificat i aixi elimina
la inconsistencia. Com es veu en la captura en el slave s' ha
syncronitzat les dades que tenia el master.

![Texto Descripción generada
automáticamente](./images/media/image44.png){width="2.4791666666666665in"
height="1.625in"}

ACTIVITAT 6 -- BACKUP

Primer el que farem es descargar el paquet de xtrabackup

![Texto Descripción generada
automáticamente](./images/media/image45.png){width="7.268055555555556in"
height="1.3444444444444446in"}

Ara extraiem el tar i hauran 4 rpm

![](./images/media/image46.png){width="7.268055555555556in"
height="0.26458333333333334in"}

![Texto Descripción generada
automáticamente](./images/media/image47.png){width="7.268055555555556in"
height="1.2708333333333333in"}

i instal·lem el paquet marcat en la captura anterior

![Texto Descripción generada
automáticamente](./images/media/image48.png){width="7.268055555555556in"
height="1.9256944444444444in"}

Ara que ja tenim el xtrabackup instalat anem al mysql i creem un usuari
backup

![](./images/media/image49.png){width="5.239583333333333in"
height="0.4895833333333333in"}

Li donarem permissos al usuari backup

![](./images/media/image50.png){width="7.268055555555556in"
height="0.41388888888888886in"}

Una vegada fet aixo surtim de l mysql i creem la carpeta per guardar el
backup

![](./images/media/image51.png){width="3.6458333333333335in"
height="0.22916666666666666in"}

Ara que ja esta creada la carpeta fem la seguent comanda amb els
parametres seguents per crear un full backup de la maquina.

![Texto Descripción generada
automáticamente](./images/media/image52.png){width="7.268055555555556in"
height="1.8208333333333333in"}

Una vegada ja creada anem a la carpeta tmp

![](./images/media/image53.png){width="2.5208333333333335in"
height="0.3541666666666667in"}

Ara a la carpeta on esta el backup creat amb tota la informacio de la
maquina

![Interfaz de usuario gráfica Descripción generada automáticamente con
confianza media](./images/media/image54.png){width="7.268055555555556in"
height="0.8013888888888889in"}

Ara farem la restauracio per que es veigi que funciona primer pararem el
mysql

![](./images/media/image55.png){width="3.6145833333333335in"
height="0.17708333333333334in"}

Anirem al directori de dades de mysql

![Texto Descripción generada
automáticamente](./images/media/image56.png){width="7.268055555555556in"
height="1.4368055555555554in"}

Ara eliminarem el contingut, i com es veu esta buit

![Imagen de la pantalla de un video juego Descripción generada
automáticamente con confianza
baja](./images/media/image57.png){width="2.9791666666666665in"
height="0.5208333333333334in"}

Ara per fer una bona restauracio primer fem el prepare per veure quins
canvis fara a la maquina

![Texto Descripción generada automáticamente con confianza
baja](./images/media/image58.png){width="7.268055555555556in"
height="1.8173611111111112in"}

Una vegada fet el prepare anirem on es guarda el backup i veure que ha
creat dos fitxers que serán els que se executaran per fer el restore

![Texto Descripción generada
automáticamente](./images/media/image59.png){width="7.268055555555556in"
height="1.5583333333333333in"}

Ara que ja tenim consistencia per fer un restore utilitzem la seguent
comanda per realizar la restauracio de la maquina

![Texto Descripción generada automáticamente con confianza
media](./images/media/image60.png){width="7.268055555555556in"
height="2.6444444444444444in"}

Una vegada ja esta feta la restauracio anem al directori de dades de
mysql on estaba eliminada i veiem que esta totalment restaurada com
abans

![](./images/media/image61.png){width="7.268055555555556in"
height="0.7798611111111111in"}

Ara li donem el permis a la ruta al mysql per no fer el secure
installation

![](./images/media/image62.png){width="5.229166666666667in"
height="0.3541666666666667in"}

Iniciem el servei de mysql

![](./images/media/image63.png){width="3.7916666666666665in"
height="0.4479166666666667in"}

Entrem al mysql fem un show databases per veure si están totes les bases
i com es veu están totes.

![Texto Descripción generada
automáticamente](./images/media/image64.png){width="6.84375in"
height="4.885416666666667in"}
