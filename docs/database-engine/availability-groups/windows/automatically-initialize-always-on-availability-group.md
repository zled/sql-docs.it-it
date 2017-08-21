---
title: "Inizializzare automaticamente un gruppo di disponibilità Always On | Microsoft Docs"
ms.custom: 
ms.date: 11/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67c6a601-677a-402b-b3d1-8c65494e9e96
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: v-saume
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b30513c845d486875840eabd66506497182eb692
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="automatically-initialize-always-on-availability-group"></a>Inizializzare automaticamente un gruppo di disponibilità Always On
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


 SQL Server 2016 introduce il seeding automatico dei gruppi di disponibilità. Quando si crea un gruppo di disponibilità con seeding automatico, SQL Server crea automaticamente le repliche secondarie per ogni database nel gruppo. Con il seeding automatico non è più necessario eseguire manualmente il backup e il ripristino delle repliche secondarie. Per abilitare il seeding automatico, creare il gruppo di disponibilità con T-SQL.
 
## <a name="prerequisites"></a>Prerequisiti

Il seeding automatico richiede che il percorso dei dati e del file di log sia lo stesso in ogni istanza di SQL Server inclusa nel gruppo di disponibilità. 

Il seeding del gruppo di disponibilità comunica attraverso l'endpoint del mirroring del database. Aprire le regole del firewall in entrata per la porta dell'endpoint del mirroring in ogni server.

I database in un gruppo di disponibilità devono essere basati sul modello di recupero con registrazione completa. Il database deve avere un backup completo aggiornato e un backup del log delle transazioni. Questi file di backup non vengono usati per il seeding automatico, ma sono necessari per includere il database in un gruppo di disponibilità. 
 
## <a name="create-availability-group-with-automatic-seeding"></a>Creare un gruppo di disponibilità con seeding automatico

Per creare un gruppo di disponibilità con seeding automatico, impostare `SEEDING_MODE=AUTOMATIC`. 

L'esempio seguente crea un gruppo di disponibilità in un cluster di failover di un server Windows a due nodi. Prima di eseguire gli script, aggiornare i valori per l'ambiente.

1. Creare gli endpoint. Ogni server deve avere un endpoint. Lo script seguente crea un endpoint che usa la porta TCP 5022 per il listener. Impostare `<endpoint_name>` e `LISTENER_PORT` in modo che corrispondano all'ambiente ed eseguire lo script:

    ```
    --Create the endpoint on both servers
    -- Run this script twice, once on each server. 
    CREATE ENDPOINT [<endpoint_name>] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
    FOR DATA_MIRRORING (ROLE = ALL, AUTHENTICATION = WINDOWS NEGOTIATE, ENCRYPTION = REQUIRED ALGORITHM AES)
    GO
    ```

1. Creare il gruppo di disponibilità. Lo script seguente crea il gruppo di disponibilità. Aggiornare i valori per il nome del gruppo, i nomi dei server e i nomi di dominio ed eseguirlo nell'istanza primaria di SQL Server.  

    ```
    ---Run On Primary
    CREATE AVAILABILITY GROUP [<availability_group_name>]
    FOR DATABASE db1
    REPLICA ON'<*primary_server*>'
    WITH (ENDPOINT_URL = N'TCP://<primary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC),
    N'<secondary_server>' WITH (ENDPOINT_URL = N'TCP://<secondary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC);
    GO
    ``` 

1. Aggiungere il server secondario al gruppo di disponibilità e concedere l'autorizzazione al gruppo di disponibilità per creare i database. Eseguire lo script seguente nell'istanza secondaria di SQL Server: 
 
    ```
    --Run on Secondary Replica to join to the availability group
    ALTER AVAILABILITY GROUP [<availability_group_name>] JOIN
    GO  
    ALTER AVAILABILITY GROUP [<availability_group_name>] GRANT CREATE ANY DATABASE
    GO
    ```

SQL Server creerà automaticamente la replica di database nel server secondario. Se il database è di grandi dimensioni, il completamento della sincronizzazione del database potrebbe richiedere del tempo. Se un database si trova in un gruppo di disponibilità configurato per il seeding automatico, è possibile eseguire query sulla vista di sistema `sys.dm_hadr_automatic_seeding` per monitorare il seeding. La query seguente restituisce una riga per ogni database incluso in un gruppo di disponibilità configurato per il seeding automatico.

```
 SELECT start_time,
       ag.name,
       db.database_name,
       current_state,
       performed_seeding,
       failure_state,
       failure_state_desc
 FROM sys.dm_hadr_automatic_seeding autos 
    JOIN sys.availability_databases_cluster db ON autos.ag_db_id = db.group_database_id
    JOIN sys.availability_groups ag ON autos.ag_id = ag.group_id
```

## <a name="prevent-automatic-seeding-after-an-availability-group"></a>Impedire il seeding automatico per un gruppo di disponibilità

