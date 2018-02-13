---
title: "Creare e configurare un gruppo di disponibilità per SQL Server in Linux | Documenti Microsoft"
description: "In questa esercitazione viene illustrato come creare e configurare i gruppi di disponibilità per SQL Server in Linux."
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 4e1190fea92c1e84ce38bd46040a8b5fcdd532d7
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>Creare e configurare un gruppo di disponibilità per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In questa esercitazione viene illustrato come creare e configurare un gruppo di disponibilità (AG) per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Linux. A differenza di [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] e in precedenza in Windows, è possibile abilitare estensivi con o senza creare prima il cluster Pacemaker sottostante. Integrazione con il cluster, se necessario, non viene eseguita fino a quando in un secondo momento.

L'esercitazione include le attività seguenti:
 
> [!div class="checklist"]
> * Abilitare gruppi di disponibilità.
> * Creare certificati ed endpoint di gruppo di disponibilità.
> * Utilizzare [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) o Transact-SQL per creare un gruppo di disponibilità.
> * Creare il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] account di accesso e le autorizzazioni per Pacemaker.
> * Creare risorse del gruppo di disponibilità in un cluster Pacemaker (solo per il tipo esterno).

## <a name="prerequisite"></a>Prerequisiti
- Distribuire il cluster a disponibilità elevata Pacemaker come descritto in [distribuire un cluster Pacemaker per SQL Server in Linux](sql-server-linux-deploy-pacemaker-cluster.md).


## <a name="enable-the-availability-groups-feature"></a>Abilitare la funzionalità gruppi di disponibilità

A differenza di Windows, non è possibile utilizzare PowerShell o [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] gruppi di Configuration Manager per abilitare la disponibilità di funzionalità (AG). In Linux, è necessario utilizzare `mssql-conf` per abilitare la funzionalità. Esistono due modi per abilitare la funzionalità gruppi di disponibilità: utilizzare il `mssql-conf` utilità o modifica di `mssql.conf` file manualmente.

> [!IMPORTANT]
> La funzionalità gruppo di disponibilità deve essere abilitata per le repliche di sola configurazione, anche in [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)].

### <a name="use-the-mssql-conf-utility"></a>Utilizzare l'utilità mssql conf

Prompt dei comandi, eseguire le operazioni seguenti:

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Modificare il file mssql.conf

