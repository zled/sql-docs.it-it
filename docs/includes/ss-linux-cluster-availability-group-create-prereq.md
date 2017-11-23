## <a name="prerequisites"></a>Prerequisiti

Prima di creare il gruppo di disponibilità, è necessario:

- Impostare l'ambiente in modo che tutti i server che ospiteranno le repliche di disponibilità possano comunicare
- Installare SQL Server

>[!NOTE]
>In Linux, è necessario creare un gruppo di disponibilità prima di aggiungerlo come risorsa cluster, da gestire con il cluster. Questo documento propone un esempio di creazione del gruppo di disponibilità. Per istruzioni specifiche sulla distribuzione per creare il cluster e aggiungere il gruppo di disponibilità come risorsa cluster, vedere i collegamenti in [Passaggi successivi](#next-steps).

1. **Aggiornare il nome del computer per ogni host**

   Ogni nome di SQL Server deve:
   
   - avere 15 caratteri o meno
   - essere univoco all'interno della rete
   
   Per impostare il nome del computer, modificare `/etc/hostname`. Lo script seguente consente di modificare `/etc/hostname` con `vi`.

   ```bash
   sudo vi /etc/hostname
   ```

1. **Configurare il file host**

>[!NOTE]
>Se i nomi host sono registrati con i relativi IP nel server DNS, non è necessario eseguire i passaggi seguenti. Verificare che tutti i nodi che faranno parte della configurazione del gruppo di disponibilità possano comunicare tra loro (l'esecuzione del ping del nome host dovrebbe ottenere come risposta l'indirizzo IP corrispondente). Inoltre, assicurarsi che il file /etc/hosts non contenga un record che esegue il mapping dell'indirizzo IP di localhost 127.0.0.1 con il nome host del nodo.


   Il file hosts in ogni server contiene gli indirizzi IP e i nomi di tutti i server che faranno parte del gruppo di disponibilità. 

   Il comando seguente restituisce l'indirizzo IP del server corrente:

   ```bash
   sudo ip addr show
   ```

   Aggiornare `/etc/hosts`. Lo script seguente consente di modificare `/etc/hosts` con `vi`.

   ```bash
   sudo vi /etc/hosts
   ```

   L'esempio seguente illustra `/etc/hosts` su **node1** con aggiunte per **node1**, **node2** e **node3**. In questo documento **node1** si riferisce al server che ospita la replica primaria. **node2** e **node3** si riferiscono ai server che ospitano le repliche secondarie.


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.12 node1
   10.128.16.77 node2
   10.128.15.33 node3
   ```

### <a name="install-sql-server"></a>Installare SQL Server

Installare SQL Server. I collegamenti seguenti puntano alle istruzioni di installazione di SQL Server per varie distribuzioni. 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)

- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)

- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Abilitare la funzionalità Gruppi di disponibilità Always On e riavviare sqlserver

Abilitare i gruppi di disponibilità Always On su ogni nodo che ospita un'istanza di SQL Server e riavviare `mssql-server`.  Eseguire lo script riportato di seguito:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>Abilitare la sessione eventi AlwaysOn_health 

Facoltativamente, è possibile abilitare gli eventi estesi dei gruppi di disponibilità Always On per diagnosticare più facilmente la causa radice durante la risoluzione dei problemi che interessano un gruppo di disponibilità. Eseguire il comando seguente in ogni istanza di SQL Server. 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Per altre informazioni su questa sessione XE, vedere [Eventi estesi di Always On](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-db-mirroring-endpoint-user"></a>Creare l'utente dell'endpoint del mirroring del database

Lo script di Transact-SQL seguente crea un account di accesso denominato `dbm_login`e un utente denominato `dbm_user`. Aggiornare lo script con una password complessa. Eseguire il comando seguente in tutte le istanze di SQL Server per creare l'utente dell'endpoint di mirroring del database.

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Creare un certificato

Il servizio SQL Server in Linux usa i certificati per autenticare la comunicazione tra gli endpoint del mirroring. 

Lo script di Transact-SQL seguente crea una chiave master e un certificato. Quindi esegue il backup del certificato e consente di proteggere il file con una chiave privata. Aggiornare lo script con password complesse. Connettersi all'istanza di SQL Server primaria ed eseguire il Transact-SQL seguente per creare il certificato:

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

A questo punto la replica di SQL Server primaria dispone di un certificato in `/var/opt/mssql/data/dbm_certificate.cer` e di una chiave privata in `var/opt/mssql/data/dbm_certificate.pvk`. Copiare questi due file nello stesso percorso in tutti i server che ospiteranno le repliche di disponibilità. Usare l'utente mssql o concedere l'autorizzazione all'utente mssql per accedere a tali file. 

Nel server di origine, ad esempio, il comando seguente copia i file nel computer di destinazione. Sostituire i valori **<node2>** con i nomi delle istanze di SQL Server che ospiteranno le repliche. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Su ciascun server di destinazione, assegnare l'autorizzazione per accedere al certificato all'utente mssql.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Creare il certificato nei server secondari

Lo script di Transact-SQL seguente crea una chiave master e un certificato dal backup creato nella replica primaria di SQL Server. Inoltre, il comando autorizza l'utente ad accedere al certificato. Aggiornare lo script con password complesse. La password di decrittografia è la stessa password utilizzata per creare il file .pvk in un passaggio precedente. Eseguire lo script seguente in tutti i server secondari per creare il certificato.

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Creare endpoint di mirroring del database in tutte le repliche

Gli endpoint del mirroring del database utilizzano il protocollo TCP (Transmission Control Protocol) per inviare e ricevere messaggi tra istanze del server che fanno parte di sessioni di mirroring del database o ospitano repliche di disponibilità. L'endpoint del mirroring del database è in attesa su un numero di porta TCP univoco. Il listener TCP richiede un indirizzo IP del listener. L'indirizzo IP del listener deve essere un indirizzo IPv4. È inoltre possibile utilizzare `0.0.0.0`. 

Lo script di Transact-SQL seguente crea un endpoint di ascolto denominato `Hadr_endpoint` per il gruppo di disponibilità. Avvia l'endpoint e assegna l'autorizzazione di connessione all'utente creato. Prima di eseguire lo script, sostituire i valori compresi tra `**< ... >**`.

Aggiornare il codice Transact-SQL per l'ambiente in tutte le istanze di SQL Server: 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!NOTE]
>Se si utilizza SQL Server Express Edition in un nodo per ospitare una replica di sola configurazione, l'unico valore valido per il ruolo è `WITNESS`. Eseguire lo script seguente in SQL Server Express Edition.
>```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

The TCP port on the firewall needs to be open for the listener port.



>[!IMPORTANT]
>For SQL Server 2017 release, the only authentication method supported for database mirroring endpoint is `CERTIFICATE`. `WINDOWS` option will be enabled in a future release.

For complete information, see [The Database Mirroring Endpoint (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