Per impedire temporaneamente al database primario di eseguire il seeding di altri database nella replica secondaria, è possibile negare al gruppo di disponibilità l'autorizzazione per creare database. Eseguire la query seguente nell'istanza che ospita la replica secondaria per negare al gruppo di disponibilità l'autorizzazione per creare i database di replica.

```
ALTER AVAILABILITY GROUP [<availability_group_name>] DENY CREATE ANY DATABASE
GO
```


## <a name="enable-automatic-seeding-on-an-existing-availability-group"></a>Abilitare il seeding automatico in un gruppo di disponibilità esistente

È possibile impostare il seeding automatico in un database esistente. Il comando seguente modifica un gruppo di disponibilità per consentire l'uso del seeding automatico. 

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
MODIFY REPLICA ON '<primary_node>' WITH (SEEDING_MODE = AUTOMATIC)
GO
```

Se necessario, questa operazione forza il riavvio del seeding in un database. Ad esempio, se seeding non riesce a causa di spazio su disco insufficiente nella replica secondaria, è possibile eseguire `ALTER AVAILABILITY GROUP ... WITH (SEEDING_MODE=AUTOMATIC)` per riavviare il seeding dopo aver aggiunto altro spazio.

## <a name="stop-automatic-seeding"></a>Arrestare il seeding automatico

Per arrestare il seeding automatico per un gruppo di disponibilità, eseguire lo script seguente nell'istanza che ospita la replica primaria:

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
    MODIFY REPLICA ON '<primary_node>'   
    WITH (SEEDING_MODE = MANUAL)
GO
```

Vengono annullate tutte le repliche attualmente sottoposte a seeding e si impedisce a SQL Server di inizializzare automaticamente le repliche in questo gruppo di disponibilità. La sincronizzazione non viene interrotta per le repliche già inizializzate. 


## <a name="monitor-automatic-seeding-availability-group"></a>Monitorare un gruppo di disponibilità con seeding automatico

### <a name="use-system-dynamic-management-views-to-monitor-seeding"></a>Usare le viste a gestione dinamica del sistema per monitorare il seeding

Le viste di sistema seguenti indicano lo stato del seeding automatico di SQL Server.

**sys.dm_hadr_automatic_seeding** 

Nella replica primaria eseguire una query su `sys.dm_hadr_automatic_seeding` per controllare lo stato del processo di seeding automatico. La vista restituisce una riga per ogni processo di seeding. Esempio:

``` 
SELECT start_time, 
        completion_time
        is_source,
        current_state,
        failure_state,
        failure_state_desc
FROM sys.dm_hadr_automatic_seeding
```
 
**sys.dm_hadr_physical_seeding_stats** 

Nella replica primaria eseguire una query sulla DMV `sys.dm_hadr_physical_seeding_stats` per visualizzare le statistiche fisiche per ogni processo di seeding attualmente in esecuzione. La query seguente restituisce le righe quando il seeding è in esecuzione:

```
SELECT * FROM sys.dm_hadr_physical_seeding_stats;
```

### <a name="diagnose-database-initialization-using-automatic-seeding-in-the-error-log"></a>Diagnosticare l'inizializzazione del database usando il seeding automatico nel log degli errori

Quando si aggiunge un database a un gruppo di disponibilità configurato per il seeding automatico, SQL Server esegue un backup VDI attraverso l'endpoint del gruppo di disponibilità. Esaminare il log degli errori di SQL Server per informazioni su quando è stato completato il backup e sincronizzato il database secondario.

### <a name="diagnose-database-level-health-with-extended-events"></a>Diagnosticare l'integrità a livello di database con gli eventi estesi

Il seeding automatico ora include nuovi eventi estesi per tenere traccia delle modifiche allo stato, degli errori e delle statistiche sulle prestazioni durante l'inizializzazione. 

Ad esempio, questo script crea una sessione di eventi estesi che acquisisce gli eventi correlati al seeding automatico: 

```
CREATE EVENT SESSION [AlwaysOn_autoseed] ON SERVER 
    ADD EVENT sqlserver.hadr_automatic_seeding_state_transition,
    ADD EVENT sqlserver.hadr_automatic_seeding_timeout,
    ADD EVENT sqlserver.hadr_db_manager_seeding_request_msg,
    ADD EVENT sqlserver.hadr_physical_seeding_backup_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_failure,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_target_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_progress,
    ADD EVENT sqlserver.hadr_physical_seeding_restore_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_submit_callback
    ADD TARGET package0.event_file(SET filename=N’autoseed.xel’,max_file_size=(5),max_rollover_files=(4))
WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=30 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=ON)
GO 

ALTER EVENT SESSION AlwaysOn_autoseed ON SERVER STATE=START
GO 
```


La tabella seguente elenca gli eventi estesi correlati al seeding automatico: 