È inoltre possibile modificare il `mssql.conf` file, che si trova sotto il `/var/opt/mssql` cartella, per aggiungere le righe seguenti:

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>Riavvio [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Dopo aver abilitato gruppi di disponibilità, come in Windows, è necessario riavviare [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Che può essere eseguita nel modo seguente:

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>Creare i certificati e l'endpoint dei gruppi disponibilità

Un gruppo di disponibilità Usa endpoint TCP per la comunicazione. In Linux, gli endpoint per un gruppo di disponibilità sono supportati solo se i certificati vengono utilizzati per l'autenticazione. Ciò significa che il certificato da un'istanza deve essere ripristinato in tutte le altre istanze che saranno repliche che partecipano stesso AG. Il processo di certificato è necessario anche per una sola configurazione di replica. 

Creazione di endpoint e certificati di ripristino può essere eseguite solo tramite Transact-SQL. È possibile utilizzare non[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-generato anche i certificati. È necessario anche un processo per gestire e sostituire i certificati che scadono.

> [!IMPORTANT]
> Se si prevede di utilizzare il [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] procedura guidata per creare il gruppo di disponibilità, è comunque necessario creare e ripristinare i certificati tramite Transact-SQL in Linux.

Per la sintassi completa le opzioni disponibili per i vari comandi (ad esempio aggiuntiva di sicurezza), consultare:

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [CREAZIONE DI CERTIFICATI](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> Anche se si crea un gruppo di disponibilità, il tipo di endpoint Usa *FOR DATABASE_MIRRORING*, perché alcuni aspetti sottostante una volta sono stati condivisi con tale funzionalità attualmente deprecato.

In questo esempio creerà i certificati per una configurazione a tre nodi. I nomi di istanza sono LinAGN1 LinAGN2 e LinAGN3.

1.  Eseguire le operazioni seguenti sul LinAGN1 per creare la chiave master, un certificato e un endpoint, nonché eseguire il backup del certificato. Per questo esempio, la porta TCP tipico 5022 viene utilizzata per l'endpoint.
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN1_Cert
    WITH SUBJECT = 'LinAGN1 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN1_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN1_Cert,
        ROLE = ALL);
    
    GO
    ```
    
2.  Eseguire la stessa in LinAGN2:
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    WITH SUBJECT = 'LinAGN2 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN2_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN2_Cert,
        ROLE = ALL);
    
    GO
    ```
    
3.  Infine, è possibile eseguire la stessa sequenza in LinAGN3:
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    WITH SUBJECT = 'LinAGN3 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN3_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN3_Cert,
        ROLE = ALL);
    
    GO
    ```
    
4.  Utilizzo `scp` o un'altra utilità, copiare i backup del certificato in ogni nodo che farà parte del gruppo di disponibilità.
    
    In questo esempio:
    
    - Copiare LinAGN1_Cert.cer LinAGN2 e LinAGN3
    - Copiare LinAGN2_Cert.cer LinAGN1 e LinAGN3.
    - Copiare LinAGN3_Cert.cer LinAGN1 e LinAGN2.
    
5.  Modificare la proprietà e il gruppo associato ai file di certificato copiato per `mssql`.
    
    ```bash
    sudo chown mssql:mssql <CertFileName>
    ```
    
6.  Creare account di accesso a livello di istanza e gli utenti associati a LinAGN2 e LinAGN3 su LinAGN1.
    
    ```SQL
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
7.  Ripristinare LinAGN2_Cert e LinAGN3_Cert su LinAGN1. Con i certificati delle altre repliche è un aspetto importante della comunicazione di gruppo di disponibilità e sicurezza.
    
    ```SQL
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
8.  Grant the logins associated with LinAG2 and LinAGN3 permission to connect to the endpoint on LinAGN1.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
9.  Creare account di accesso a livello di istanza e gli utenti associati a LinAGN1 e LinAGN3 su LinAGN2.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
10.  Ripristinare LinAGN1_Cert e LinAGN3_Cert su LinAGN2. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
11.  Grant the logins associated with LinAG1 and LinAGN3 permission to connect to the endpoint on LinAGN2.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
12.  Creare account di accesso a livello di istanza e gli utenti associati a LinAGN1 e LinAGN2 su LinAGN3.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    ```
    
13.  Ripristinare LinAGN1_Cert e LinAGN2_Cert su LinAGN3. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
14.  Grant the logins associated with LinAG1 and LinAGN2 permission to connect to the endpoint on LinAGN3.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    ```

## <a name="create-the-availability-group"></a>Creare il gruppo di disponibilità

In questa sezione viene illustrato come utilizzare [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) o Transact-SQL per creare il gruppo di disponibilità per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>Utilizzare [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)].

In questa sezione viene illustrato come creare un gruppo di disponibilità con un tipo di cluster di esterni con la creazione guidata gruppo di disponibilità di SQL Server Management Studio.

1.  In SQL Server Management Studio, espandere **disponibilità elevata Always On**, fare clic destro **gruppi di disponibilità**e selezionare **Creazione guidata nuovo gruppo di disponibilità**.

2.  Nella finestra di dialogo Introduzione, fare clic su **Avanti**.

3.  Nella finestra di dialogo specificare le opzioni di gruppo di disponibilità, immettere un nome per il gruppo di disponibilità e selezionare un tipo di cluster di esterno o nessuno nell'elenco a discesa. Esterno deve essere utilizzata quando Pacemaker verrà distribuito. Non è per gli scenari specializzati, ad esempio lettura scalabilità orizzontale. Selezionare l'opzione per il rilevamento dell'integrità di livello database è facoltativa. Per ulteriori informazioni su questa opzione, vedere [opzione di failover di disponibilità gruppo database integrità livello rilevamento](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md). Scegliere **Avanti**.

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  Nella finestra di dialogo Seleziona database, selezionare i database che faranno parte del gruppo di disponibilità. Ogni database deve avere un backup completo prima di aggiungerlo a un gruppo di disponibilità. Scegliere **Avanti**.

5.  Nella finestra di dialogo specifica repliche, fare clic su **Aggiungi Replica**.

6.  Nella finestra di dialogo Connetti al Server, immettere il nome dell'istanza di Linux [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] che sarà la replica secondaria e le credenziali per connettersi. Fare clic su **Connetti**.

7.  Ripetere i due passaggi precedenti per l'istanza che conterrà una sola configurazione di replica o un'altra replica secondaria.

8.  Tutte le istanze dovrebbero ora essere elencate nella finestra di dialogo specifica repliche. Se si utilizza un tipo di cluster di esterno, per la replica secondaria da un database secondario è true, verificare che la modalità di disponibilità corrisponda a quella della replica primaria e la modalità di failover è impostata come esterna. Per la replica di sola configurazione, selezionare solo una modalità di disponibilità della configurazione.

    Nell'esempio seguente viene illustrato un gruppo di disponibilità con due repliche di un tipo di cluster di esterni e una sola configurazione di replica.

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    Nell'esempio seguente viene illustrato un gruppo di disponibilità con due repliche, nessuno e una configurazione solo una replica di un tipo di cluster.

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  Se si desidera modificare le preferenze di backup, fare clic sulla scheda Preferenze di Backup. Per ulteriori informazioni sulle preferenze di backup con estensivi, vedere [configurare il backup su repliche di disponibilità](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).

10. Se tramite le repliche secondarie leggibili o creazione di un gruppo di disponibilità con un cluster di tipo None per la scala di lettura, è possibile creare un listener, selezionare la scheda di Listener. Inoltre è possibile aggiungere un listener in un secondo momento. Per creare un listener, scegliere l'opzione **creare un listener del gruppo di disponibilità** e immettere un nome e una porta TCP/IP se si desidera utilizzare un statico o assegnato automaticamente un indirizzo IP DHCP. Tenere presente che per un gruppo di disponibilità con un tipo di cluster None, l'indirizzo IP deve essere statico e impostare indirizzo IP del database primario.

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. Se viene creato un listener per gli scenari leggibili, SSMS 17.3 o versioni successive consente la creazione di routing in sola lettura nella procedura guidata. Può inoltre essere aggiunto in un secondo momento tramite SSMS o Transact-SQL. Per aggiungere routing ora di sola lettura:

    A.  Selezionare la scheda di Routing di sola lettura.

    B.  Immettere l'URL per le repliche di sola lettura. Questi URL sono simili agli endpoint, ad eccezione del fatto che utilizza la porta dell'istanza, non l'endpoint.

    c.  Selezionare ogni URL e dal basso, selezionare le repliche leggibile. Effettuare una selezione multipla, tenere premuto MAIUSC o clic e trascinamento.

12. Scegliere **Avanti**.

13. Scegliere la modalità di inizializzazione nelle repliche secondarie. Il valore predefinito consiste nell'usare [il seeding automatico](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md), che richiede lo stesso percorso in tutti i server che fanno parte del gruppo di disponibilità. È anche possibile la procedura guidata eseguire una copia di backup e ripristino (la seconda opzione); aggiungerlo se si dispone manualmente il backup, copiare e ripristinare il database di repliche (terza opzione); o aggiungere il database in un secondo momento (ultima opzione). Come con i certificati, se si è la creazione di backup e copiarli manualmente, è necessario che le autorizzazioni per i file di backup da impostare per le altre repliche. Scegliere **Avanti**.

14. Nella finestra di dialogo convalida, se tutti gli elementi non torna come esito positivo, provare a utilizzare. Alcuni avvisi sono accettabili e non irreversibile, ad esempio se non si crea un listener. Scegliere **Avanti**.

15. Nella finestra di dialogo riepilogo, fare clic su **fine**. Si inizierà ora il processo di creazione del gruppo di disponibilità.

16. Una volta completata la creazione del gruppo di disponibilità, fare clic su **Chiudi** sui risultati. È ora possibile visualizzare il gruppo di disponibilità in repliche in viste a gestione dinamica e nella cartella disponibilità elevata AlwaysOn in SQL Server Management Studio.

### <a name="use-transact-sql"></a>Usare Transact-SQL

In questa sezione vengono illustrati esempi di creazione di un gruppo di disponibilità tramite Transact-SQL. Il listener e il routing di sola lettura può essere configurati dopo aver creato il gruppo di disponibilità. È possibile modificare il gruppo di disponibilità con `ALTER AVAILABILITY GROUP`, ma la modifica del tipo di cluster non può essere eseguita [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Se non si intendeva creare un gruppo di disponibilità con un tipo di cluster di esterni, è necessario eliminarla e ricrearla con un tipo di cluster None. Altre informazioni e altre opzioni sono disponibili i seguenti collegamenti:

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [Configurare il Routing di sola lettura per un gruppo di disponibilità (SQL Server)](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [Creare o configurare un listener del gruppo di disponibilità (SQL Server)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>Repliche di esempio, uno-due con una configurazione replica sola (tipo di cluster esterno)

In questo esempio viene illustrato come creare un gruppo di disponibilità di due repliche che usa una sola configurazione di replica.

1.  Eseguire sul nodo che sarà la replica primaria che contiene la copia di lettura/scrittura completamente dei database. In questo esempio viene usato il seeding automatico.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1' WITH (
       ENDPOINT_URL = N' TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       SEEDING_MODE = AUTOMATIC),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       AVAILABILITY_MODE = CONFIGURATION_ONLY);
       
    GO
    ```
    
2.  Nella finestra di query connessa a altra replica, eseguire il comando seguente per creare un join della replica per il gruppo di disponibilità e avviare il processo di seeding dal database primario per la replica secondaria.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Nella finestra di query connessa alla replica solo configurazione, creare un join al gruppo di disponibilità.
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>Repliche di esempio 2 – 3 con il routing di sola lettura (tipo di cluster esterno)

Questo esempio mostra tre completo repliche e la modalità di sola lettura di routing può essere configurati come parte della creazione del gruppo di disponibilità iniziale.

1.  Eseguire sul nodo che sarà la replica primaria che contiene la copia di lettura/scrittura completamente dei database. In questo esempio viene usato il seeding automatico.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN2.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:1433')),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN2.FullyQualified.Name:1433')),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN3.FullyQualified.Name:1433'))
    LISTENER '<ListenerName>' (WITH IP = ('<IPAddress>', '<SubnetMask>'), Port = 1433);
    
    GO
    ```
    
    Alcuni aspetti da considerare questa configurazione:
    
    - *AGName* è il nome del gruppo di disponibilità.
    - *DBName* è il nome del database che verrà utilizzato con il gruppo di disponibilità. Può essere anche un elenco di nomi separati da virgole.
    - *ListenerName* è un nome diverso da uno dei nodi del server sottostanti. Verrà registrato nel DNS insieme a *IPAddress*.
    - *IPAddress* è un indirizzo IP associato *ListenerName*. È inoltre univoco e non uguale a uno dei nodi/server. Le applicazioni e gli utenti finali utilizzeranno uno *ListenerName* o *IPAddress* per la connessione per il gruppo di disponibilità.
    - *SubnetMask* è la subnet mask di *IPAddress*, ad esempio 255.255.255.0.

2.  Nella finestra di query connessa a altra replica, eseguire il comando seguente per creare un join della replica per il gruppo di disponibilità e avviare il processo di seeding dal database primario per la replica secondaria.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Ripetere il passaggio 2 per la terza replica.

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>Repliche di esempio 3: due con sola lettura e routing (nessun cluster di tipo)

In questo esempio viene illustrata la creazione di una configurazione di due repliche utilizzando un cluster di tipo None. Viene utilizzato per lo scenario di lettura scala in cui non è prevista alcuna funzione di failover. Verrà creato il listener che è effettivamente la replica primaria, nonché la sola lettura e routing, utilizzando la funzionalità di round robin.

1.  Eseguire sul nodo che sarà la replica primaria che contiene la copia di lettura/scrittura completamente dei database. In questo esempio viene usato il seeding automatico.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = NONE)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name: <PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name'.'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:<PortOfInstance>'));
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:<PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL =N'TCP://LinAGN2.FullyQualified.Name:<PortOfInstance>'));
    LISTENER '<ListenerName>' (WITH IP = ('<PrimaryReplicaIPAddress>', '<SubnetMask>'), Port = <PortOfListener>);
    
    GO
    ```
    
    Where
    - *AGName* è il nome del gruppo di disponibilità.
    - *DBName* è il nome del database che verrà utilizzato con il gruppo di disponibilità. Può essere anche un elenco di nomi separati da virgole.
    - *PortOfEndpoint* è il numero di porta utilizzato dall'endpoint creato.
    - *PortOfInstance* è il numero di porta utilizzato dall'istanza di [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].
    - *ListenerName* è un nome che è diverso rispetto a qualsiasi delle repliche sottostante ma non verrà effettivamente utilizzato.
    - *PrimaryReplicaIPAddress* è l'indirizzo IP della replica primaria.
    - *SubnetMask* è la subnet mask di *IPAddress*. Ad esempio 255.255.255.0.
    
