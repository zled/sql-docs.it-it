---
title: "Configurare il gruppo di disponibilità di scalabilità orizzontale lettura per SQL Server in Linux | Documenti Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cf249ff8e6d2e82d1cf413bdec0272e3796b72cb
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="configure-read-scale-out-availability-group-for-sql-server-on-linux"></a>Configurare il gruppo di disponibilità di scalabilità orizzontale lettura per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

È possibile configurare un gruppo di disponibilità di scalabilità orizzontale lettura per SQL Server in Linux. Esistono due architetture per i gruppi di disponibilità. Oggetto *la disponibilità elevata* architettura utilizza una gestione di cluster per assicurare la continuità aziendale migliorata. Questa architettura può anche includere letture repliche di scalabilità orizzontale. Per creare l'architettura a disponibilità elevata, vedere [configurare sempre nel gruppo di disponibilità per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md).

Questo documento viene illustrato come creare un *scalabilità lettura* gruppo di disponibilità senza un gestore cluster. Questa architettura fornisce solo lettura scalabilità orizzontale solo. Non fornisce la disponibilità elevata.

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Creare il gruppo di disponibilità

Creare il gruppo di disponibilità. Set `CLUSTER_TYPE = NONE`. Inoltre, impostare ogni replica con `FAILOVER_MODE = NONE`. Le applicazioni client in esecuzione analitica o reporting carichi di lavoro possono direttamente la connessione ai database secondari. È anche possibile creare un elenco di routing di sola lettura. Le connessioni alla replica primaria in avanti leggere le richieste di connessione a ognuna delle repliche secondarie della lista di distribuzione in uno schema round robin.

Lo script di Transact-SQL seguente crea un nome di gruppo di disponibilità `ag1`. Lo script consente di configurare le repliche del gruppo di disponibilità con `SEEDING_MODE = AUTOMATIC`. Questa impostazione, SQL Server creare automaticamente il database in ciascun server secondario dopo averlo aggiunto al gruppo di disponibilità. Aggiornare lo script seguente per l'ambiente. Sostituire il `**<node1>**` e `**<node2>**` valori con i nomi delle istanze di SQL Server che ospitano le repliche. Sostituire il `**<5022>**` con la porta è impostata per l'endpoint. Nella replica primaria di SQL Server, eseguire l'istruzione Transact-SQL seguente:

```Transact-SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'**<node1>**' WITH (
            ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'**<node2>**' WITH ( 
            ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-availability-group"></a>Creare un join al gruppo di disponibilità secondaria SQL Server

Lo script Transact-SQL seguente viene aggiunto un server a un gruppo di disponibilità denominato `ag1`. Aggiornare lo script per l'ambiente. In ogni replica secondaria di SQL Server, eseguire Transact-SQL seguente per aggiungere il gruppo di disponibilità.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Non si tratta di una configurazione a disponibilità elevata, se è necessaria la disponibilità elevata, seguire le istruzioni in [Configura gruppo di disponibilità AlwaysOn per SQL Server in Linux](sql-server-linux-availability-group-configure-ha.md). In particolare, creare il gruppo di disponibilità con `CLUSTER_TYPE=WSFC` (in Windows) o `CLUSTER_TYPE=EXTERNAL` (in Linux) e integrare con un gestore cluster - WSFC in Windows o Pacemaker in Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Connettersi a repliche secondarie di sola lettura

Esistono due modi per connettersi a repliche secondarie di sola lettura. Le applicazioni possono connettersi direttamente all'istanza di SQL Server che ospita la replica secondaria ed eseguire query sui database oppure possono utilizzare il routing di sola lettura. routing di sola lettura richiede un listener.

[Repliche secondarie leggibili](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)

[routing di sola lettura](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-primary-replica-on-read-scale-out-availability-group"></a>Eseguire il failover la replica primaria nel gruppo di disponibilità di scalabilità orizzontale lettura

Ogni gruppo di disponibilità include solo una replica primaria. La replica primaria consente operazioni di lettura e scrittura. Per modificare la replica primaria, è possibile eseguire il failover. In un gruppo di disponibilità per la disponibilità elevata, nel processo di failover consente di automatizzare la gestione di cluster. In un gruppo di disponibilità di scalabilità orizzontale lettura, il processo di failover è manuale. Esistono due modi per eseguire il failover la replica primaria in un gruppo di disponibilità di scala di lettura.

- Forzato manuale tramite con perdita di dati

- Il failover manuale senza perdita di dati

### <a name="forced-fail-over-with-data-loss"></a>Forzato failover con perdita di dati

Utilizzare questo metodo quando la replica primaria non è disponibile e non può essere ripristinata. È possibile trovare ulteriori informazioni sul failover forzato con perdita di dati in [eseguire un Failover manuale forzato](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).

Per forzare il failover con perdita di dati, connettersi all'istanza di SQL che ospita la replica secondaria di destinazione ed eseguire:
```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>Il failover manuale senza perdita di dati

Utilizzare questo metodo quando la replica primaria è disponibile, ma è necessario temporaneamente o definitivamente, modificare la configurazione e modificare l'istanza di SQL Server che ospita la replica primaria. Prima di eseguire il failover manuale su, verificare che la replica secondaria di destinazione viene aggiornata, in modo che non vi sia alcuna perdita di dati. 

I passaggi seguenti viene descritto come eseguire manualmente il failover senza perdita di dati:

1. Effettuare il commit sincrono replica secondaria di destinazione.

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] MODIFY REPLICA ON N'**<node2>*' WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```
1. Aggiornamento `required_synchronized_secondaries_to_commit`su 1.

   Questa impostazione assicura che ogni transazione attiva viene eseguito il commit per la replica primaria e almeno un database secondario sincrono. Il gruppo di disponibilità è pronto per eseguire il failover quando il synchronization_state_desc è sincronizzato e il sequence_number è uguale per entrambi primaria e replica secondaria di destinazione. Eseguire la query per controllare:

   ```Transact-SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

1. Abbassare di livello la replica primaria alla replica secondaria. Dopo la replica primaria viene abbassato di livello, è in sola lettura. Eseguire questo comando sull'istanza SQL che ospita la replica primaria per aggiornare il ruolo secondario:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY); 
   ```

1. Alzare di livello la replica secondaria di destinazione come primaria. 

   ```Transact-SQL
   ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Per eliminare un utilizzo di gruppo di disponibilità [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Per un gruppo di disponibilità creato con CLUSTER_TYPE NONE o esterno, il comando deve essere eseguito in parte le repliche del gruppo di disponibilità.

## <a name="next-steps"></a>Passaggi successivi

[Configurare il gruppo di disponibilità distribuito](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)

[Altre informazioni sui gruppi di disponibilità](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)


