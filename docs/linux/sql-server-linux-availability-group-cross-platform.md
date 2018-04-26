---
title: Configurare sempre SQL Server nel gruppo di disponibilità in Windows e Linux | Documenti Microsoft
description: Configura gruppo disponibilità SQL Server con le repliche in Windows e Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/31/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: e2294549df8bca9fc21d7a72a26a59839fea9022
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Configurare SQL Server gruppo di disponibilità AlwaysOn in Windows e Linux (multipiattaforma)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

In questo articolo vengono illustrati i passaggi per creare un sempre nel gruppo di disponibilità (AG) con una replica in un server Windows e l'altra replica in un server Linux. Questa configurazione è multipiattaforma perché le repliche si trovano in sistemi operativi diversi. Utilizzare questa configurazione per la migrazione da una piattaforma a altra o il ripristino di emergenza (ripristino di emergenza). Questa configurazione non supporta la disponibilità elevata poiché non esiste alcuna soluzione di cluster per gestire una configurazione di più piattaforme. 

![Ibrida nessuno](./media/sql-server-linux-availability-group-overview/image1.png)

Prima di procedere, è necessario conoscere con l'installazione e configurazione per le istanze di SQL Server in Windows e Linux. 

## <a name="scenario"></a>Scenario

In questo scenario, due server si trovano in sistemi operativi diversi. Windows Server 2016 denominato `WinSQLInstance` ospita la replica primaria. Un server Linux denominato `LinuxSQLInstance` ospitare la replica secondaria.

## <a name="configure-the-ag"></a>Configurare il gruppo di disponibilità 

I passaggi per creare il gruppo di disponibilità sono come i passaggi per creare un gruppo di disponibilità per i carichi di lavoro di lettura della scala. Il tipo di cluster del gruppo di disponibilità è NONE, poiché non esiste alcun gestore cluster. 

   >[!NOTE]
   >Per gli script in questo articolo, le parentesi acute `<` e `>` identificano i valori che è necessario sostituire per l'ambiente. Le parentesi uncinate stessi non sono necessari per gli script. 

