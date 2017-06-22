## <a name="prerequisites"></a>Prerequisiti

Prima di creare il gruppo di disponibilità, è necessario:

- Impostare l'ambiente in modo che possano comunicare tutti i server che ospiteranno le repliche di disponibilità
- Installare SQL Server

>[!NOTE]
>In Linux, è necessario creare un gruppo di disponibilità prima di aggiungerlo come risorsa cluster da gestire con il cluster. Questo documento viene fornito un esempio che crea il gruppo di disponibilità. Per la distribuzione istruzioni specifiche per creare il cluster e aggiungere il gruppo di disponibilità come risorsa cluster, vedere i collegamenti in [passaggi successivi](#next-steps).

1. **Aggiornare il nome del computer per ogni host**

   Ogni nome di SQL Server deve essere:
   
   - 15 caratteri o meno
   - Univoco all'interno della rete
   
   Per impostare il nome del computer, modificare `/etc/hostname`. Lo script seguente consente di modificare `/etc/hostname` con `vi`.

   ```bash
   sudo vi /etc/hostname
   ```

1. **Configurare il file hosts**

>[!NOTE]
>Se i nomi host sono registrati con i relativi IP nel server DNS, non è necessario eseguire la procedura seguente. Verificare che tutti i nodi che sono faranno parte della configurazione del gruppo di disponibilità possono comunicare tra loro (esecuzione del ping il nome host deve rispondere con l'indirizzo IP corrispondente). Inoltre, assicurarsi che il file /etc/hosts non contiene un record che esegue il mapping di indirizzi IP di localhost 127.0.0.1 con il nome host del nodo.


   Il file hosts in ogni server contiene gli indirizzi IP e nomi di tutti i server che farà parte del gruppo di disponibilità. 

   Il comando seguente restituisce l'indirizzo IP del server corrente:

   ```bash
   sudo ip addr show
   ```

   Aggiornamento `/etc/hosts`. Lo script seguente consente di modificare `/etc/hosts` con `vi`.

   ```bash
   sudo vi /etc/hosts
   ```

   Nell'esempio seguente `/etc/hosts` su **node1** con le aggiunte per **node1** e **node2**. In questo documento **node1** fa riferimento alla replica primaria di SQL Server. **NODE2** fa riferimento a SQL Server secondario.;


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 node1
   10.128.16.77 node2
   ```

### <a name="install-sql-server"></a>Installare SQL Server

Installare SQL Server. I collegamenti seguenti puntano alle istruzioni di installazione di SQL Server per distribuzioni diverse. 

- [Red Hat Enterprise Linux](..\linux\sql-server-linux-setup-red-hat.md)

- [SUSE Linux Enterprise Server](..\linux\sql-server-linux-setup-suse-linux-enterprise-server.md)

- [Ubuntu](..\linux\sql-server-linux-setup-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Abilitare gruppi di disponibilità Always On e riavviare SQL Server

Abilitare sempre in gruppi di disponibilità in ogni nodo che ospita il servizio SQL Server, quindi riavviare `mssql-server`.  Eseguire lo script riportato di seguito:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>Abilitare la sessione di eventi AlwaysOn_health 

È possibile abilitare optionaly gruppi di disponibilità AlwaysOn specifici eventi estesi per facilitare la diagnosi della causa principale durante la risoluzione di un gruppo di disponibilità.

```Transact-SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Per ulteriori informazioni sulla sessione XE, vedere [sempre in eventi estesi](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-db-mirroring-endpoint-user"></a>Creare l'utente dell'endpoint di mirroring del database

Lo script di Transact-SQL seguente crea un account di accesso denominato `dbm_login`e un utente denominato `dbm_user`. Aggiornare lo script con una password complessa. Eseguire il comando seguente in tutti i server SQL per creare l'utente dell'endpoint di mirroring del database.

```Transact-SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Creare un certificato

Il servizio SQL Server in Linux Usa certificati per autenticare le comunicazioni tra gli endpoint del mirroring. 

Lo script Transact-SQL seguente crea una chiave master e certificato. Quindi eseguito il backup del certificato e consente di proteggere il file con una chiave privata. Aggiornare lo script con una password complessa. Connettersi al Server SQL primario ed eseguire Transact-SQL seguente per creare il certificato:

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

A questo punto la replica di SQL Server primaria dispone di un certificato in `/var/opt/mssql/data/dbm_certificate.cer` un at chiave privata e `var/opt/mssql/data/dbm_certificate.pvk`. Copiare questi due file nello stesso percorso in tutti i server che ospiterà le repliche di disponibilità. Usare l'utente mssql o concedere l'autorizzazione all'utente mssql per accedere a tali file. 

Nel server di origine, ad esempio il comando seguente copia i file nel computer di destinazione. Sostituire il  **<node2>**  valori con i nomi delle istanze di SQL Server che ospiteranno le repliche. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

Nel server di destinazione, assegnare l'autorizzazione per accedere al certificato utente mssql.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Creare il certificato nel server secondario

Lo script Transact-SQL seguente crea una chiave master e certificato da backup creati nella replica primaria di SQL Server. Inoltre, il comando autorizza l'utente per accedere al certificato. Aggiornare lo script con una password complessa. La password di decrittografia è la stessa password utilizzata per creare il file PVK in un passaggio precedente. Eseguire lo script seguente in tutti i server secondari per creare il certificato.

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>Creare endpoint in tutte le repliche di mirroring del database

Gli endpoint del mirroring del database utilizzano il protocollo TCP (Transmission Control Protocol) per inviare e ricevere messaggi tra istanze del server che fanno parte di sessioni di mirroring del database o ospitano repliche di disponibilità. L'endpoint del mirroring del database è in attesa su un numero di porta TCP univoco. 

L'istruzione Transact-SQL seguente crea un endpoint di ascolto denominato `Hadr_endpoint` per il gruppo di disponibilità. Avviare l'endpoint e dell'autorizzazione di connessione consente all'utente che ha creato. Prima di eseguire lo script, sostituire i valori compresi tra `**< ... >**`.


>[!NOTE]
>Per questa versione, non utilizzare un indirizzo IP diverso per l'indirizzo IP del listener. Stiamo lavorando su una correzione per questo problema, ma l'unico valore accettabile per il momento è '0.0.0.0'.

Aggiornare il codice Transact-SQL per l'ambiente in tutte le istanze di SQL Server: 

```Transact-SQL
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

>[!IMPORTANT]
>La porta TCP sul firewall deve essere aperta per la porta del listener.

Per ulteriori informazioni, vedere [l'Endpoint del Mirroring Database (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
