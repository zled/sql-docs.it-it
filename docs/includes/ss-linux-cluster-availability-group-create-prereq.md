## <a name="prerequisites"></a>Prerequisiti

Prima di creare il gruppo di disponibilità, è necessario:

- Impostare l'ambiente in modo che tutti i server che ospiteranno le repliche di disponibilità possono comunicare.
- Installare SQL Server.

>[!NOTE]
>In Linux, è necessario creare un gruppo di disponibilità prima di aggiungerlo come risorsa cluster da gestire con il cluster. Questo documento propone un esempio di creazione del gruppo di disponibilità. Per le istruzioni di distribuzione specifiche creare il cluster e aggiungere il gruppo di disponibilità come risorsa cluster, vedere i collegamenti nella sezione "passaggi successivi"."

1. Aggiornare il nome del computer per ogni host.

   Ogni nome di SQL Server deve:
   
   - 15 caratteri o meno.
   - Univoco all'interno della rete.
   
   Per impostare il nome del computer, modificare `/etc/hostname`. Lo script seguente consente di modificare `/etc/hostname` con `vi`:

   ```bash
   sudo vi /etc/hostname
   ```

2. Configurare il file hosts.

    >[!NOTE]
    >Se i nomi host sono registrati con i relativi IP nel server DNS, è necessario effettuare i passaggi seguenti. Verificare che tutti i nodi faranno parte della configurazione del gruppo di disponibilità possono comunicare tra loro. (Un ping per il nome host deve rispondere con l'indirizzo IP corrispondente). Inoltre, assicurarsi che il file /etc/hosts non contiene un record che associa l'indirizzo IP localhost 127.0.0.1 con il nome host del nodo.
    >

   Il file hosts in ogni server contiene gli indirizzi IP e i nomi di tutti i server che faranno parte del gruppo di disponibilità. 

   Il comando seguente restituisce l'indirizzo IP del server corrente:

   ```bash
   sudo ip addr show
   ```

   Aggiornare `/etc/hosts`. Lo script seguente consente di modificare `/etc/hosts` con `vi`:

   ```bash
   sudo vi /etc/hosts
   ```

   L'esempio seguente illustra `/etc/hosts` su **node1** con aggiunte per **node1**, **node2** e **node3**. In questo documento, **node1** fa riferimento al server che ospita la replica primaria. E **node2** e **Nodo3** fare riferimento ai server che ospitano le repliche secondarie.

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>Installare SQL Server

Installare SQL Server. I collegamenti seguenti puntano alle istruzioni di installazione di SQL Server per varie distribuzioni: 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>Abilitare gruppi di disponibilità AlwaysOn e riavviare mssql-server

Abilitare gruppi di disponibilità AlwaysOn in ogni nodo che ospita un'istanza di SQL Server. Riavviare quindi `mssql-server`. Eseguire lo script riportato di seguito:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>Abilitare una sessione dell'evento AlwaysOn_health 

Facoltativamente, è possibile abilitare eventi estesi con gruppi di disponibilità AlwaysOn facilitare la diagnosi della causa principale durante la risoluzione di un gruppo di disponibilità. Eseguire il comando seguente in ogni istanza di SQL Server: 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

Per ulteriori informazioni sulla sessione XE, vedere [AlwaysOn eventi estesi](http://msdn.microsoft.com/library/dn135324.aspx).

## <a name="create-a-database-mirroring-endpoint-user"></a>Creare un utente dell'endpoint di mirroring del database

Lo script di Transact-SQL seguente crea un account di accesso denominato `dbm_login` e un utente denominato `dbm_user`. Aggiornare lo script con una password complessa. Per creare l'utente dell'endpoint di mirroring del database, eseguire il comando seguente in tutte le istanze di SQL Server:

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>Creare un certificato

Il servizio SQL Server in Linux usa i certificati per autenticare la comunicazione tra gli endpoint del mirroring. 

Lo script Transact-SQL seguente crea una chiave master e un certificato. Quindi esegue il backup del certificato e protegge il file con una chiave privata. Aggiornare lo script con password complesse. Connettersi all'istanza del Server SQL primario. Per creare il certificato, eseguire lo script Transact-SQL seguente:

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

A questo punto, la replica di SQL Server primaria dispone di un certificato in `/var/opt/mssql/data/dbm_certificate.cer` un at chiave privata e `var/opt/mssql/data/dbm_certificate.pvk`. Copiare questi due file nello stesso percorso in tutti i server che ospiteranno le repliche di disponibilità. Usare l'utente mssql o concedere l'autorizzazione all'utente mssql per accedere a tali file. 

Nel server di origine, ad esempio, il comando seguente copia i file nel computer di destinazione. Sostituire il `**<node2>**` valori con i nomi delle istanze di SQL Server che ospiteranno le repliche. 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

In ogni server di destinazione, assegnare l'autorizzazione per l'utente mssql per accedere al certificato.

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>Creare il certificato nei server secondari

Lo script Transact-SQL seguente crea una chiave master e un certificato da backup creati nella replica primaria di SQL Server. Inoltre, il comando autorizza l'utente ad accedere al certificato. Aggiornare lo script con password complesse. La password di decrittografia è la stessa password utilizzata per creare il file .pvk in un passaggio precedente. Per creare il certificato, eseguire lo script seguente in tutti i server secondari:

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

Endpoint del mirroring del database utilizzano il protocollo TCP (Transmission Control) per inviare e ricevere messaggi tra istanze del server che fanno parte di sessioni di mirroring del database o ospitano repliche di disponibilità. L'endpoint del mirroring del database è in attesa su un numero di porta TCP univoco. Il listener TCP richiede un indirizzo IP del listener. L'indirizzo IP del listener deve essere un indirizzo IPv4. È inoltre possibile utilizzare `0.0.0.0`. 

Lo script di Transact-SQL seguente crea un endpoint di ascolto denominato `Hadr_endpoint` per il gruppo di disponibilità. Avvia l'endpoint e fornisce l'autorizzazione di connessione all'utente che è stato creato. Prima di eseguire lo script, sostituire i valori compresi tra `**< ... >**`.

Aggiornare lo script Transact-SQL seguente per l'ambiente in tutte le istanze di SQL Server: 

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
>Se è utilizzare SQL Server Express Edition in un nodo per ospitare una replica di sola configurazione, l'unico valore valido per `ROLE` è `WITNESS`. Eseguire lo script seguente in SQL Server Express Edition:

```SQL
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

La porta TCP sul firewall deve essere aperta per la porta del listener.



>[!IMPORTANT]
>Per la versione di SQL Server 2017, l'unico metodo di autenticazione supportato per l'endpoint del mirroring del database è `CERTIFICATE`. Il `WINDOWS` verrà abilitata l'opzione in una versione futura.

Per ulteriori informazioni, vedere [(SQL Server) di endpoint di mirroring del database](http://msdn.microsoft.com/library/ms179511.aspx).