| Nome | Descrizione|
|------------ |---------------| 
|hadr_db_manager_seeding_request_msg |  Messaggio di richiesta di seeding.
|hadr_physical_seeding_backup_state_change |    Modifica dello stato lato backup del seed fisico.
|hadr_physical_seeding_restore_state_change |Modifica dello stato lato ripristino del seed fisico.
|hadr_physical_seeding_forwarder_state_change | Modifica dello stato lato server di inoltro del seed fisico.
|hadr_physical_seeding_forwarder_target_state_change |  Modifica dello stato lato destinazione del server di inoltro del seed fisico.
|hadr_physical_seeding_submit_callback  |Evento di callback invio del seed fisico.
|hadr_physical_seeding_failure  |Evento di errore del seed fisico.
|hadr_physical_seeding_progress |   Evento di stato del seed fisico.
|hadr_physical_seeding_schedule_long_task_failure   |Evento di errore per attività di lunga durata della pianificazione per il seed fisico.
|hadr_automatic_seeding_start   |Si verifica quando viene inviata un'operazione di seeding automatico.
|hadr_automatic_seeding_state_transition    |Si verifica quando cambia lo stato di un'operazione di seeding automatico.
|hadr_automatic_seeding_success |Si verifica quando un'operazione di seeding automatico riesce.
|hadr_automatic_seeding_failure |Si verifica quando un'operazione di seeding automatico non riesce.
|hadr_automatic_seeding_timeout |Si verifica in caso di timeout di un'operazione di seeding automatico.

### <a name="other-troubleshooting-considerations"></a>Altre considerazioni sulla risoluzione dei problemi

**Monitorare il completamento del seeding automatico**

Eseguire una query `sys.dm_hadr_physical_seeding_stats` per il processo di seeding automatico in esecuzione. La vista restituisce una riga per ogni database. Esempio:

```
SELECT local_database_name, 
       role_desc, 
       internal_state_desc, 
       transfer_rate_bytes_per_second, 
       transferred_size_bytes, 
       database_size_bytes, 
       start_time_utc, 
       end_time_utc, estimate_time_complete_utc, 
       total_disk_io_wait_time_ms, 
       total_network_wait_time_ms, 
       is_compression_enabled 
FROM sys.dm_hadr_physical_seeding_stats
```

**Risolvere il problema della mancata visualizzazione di un database in un gruppo di disponibilità configurato per il seeding automatico**


Quando un database non viene visualizzato in un gruppo di disponibilità con seeding automatico abilitato, è probabile che il seeding automatico non sia riuscito. Questo impedisce l'aggiunta del database al gruppo di disponibilità nella replica primaria e secondaria. Eseguire una query `sys.dm_hadr_automatic_seeding` sulle repliche primarie e secondarie. Ad esempio, eseguire la query seguente per identificare lo stato di errore del seeding automatico.

```
SELECT start_time, 
       completion_time, 
       is_source, 
       current_state, 
       failure_state, 
       failure_state_desc, 
       error_code 
FROM sys.dm_hadr_automatic_seeding
```

## <a name="automatic-seeding-and-performance-considerations"></a>Considerazioni relative al seeding automatico e alle prestazioni

SQL Server usa un numero fisso di thread per il seeding automatico. Nell'istanza primaria SQL Server usa un thread per ogni LUN per leggere le modifiche. Nell'istanza secondaria SQL Server usa un thread per ogni LUN per inizializzare il database.

Impostare il flag di traccia 9567 sulla replica primaria per abilitare la compressione del flusso di dati durante il seeding automatico. Ciò consente di ridurre notevolmente il tempo di trasferimento del seeding automatico, ma allo stesso tempo aumenta anche l'utilizzo della CPU. Per altre informazioni, vedere [Tune compression for availability group (Ottimizzare la compressione per il gruppo di disponibilità)](../../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md). 


## <a name="when-not-to-use-automatic-seeding"></a>Quando evitare l'utilizzo del seeding automatico

In alcuni scenari il seeding automatico potrebbe non essere la scelta ottimale per inizializzare una replica secondaria. Durante il seeding automatico, SQL Server esegue un backup in rete per l'inizializzazione. Questo processo può essere lento se i database sono molto grandi o se la replica secondaria è remota. Non è possibile troncare il log delle transazioni per questi database durante il processo di backup, quindi un processo di inizializzazione prolungato in un database occupato può causare un aumento significativo del log delle transazioni.
Prima di aggiungere un database a un gruppo di disponibilità con seeding automatico, valutare le dimensioni del database, il carico e la distanza del sito tra le repliche.

## <a name="resources"></a>Risorse

[CREATE AVAILABILITY GROUP (Transact-SQL) -](https://msdn.microsoft.com/library/ff878399.aspx)

[Guida alla risoluzione dei problemi e al monitoraggio dei gruppi di disponibilità Always On](http://technet.microsoft.com/library/dn135328.aspx)