2.  Join della replica secondaria al gruppo di disponibilità e di avviare il seeding automatico.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>Creare il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] account di accesso e le autorizzazioni per Pacemaker

Sottostante per un cluster per la disponibilità elevata Pacemaker [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Linux richiede l'accesso per il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] istanza, nonché le autorizzazioni per il gruppo di disponibilità. Questi passaggi consentono di creare l'account di accesso e le relative autorizzazioni, insieme a un file che spiega come accedere a Pacemaker [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

1.  Nella finestra di query connessa alla prima replica, eseguire le operazioni seguenti:

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  Nel nodo 1, immettere il comando 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    Verrà aperto l'editor Emacs.
    
3.  Nell'editor, immettere le due righe seguenti:

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  Tenere premuto il tasto CTRL e quindi premere X, quindi C per uscire e salvare il file.

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    Per bloccare il file.

6.  Ripetere i passaggi 1 e 5 su altri server che fungerà da repliche.

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Creare la disponibilità di risorse del gruppo nel cluster Pacemaker (solo esterne)

Dopo una disponibilità gruppo viene creato in [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], le risorse corrispondenti devono essere create in Pacemaker, se viene specificato un tipo di cluster di esterni. Sono presenti due risorse associate a un gruppo di disponibilità: il gruppo di disponibilità e un indirizzo IP. Configurazione delle risorse indirizzo IP è facoltativa se non si utilizza la funzionalità di listener, ma è consigliato.

La risorsa del gruppo di disponibilità creato è un tipo speciale di risorsa chiamata di un clone. La risorsa del gruppo di disponibilità è essenzialmente copie in ogni nodo ed è una risorsa di controllo denominata master. Lo schema è associato il server che ospita la replica primaria. Le repliche secondarie (regolare o configurazione sola) sono considerate come slave e può essere promossa a master in un failover.

1.  Creare la risorsa del gruppo di disponibilità con la sintassi seguente:

    **Red Hat Enterprise Linux (RHEL) e Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> --master meta notify=true
    ```

    >[!NOTE]
    >Su RHEL 7.4, è possibile riscontrare un avviso con l'utilizzo di - master. Per evitare questo problema, utilizzare `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    op start timeout=60s \
    op stop timeout=60s \
    op promote timeout=60s \
    op demote timeout=10s \
    op monitor timeout=60s interval=10s \
    op monitor timeout=60s interval=11s role="Master" \
    op monitor timeout=60s interval=12s role="Slave" \
    op notify timeout=60s
    ms ms-ag_cluster <NameForAGResource> \
    meta master-max="1" master-node-max="1" clone-max="3" \
    clone-node-max="1" notify="true" \
    commit
    ```
    
    dove *NameForAGResource* è il nome univoco assegnato a questa risorsa cluster per il gruppo di disponibilità e *AGName* è il nome del gruppo di disponibilità che è stato creato.
 
2.  Creare la risorsa indirizzo IP per il gruppo di disponibilità che verrà associato alla funzionalità di listener.

    **RHEL e Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForIPResource> ocf:heartbeat:IPaddr2 ip=<IPAddress> cidr_netmask=<Netmask>
    ```

    **SLES**
    
    ```bash
    crm configure \
    primitive <NameForIPResource> \
       ocf:heartbeat:IPaddr2 \
       params ip=<IPAddress> \
          cidr_netmask=<Netmask>
    ```
    
    dove *NameForIPResource* è il nome univoco per la risorsa IP, e *IPAddress* è l'indirizzo IP assegnato alla risorsa. In SLES, è necessario specificare la subnet mask. Ad esempio 255.255.255.0 avrebbe un valore pari a 24 per *Netmask.*
    
3.  Per garantire che l'indirizzo IP e la risorsa del gruppo di disponibilità sono in esecuzione nello stesso nodo, è necessario configurare un vincolo di condivisione del percorso.

    **RHEL e Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    dove *NameForIPResource* è il nome per la risorsa IP, *NameForAGResource* è il nome per la risorsa del gruppo di disponibilità e SLES, *NameForConstraint* è il nome per il vincolo.

4.  Creare un vincolo per assicurarsi che la risorsa del gruppo di disponibilità sia attivo e in esecuzione prima dell'indirizzo IP. Mentre il vincolo di percorso condiviso implica un vincolo di ordinamento, in questo modo.

    **RHEL e Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    dove *NameForIPResource* è il nome per la risorsa IP, *NameForAGResource* è il nome per la risorsa del gruppo di disponibilità e SLES, *NameForConstraint* è il nome per il vincolo.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come creare e configurare un gruppo di disponibilità per [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] in Linux. Si è appreso per:
> [!div class="checklist"]
> * Abilitare gruppi di disponibilità.
> * Gli endpoint Crea gruppo di disponibilità e certificati.
> * Utilizzare [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) o Transact-SQL per creare un gruppo di disponibilità.
> * Creare il [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] account di accesso e le autorizzazioni per Pacemaker.
> * Creare risorse di gruppo di disponibilità in un cluster Pacemaker.

Per la maggior parte delle attività di amministrazione di gruppo di disponibilità, inclusi gli aggiornamenti e del failover, vedere:

> [!div class="nextstepaction"]
> [Funzioni gruppo di disponibilità elevata per SQL Server in Linux](sql-server-linux-availability-group-failover-ha.md)

