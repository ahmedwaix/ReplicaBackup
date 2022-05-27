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

# **ACTIVITAT 5 -- EINES PERCONA TOOLKIT**
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/toolkit.png)

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
