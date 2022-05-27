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

# **ACTIVITAT 1 -- CONFIGURACIÓ D’UN SISTEMA DE RÈPLICA**
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/configuracio.png)
### **CONFIGURACIO MÁSTER**

**Verifica que el paràmetre server-id té un valor numèric (per defecte és
1).**

Per tal de verificar el verificar que el paràmetre del server-id tingui un valor númeric 1, ens dirigim a la ruta ***/etc/my.cnf***, i seguidament escribim la següent comanda:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image1.png)

**Fes un FLUSH DELS LOGS utilitzant la comanda FLUSH LOGS dins del MySQL**

Per tal de fer un FLUSH dels LOGS a dintre de Mysql fem el següent:

![Interfaz de usuario gráfica, Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image2.png)

**Realitza una comprovació dels logs com a master mitjançant SHOW MASTER LOGS**

Per tal de realitzar una COMPROVACIÓ dels LOGS com a master mitjançant el show master los fem el següent:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image3.png)

### **CONFIGURACIÓ SLAVE i MASTER**

**Realitza una còpia de la màquina virtual a on tinguis SGBD MySQL. Aquesta nova màquina serà que farà d'eslau**

Ens dirigium a les maquines virtuals i clonem la nostra màquina ja que aquesta serà la d'esclau tal com posa l'enunciat que fem (**SLAVE**)



![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image4.png)

**Esbrina quina IP tenen cadascuna de les màquines**

Escrivim ***ipconfig*** i aquesta es la ip que correspon a la màquina del **Master**

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image5.png)

I aquesta a la màquina que correspon a la del **Slave**

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image6.png)

**Crea un backup de la BD a la màquina master utilitzant el mysqldump:**

Utilitzem la seguent comanda per crear l'arxiu .sql  

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image7.png)

Transpasem l'arxiu amb la següent comanda:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image8.png)

Anem al mysql de la màquina del slave

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image9.png)

Creem la base de dades anmomenada sakila
 
![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image65.png)

Utilitzem la base de sakila i executem l'arxiu .sql amb la seguent sentència mysql

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image10.png)

Ara fem un SHOW TABLES per veure si ha fet els canvis. Tal i com es veu ho ha fet!

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image66.png)

**Edita el fitxer master_backup.sql i busca la línia que comenci per
\--CHANGE MASTER TO\.... i busca els valors MASTER_LOG_FILE i
MASTER_LOG_POS.**

Ara anem a la maàquina master i ens dirigim a la ruta on es va fer el dump. A continuació farem el nano de l'arxiu 

![Interfaz de usuario gráfica Descripción generada 
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image11.png)

Una vegada estem a dins del fitxer anem a la linia on ens indiaca la poscicio i el nom del log file.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image12.png)

#### **SLAVE**

**Para el servei de MySQL.**

Per tal de parar el servei de mysql de la màquina slave tan sols hem de fer el **STOP** en el systemctl

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image13.png)

**Modifica el fitxer de configuració /etc/my.conf**

Una vegada fet el previ, ens redirigim a ***/etc/my.cnf***, posem el id del server del slave i desmarquem la linia per aixi tenir el binlog desactivat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image14.png)

**Torna engegar el servei MySQL.**

Per tal de engegar el servei de mysql de la màquina slave tan sols hem de fer el **RESTART** en el systemctl

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image15.png)

#### **MASTER**

**Afegeix l\'usuari slave amb la IP de la màquina slave**

Per tal de crear l'usuari SLAVE fem el següent:

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image16.png)

**Afegix el permís de REPLICATION SLAVE a l\'usuari que acabes de crear.**

Li donem els permisos de replicació al SLAVE amb la comanda qu mostrem:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image17.png)

Ara fem un alter al usuari slave creat i li posem que la contaseña sigui nativa ja que el mysql 8.0 ja te per defecte la securització activada

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image18.png)

Fem un FLUSH PRIVILEGES

![](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image19.png)

**A la màquina SLAVE executa la següent comanda ajudant-te de les dades
del pas 3 i 4:**

Fem un change master to, i posem totes les dades de la màquina slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image20.png)

Iniciem el slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image21.png)

Ara veurem el status del slave amb la següent sentència mysql. Tal i com es veu està operatiu i funciona correctament

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image67.png)

Aixi es veu en el slave la base de dades creada

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image22.png)

Ara li introduim nos valors en el salave per que repliqui en el slave

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image23.png)

Mirem al slave si se ha replicat , i com es veu en la captura esta
replicat

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/ReplicaBackup/blob/main/imagenes/image24.png)
