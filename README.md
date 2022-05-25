# ReplicaBackup
**CFGS Administració de Sistemes Informàtics a la Xarxa**

**Mòdul 10:** Administració de sistemes gestors de base de dades (ASIX)

**UF 3:** Llenguatges SQL: DCL i extensió procedimental SGBD corporatiu


***


**Activitat 3: Replica Backup**


***

**Gaurav Pal**

**Ahmed Belhadi**

**ASIX**

**26/05/2022**
***

# **[ÍNDEX]**
CONFIGURACIO MÁSTER

Verifica que el paràmetre server-id té un valor numèric (per defecte és
1). ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image1.png)

• Fes un FLUSH DELS LOGS utilitzant la comanda FLUSH LOGS dins del MySQL

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image2.png)

• Realitza una comprovació dels logs com a master mitjançant SHOW MASTER
LOGS

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image3.png)

CONFIGURACIÓ SLAVE i MASTER

Realitza una còpia de la màquina virtual a on tinguis SGBD MySQL.
Aquesta nova màquina serà que farà d\'eslau

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image4.png)

• Esbrina quina IP tenen cadascuna de les màquines (master, slave).

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image5.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image6.png)

Crea un backup de la BD a la màquina master utilitzant:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image7.png)

Transpasem el archiu

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image8.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image9.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image10.png)

Edita el fitxer master_backup.sql i busca la línia que comenci per
\--CHANGE MASTER TO\.... i busca els valors MASTER_LOG_FILE i
MASTER_LOG_POS.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image11.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image12.png)

[SLAVE]{.underline}

Para el servei de MySQL.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image13.png)

Modifica el fitxer de configuració /etc/my.conf

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image14.png)

Torna engegar el servei MySQL.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image15.png)

[MASTER]{.underline}

Afegeix l\'usuari slave amb la IP de la màquina slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image15.png)

Afegix el permís de REPLICATION SLAVE a l\'usuari que acabes de crear.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image17.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image18.png)

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image19.png)

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

◦ pt-table-checksum:
