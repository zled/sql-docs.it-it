---
title: Seeding automatico per le repliche secondarie (SQL Server) | Microsoft Docs
description: Usare il seeding automatico per inizializzare le repliche secondarie.
services: data-lake-analytics
ms.custom: 
ms.date: 06/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Automatic seeding [SQL Server], secondary replica
ms.assetid: 
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1b72f9f5bf58f72bb4284b1a6cc8d0af7a722aed
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="automatic-seeding-for-secondary-replicas"></a>Seeding automatico per le repliche secondarie

[!INCLUDE [tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

In SQL Server 2012 e 2014, l'unico modo per inizializzare una replica secondaria in un gruppo di disponibilità consiste nell'usare le operazioni di backup, copia e ripristino. SQL Server 2016 introduce una nuova funzionalità per inizializzare una replica secondaria: il *seeding automatico*. Il seeding automatico usa il trasporto del flusso di log per trasmettere il backup mediante un'infrastruttura VDI nella replica secondaria per ogni database del gruppo di disponibilità tramite endpoint configurati. Questa nuova funzionalità può essere usata durante la creazione iniziale di un gruppo di disponibilità o quando viene aggiunto un database a un gruppo di disponibilità. Il seeding automatico si trova in tutte le edizioni di SQL Server che supportano i gruppi di disponibilità Always On e può essere usato sia con i gruppi di disponibilità tradizionali che con i [gruppi di disponibilità distribuiti](distributed-availability-groups.md).

## <a name="considerations"></a>Considerazioni

Le considerazioni sull'uso del seeding automatico includono:

* [Impatto del log delle prestazioni e delle transazioni sulla replica primaria](#performance-and-transaction-log-impact-on-the-primary-replica)
* [Layout dei dischi](#disk-layout)
* [Sicurezza](#security)


### <a name="performance-and-transaction-log-impact-on-the-primary-replica"></a>Impatto del log delle prestazioni e delle transazioni sulla replica primaria

Il seeding automatico potrebbe essere pratico o meno per inizializzare una replica secondaria, a seconda delle dimensioni del database, della velocità della rete e della distanza tra le repliche primaria e secondaria. Si consideri ad esempio di avere una situazione simile alla seguente:

* Dimensioni del database di 5 TB
* Velocità della rete di 1 GB/sec
* Distanza tra i due siti di 1.000 miglia

Se è disponibile la larghezza di banda completa, una rete di 1 GB/sec può fornire una velocità effettiva sostenibile di 125 MB/sec. In questo esempio, il seeding automatico richiederebbe poco più di 11 ore. In pratica, il processo di seeding automatico è leggermente più lento, perché i segnali della rete peggiorano per le distanze più lunghe e il collegamento viene in genere condiviso con altre risorse nella rete. Durante il seeding, il log delle transazioni per il database nella replica primaria continuerà ad aumentare e non può essere troncato finché il seeding automatico di tale database non viene completato.  È quindi possibile troncare il log delle transazioni con un backup del log delle transazioni.

Il seeding automatico è un processo a thread singolo in grado di gestire fino a cinque database. Questo potrebbe influire sulle prestazioni, soprattutto se il gruppo di disponibilità ha più di un database.

Per il seeding automatico è possibile usare la compressione, ma è disabilitata per impostazione predefinita. Attivando la compressione si riduce la larghezza di banda di rete e si accelera possibilmente il processo, ma si ottiene in cambio un sovraccarico aggiuntivo del processore. Per usare la compressione durante il seeding automatico, abilitare il flag di traccia 9567. Vedere [Ottimizzare la compressione per un gruppo di disponibilità](tune-compression-for-availability-group.md).

### <a name="disk-layout"></a>Layout dei dischi

La cartella in cui verrà creato il database per il seeding automatico deve già esistere e deve essere uguale a quella del percorso per la replica primaria.

### <a name="security"></a>Security

Le autorizzazioni di sicurezza variano a seconda del tipo di replica da inizializzare:

* Per un gruppo di disponibilità tradizionale, le autorizzazioni devono essere concesse al gruppo di disponibilità nella replica secondaria quando viene aggiunta al gruppo di disponibilità. In Transact-SQL usare il comando ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE.
* Per un gruppo di disponibilità distribuito in cui i database della replica che verranno creati si trovano nella replica primaria del secondo gruppo di disponibilità non sono necessarie autorizzazioni aggiuntive perché è già un gruppo di disponibilità primario.
* Per una replica secondaria nel secondo gruppo di disponibilità di un gruppo di disponibilità distribuito, è necessario usare il comando ALTER AVAILABILITY GROUP [2ndAGName] GRANT CREATE ANY DATABASE. Verrà eseguito il seeding di questa replica secondaria dal gruppo di disponibilità primario del secondo gruppo di disponibilità.

## <a name="create-an-availability-group-with-automatic-seeding"></a>Creare un gruppo di disponibilità con seeding automatico

È possibile creare un gruppo di disponibilità con il seeding automatico con Transact-SQL o SQL Server Management Studio (SSMS versione 17 o successiva). Per usare la creazione guidata Gruppo di disponibilità in SSMS, attenersi a [queste istruzioni](use-the-availability-group-wizard-sql-server-management-studio.md). Quando si arriva al passaggio 9, come prima opzione predefinita verrà visualizzato il seeding automatico.

![Seleziona sincronizzazione dati iniziale][1]

L'esempio seguente crea un gruppo di disponibilità con Transact-SQL. Vedere anche l'argomento [Creare un gruppo di disponibilità (Transact-SQL)](create-an-availability-group-transact-sql.md). Il seeding viene abilitato in una replica secondaria impostando l'opzione SEEDING_MODE su AUTOMATIC. Il comportamento predefinito è MANUAL, che è il comportamento delle versioni precedenti a SQL Server 2016 che richiede il backup del database da eseguire nella replica primaria, la copia del file di backup nella replica secondaria e il ripristino del backup con l'opzione WITH NORECOVERY.

```
CREATE AVAILABILITY GROUP [AGName]
  FOR DATABASE db1
  REPLICA ON N'Primary_Replica'
WITH (
  ENDPOINT_URL = N'TCP://Primary_Replica.Contoso.com:5022', 
  FAILOVER_MODE = AUTOMATIC, 
  AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
),
  N'Secondary_Replica' WITH (
    ENDPOINT_URL = N'TCP://Secondary_Replica.Contoso.com :5022', 
    FAILOVER_MODE = AUTOMATIC, 
    SEEDING_MODE = AUTOMATIC);
 GO
```

L'impostazione di SEEDING_MODE in una replica primaria durante l'istruzione CREATE AVAILABILITY GROUP non ha alcun effetto perché la replica primaria contiene già la copia principale di lettura/scrittura del database. SEEDING_MODE verrà applicato solo quando un'altra replica diventa la replica primaria e viene aggiunto un database. La modalità di seeding può essere modificata successivamente. Vedere [Modificare la modalità di seeding di una replica](#change-the-seeding-mode-of-a-replica).

In un'istanza che diventa una replica secondaria, dopo l'aggiunta dell'istanza al log di SQL Server viene aggiunto il messaggio seguente:

Alla replica di disponibilità locale per il gruppo di disponibilità 'AGName' non è stata concessa l'autorizzazione per creare i database sebbene SEEDING_MODE sia impostato su AUTOMATIC. Usare il comando ALTER AVAILABILITY GROUP … GRANT CREATE ANY DATABASE per consentire la creazione di database di cui è stato effettuato il seeding dalla replica di disponibilità primaria.

Dopo l'aggiunta eseguire l'istruzione seguente:

```
ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE
 GO
````

> [!NOTE] 
> Attualmente c'è un problema noto a partire da SQL Server 2016 SP1 CU2 dove una replica secondaria deve attendere tre minuti per consentire al gruppo di disponibilità di eseguire il seeding del database prima dell'esecuzione di un'istruzione ALTER AVAILABILITY GROUP... Prima dello scadere di tale intervallo di tempo, l'istruzione non restituirà alcun errore, anzi indicherà l'esito positivo dell'operazione. Anche questo è un problema noto. Questi errori verranno risolti in un futuro aggiornamento di SQL Server. Come soluzione alternativa, inserire un'istruzione WAITFOR:

```
WAITFOR DELAY '00:03:15';
ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE;
GO
```

Se l'operazione ha esito positivo, i database vengono creati automaticamente nella replica secondaria con uno dei due stati seguenti:

* SYNCHRONIZED se la replica secondaria è configurata per essere sincrona e i dati vengono sincronizzati completamente.
* SYNCHRONIZING se la replica secondaria è configurata con lo spostamento dei dati asincrono o quando è configurata con dati sincroni, ma non ancora sincronizzati con la replica primaria.

<a name="sql-server-log"></a> Oltre alle [DMV (viste a gestione dinamica)](#dynamic-management-views) descritte di seguito, l'inizio e il completamento del seeding automatico possono essere visualizzati nel log di SQL Server:

![Log di SQL Server][2]

## <a name="combine-backup-and-restore-with-automatic-seeding"></a>Combinare operazioni di backup e ripristino con il seeding automatico

Con il seeding automatico è possibile combinare le operazioni tradizionali di backup, copia e ripristino. In questo caso, ripristinare prima il database in una replica secondaria, inclusi tutti i log delle transazioni disponibili. Successivamente, abilitare il seeding automatico quando si crea il gruppo di disponibilità per "aggiornare" il database della replica secondaria, come se venisse ripristinato un backup della parte finale del log (vedere [Backup della parte finale del log (SQL Server)](../../../relational-databases/backup-restore/tail-log-backups-sql-server.md)).

## <a name="add-a-database-to-an-availability-group-with-automatic-seeding"></a>Aggiungere un database a un gruppo di disponibilità con seeding automatico

È possibile aggiungere un database a un gruppo di disponibilità con il seeding automatico con Transact-SQL o SQL Server Management Studio (SSMS versione 17 o successiva).
Se per la replica secondaria è stato usato il seeding automatico quando è stata aggiunta al gruppo di disponibilità, non è necessario eseguire alcuna operazione. Se sono state eseguite le operazioni di backup, copia e ripristino, modificare innanzitutto la modalità di seeding (vedere la sezione successiva) e quindi quando si aggiunge il database usare l'istruzione GRANT. Vedere [Gruppo di disponibilità - Aggiungere un database](availability-group-add-a-database.md).

## <a name="change-the-seeding-mode-of-a-replica"></a>Modificare la modalità di seeding di una replica

La modalità di seeding di una replica può essere modificata dopo la creazione del gruppo di disponibilità, pertanto il seeding automatico può essere abilitato o disabilitato. Abilitando il seeding automatico dopo la creazione consente a un database di essere aggiunto al gruppo di disponibilità con il seeding automatico, se è stato creato con le operazioni di backup, copia e ripristino. Esempio:

```
ALTER AVAILABILITY GROUP [AGName]
  MODIFY REPLICA ON 'Replica_Name'
  WITH (SEEDING_MODE = AUTOMATIC)
```

Per disabilitare il seeding automatico, usare il valore MANUAL.

## <a name="prevent-automatic-seeding-after-an-availability-group-is-created"></a>Impedire il seeding automatico dopo la creazione di un gruppo di disponibilità

Se non si vuole disabilitare completamente il seeding automatico per una replica secondaria, ma si vuole impedire temporaneamente alla replica secondaria di creare automaticamente i database, è possibile negare l'autorizzazione CREATE al gruppo di disponibilità. Ciò avviene quando un nuovo database viene aggiunto al gruppo di disponibilità, ma il gruppo di disponibilità non deve poter creare il database in una replica secondaria.

```
ALTER AVAILABILITY GROUP [AGName] DENY CREATE ANY DATABASE
GO
```

## <a name="monitor-automatic-seeding"></a>Monitorare il seeding automatico

Sono disponibili quattro modi per monitorare e risolvere i problemi del seeding automatico:

* [Log di SQL Server](#sql-server-log) come già descritto
* [DMV](#dynamic-management-views)
* [Tabelle di cronologia di backup](#backup-history-tables)
* [Eventi estesi](#extended-events)

### <a name="dynamic-management-views"></a>DMV

Sono disponibili due DMV (viste a gestione dinamica) per il monitoraggio del seeding: sys.dm_hadr_automatic_seeding e sys.dm_hadr_physical_seeding_stats.

* sys.dm_hadr_automatic_seeding contiene lo stato generale del seeding automatico e mantiene la cronologia di ogni esecuzione (indipendentemente se ha esito positivo o meno). La colonna current_state conterrà il valore COMPLETED o FAILED. Se il valore è FAILED, usare il valore in failure_state_desc per la diagnosi del problema. Potrebbe essere necessario usare sia questo valore che quello riportato nel [Log di SQL Server](#sql-server-log) per stabilire la causa dell'errore. Questa DMV viene popolata nella replica primaria e in tutte le repliche secondarie.

* sys.dm_hadr_physical_seeding_stats mostra lo stato dell'operazione di seeding automatico quando è in esecuzione. Analogamente a sys.dm_hadr_automatic_seeding questa DMV mostrerà i valori sia per la replica primaria che per quelle secondarie, ma questa cronologia non viene archiviata. I valori sono per solo l'esecuzione corrente e non verranno mantenuti. Le colonne di interesse includono start_time_utc, end_time_utc, estimate_time_complete_utc, total_disk_io_wait_time_ms, total_network_wait_time_ms e, se l'operazione di seeding non riesce, failure_message.

### <a name="backup-history-tables"></a>Tabelle di cronologia di backup

Il seeding automatico inserisce inoltre le voci nelle tabelle `msdb` in cui viene archiviata la cronologia di backup e ripristini. Nella replica secondaria che riceve il seeding automatico, la colonna physical_device_name della tabella `backupmediafamily` contiene un GUID per il relativo valore e la voce corrispondente in `backupset` contiene il nome della replica primaria per server_name e machine_name.

### <a name="extended-events"></a>Eventi estesi

Il seeding automatico aggiunge nuovi eventi estesi per tenere traccia delle modifiche allo stato, degli errori e delle statistiche sulle prestazioni durante l'inizializzazione.
Ad esempio, lo script seguente crea una sessione di eventi estesi che acquisisce gli eventi correlati al seeding automatico.

```
CREATE EVENT SESSION [AG_autoseed] ON SERVER 
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

La tabella seguente elenca gli eventi estesi correlati al seeding automatico.

|Nome|Descrizione|
|----|-----------|
|hadr_db_manager_seeding_request_msg|Messaggio di richiesta di seeding.|
|hadr_physical_seeding_backup_state_change|Modifica dello stato lato backup del seed fisico.|
|hadr_physical_seeding_restore_state_change|Modifica dello stato lato ripristino del seed fisico.|
|hadr_physical_seeding_forwarder_state_change|Modifica dello stato lato server di inoltro del seed fisico.|
|hadr_physical_seeding_forwarder_target_state_change|Modifica dello stato lato destinazione del server di inoltro del seed fisico.|
|hadr_physical_seeding_submit_callback|Evento di callback invio del seed fisico.|
|hadr_physical_seeding_failure|Evento di errore del seed fisico.|
|hadr_physical_seeding_progress|Evento di stato del seed fisico.|
|hadr_physical_seeding_schedule_long_task_failure|Evento di errore per attività di lunga durata della pianificazione per il seed fisico.|
|hadr_automatic_seeding_start|Si verifica quando viene inviata un'operazione di seeding automatico.|
|hadr_automatic_seeding_state_transition|Si verifica quando cambia lo stato di un'operazione di seeding automatico.|
|hadr_automatic_seeding_success|Si verifica quando un'operazione di seeding automatico riesce.|
|hadr_automatic_seeding_failure|Si verifica quando un'operazione di seeding automatico non riesce.|
|hadr_automatic_seeding_timeout|Si verifica in caso di timeout di un'operazione di seeding automatico.|

## <a name="see-also"></a>Vedere anche

[ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)

[CREATE AVAILABILITY GROUP (Transact-SQL)](https://msdn.microsoft.com/library/ff878399.aspx)

[Guida alla risoluzione dei problemi e al monitoraggio dei gruppi di disponibilità Always On](http://technet.microsoft.com/library/dn135328.aspx)

> Il contenuto di questo articolo è stato scritto da [Allan Hirt](http://mvp.microsoft.com/en-us/PublicProfile/4025254?fullName=Allan%20Hirt), Microsoft Most Valued Professional.

<!--Image references-->
[1]: ./media/auto-seed-new-availability-group.png
[2]: ./media/auto-seed-sql-server-log.png

