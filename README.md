Descrizione Role
=========
Installa il plugin mariadb per l'audit su istanze mysql 5.5 di produzione.
Il playbook posiziona il file server_audit.so per ogni path /opt/mysql/install/mysql<n>/lib/plugin

Introduce una modifica nel file /opt/mysql/install/mysql<n>/my.cnf introducendo le direttive per il funzionamento del plugin.
Carica il plugin a runtime per ogni istanza con il comando:
INSTALL PLUGIN server_audit SONAME 'server_audit.so';

Se la macchina è in ambiente saas (e il controllo viene fatto tramite il nome della macchina), tutte le loggate di syslog del plugin vengono inviate a  saas-log1.saas.priv porta in 518 su protocollo TCP.

Se la macchina non è in ambiente saas, tutte le loggate vengono inviate al file /var/log/audit_mysql.log.
Per questo file deve essere previsto anche una rotazione del file


Requisiti
------------
* Istanza mysql 5.5
* Se una macchina è in ambiente SAAS deve poter raggiungere al ping saas-log1.saas.priv

Variabili
--------------

Dipendenze
------------

Nessuna

Esempio di chiamata
----------------

ansible-playbook /home/playbook/bugs/6581/main.yml

Informazioni Autore
------------------

Martino.Viganò
Martino.Vigano@enghouse.com

![alt text](https://pbs.twimg.com/media/DEjbEx2XsAM-RXu.jpg)