1. Installare SQL Server 2017 in Windows Server 2016, abilitare gruppi di disponibilità AlwaysOn da Gestione configurazione SQL Server e impostare l'autenticazione modalità mista. 

   >[!TIP]
   >Se si convalida la soluzione in Azure, posizionare entrambi i server nello stesso set affinché che sono separati nel data center di disponibilità. 

   **Abilitare gruppi di disponibilità**

   Per istruzioni, vedere [abilitare e disabilitare gruppi di disponibilità AlwaysOn (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Abilitare gruppi di disponibilità](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   Gestione configurazione SQL Server rileva che il computer non è un nodo in un cluster di failover. 

   Dopo aver abilitato gruppi di disponibilità, riavviare SQL Server.

   **Impostare l'autenticazione modalità mista**

   Per istruzioni, vedere [modifica della modalità di autenticazione server](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure).

1. Installare SQL Server 2017 in Linux. Per istruzioni, vedere [installare SQL Server](sql-server-linux-setup.md). Abilitare `hadr` tramite mssql conf

   Per abilitare `hadr` tramite conf mssql da un prompt della shell, eseguire il comando seguente:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   Dopo aver abilitato `hadr`, riavviare l'istanza di SQL Server.  

   Di seguito viene illustrato il passaggio di completamento.

   ![Abilitare Linux di gruppi di disponibilità](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Configurare il file hosts in entrambi i server o registrare i nomi dei server con DNS.

1. Aprire le porte del firewall per TCP 1433 e 5022 su Windows e Linux.

1. Nella replica primaria, creare un account di accesso e una password.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. Nella replica primaria, creare una chiave master e certificato, quindi eseguire il backup del certificato con una chiave privata.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. Copiare il certificato e chiave privata per il server Linux (replica secondaria) `/var/opt/mssql/data`. È possibile utilizzare `pscp` per copiare i file al server Linux. 

1. Impostare il gruppo e la proprietà di chiave privata e il certificato da `mssql:mssql`.

   Lo script seguente imposta il gruppo e la proprietà dei file. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   Nel diagramma seguente, la proprietà e gruppo siano impostate correttamente per la chiave e il certificato.

   ![Abilitare Linux di gruppi di disponibilità](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. Nella replica secondaria, creare un account di accesso e una password e creare una chiave master.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. Nella replica secondaria, ripristinare il certificato è stata copiata nella `/var/opt/mssql/data`. 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. Nella replica primaria, creare un endpoint.

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >Il firewall deve essere aperto per il listener di porta TCP. Nello script precedente, la porta è la 5022. Utilizzare qualsiasi porta TCP disponibile. 

1. Nella replica secondaria, creare l'endpoint. Ripetere il precedente script nella replica secondaria per creare l'endpoint. 

1. Nella replica primaria, creare il gruppo di disponibilità con `CLUSTER_TYPE = NONE`. Lo script di esempio utilizza `SEEDING_MODE = AUTOMATIC` per creare il gruppo di disponibilità. 

   >[!NOTE]
   >Quando l'istanza di Windows di SQL Server utilizza i percorsi diversi per i dati e log file, automatici seeding non riesce per l'istanza di SQL Server, poiché questi percorsi non sono presenti nella replica secondaria. Per utilizzare lo script seguente per un gruppo di disponibilità di più piattaforme, il database richiede lo stesso percorso per i file di dati e di log nel server di Windows. In alternativa è possibile aggiornare lo script per impostare `SEEDING_MODE = MANUAL` e quindi eseguire il backup e ripristino del database con `NORECOVERY` per il seeding del database. 
   >
   >Questo comportamento si applica alle immagini di Azure Marketplace. 
   >
   >Per ulteriori informazioni su seeding automatico, vedere [il Seeding automatico - Layout dei dischi](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Prima di eseguire lo script, aggiornare i valori per gli estensivi.

      * Sostituire `<WinSQLInstance>` con il nome del server dell'istanza di SQL Server di replica primaria.

      * Sostituire `<LinuxSQLInstance>` con il nome del server dell'istanza di SQL Server di replica secondaria. 

   Per creare il gruppo di disponibilità, aggiornare i valori ed eseguire lo script nella replica primaria.  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   Per ulteriori informazioni, vedere [Crea gruppo di disponibilità (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md).

1. Nella replica secondaria, creare un join del gruppo di disponibilità.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Creare un database per il gruppo di disponibilità. La procedura di esempio utilizza un database denominato `<TestDB>`. Se si utilizza il seeding automatico, impostare lo stesso percorso per i dati e i file di log. 

   Prima di eseguire lo script, aggiornare i valori per il database.

      * Sostituire `<TestDB>` con il nome del database.

      * Sostituire `<F:\Path>` con il percorso per i file di database e di log. Utilizzare lo stesso percorso per i file di database e di log. 

      È inoltre possibile utilizzare i percorsi predefiniti. 

    Per creare il database, eseguire lo script. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Eseguire un backup completo del database. 

1. Se non si utilizza il seeding automatico, è possibile ripristinare il database nel server di replica secondaria (Linux). [Eseguire la migrazione di un database di SQL Server da Windows per Linux tramite backup e ripristino](sql-server-linux-migrate-restore-database.md). Ripristinare il database `WITH NORECOVERY` nella replica secondaria. 

1. Aggiungere il database per il gruppo di disponibilità. Aggiornare lo script di esempio. Sostituire `<TestDB>` con il nome del database. Nella replica primaria, eseguire la query SQL per aggiungere il database al gruppo di disponibilità.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Verificare che il database sia recupero presente nella replica secondaria. 

## <a name="fail-over-the-primary-replica"></a>Eseguire il failover della replica primaria

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

In questo articolo esaminato i passaggi per creare un gruppo di disponibilità multipiattaforma per supportare i carichi di lavoro di migrazione o la scala di lettura. E può essere utilizzato per il ripristino di emergenza manuale. Inoltre spiegato come eseguire il failover del gruppo di disponibilità. Un gruppo di disponibilità multipiattaforma utilizza il tipo di cluster `NONE` e non supporta la disponibilità elevata perché non esiste alcun strumento di cluster tra piattaforme. 

## <a name="next-steps"></a>Passaggi successivi

[Panoramica di gruppi di disponibilità Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Nozioni fondamentali sulla disponibilità di SQL Server per le distribuzioni di Linux](sql-server-linux-ha-basics.md)
