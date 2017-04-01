---
title: "Gruppi di disponibilit&#224; distribuiti (gruppi di disponibilit&#224; AlwaysOn) | Microsoft Docs"
ms.custom: ""
ms.date: "08/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 28
---
# Gruppi di disponibilit&#224; distribuiti (gruppi di disponibilit&#224; AlwaysOn)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  I gruppi di disponibilità distribuiti consentono di associare due gruppi di disponibilità che si trovano in cluster di failover di Windows Server (WSFC) diversi. Uno degli usi principali dei gruppi di disponibilità distribuiti è il ripristino di emergenza in cui il sito primario è dislocato in diverse località geografiche rispetto al sito di ripristino di emergenza. Si desidera che i dati vengano replicati continuamente nel sito di ripristino di emergenza, ma non si vuole che un potenziale problema di rete o del sito di ripristino di emergenza arresti il sito primario.  
  
 Il diagramma seguente illustra l'architettura di un gruppo di disponibilità distribuito.  
  
 ![AlwaysOn Distributed Availability Groups](../../../database-engine/availability-groups/windows/media/alwayson-distributed-availability-groups.png "AlwaysOn Distributed Availability Groups")  
  
 Nel diagramma precedente sono presenti due cluster di failover di Windows Server (WFSC 1 e WFSC 2). Ogni cluster dispone del proprio gruppo di disponibilità con configurazione corrispondente di database. Un gruppo di disponibilità distribuito può essere considerato come un "gruppo di disponibilità di gruppi di disponibilità". In questo esempio AG 1 diventa il gruppo di disponibilità primario. Gli inserimenti e gli aggiornamenti vengono tutti eseguiti sulla replica primaria, AG 1, quindi vengono replicati nelle relative repliche secondarie. Ma anche le modifiche vengono replicate, una volta in rete, nel gruppo di disponibilità secondario su WSFC 2. Il gruppo di disponibilità AG 2 replica le modifiche nelle sue repliche secondarie.  
  
> [!IMPORTANT]  
>  Quando viene stabilita una relazione di gruppo di disponibilità distribuito tra due gruppi di disponibilità, il gruppo di disponibilità secondario diventa automaticamente di sola lettura. È possibile apportare aggiornamenti e inserimenti solo alla replica primaria del gruppo di disponibilità primario (in questo esempio la replica primaria di AG 1).  
  
 I gruppi di disponibilità distribuiti differiscono da un gruppo di disponibilità in un singolo cluster di failover di Windows Server nei modi seguenti:  
  
-   Ogni WSFC mantiene la propria modalità quorum e configurazione di voto dei nodi. Ciò significa che lo stato del WSFC secondario non influisce sul WSFC primario.  
  
-   I dati vengono inviati una volta in rete al WSFC secondario e quindi replicati all'interno di tale cluster. In un WSFC singolo i dati vengono inviati singolarmente a ogni replica. I gruppi di disponibilità distribuiti sono più efficienti per siti secondari dislocati in diverse località geografiche.  
  
-   La versione del sistema operativo usata nei cluster primario e secondario può differire. I server di un WSFC singolo devono tutti eseguire la stessa versione del sistema operativo. Ciò consente potenzialmente di usare gruppi di disponibilità distribuiti con aggiornamenti in sequenza del sistema operativo.  
  
-   I gruppi di disponibilità primario e secondario devono presentare la stessa configurazione di database.  
  
-   Il failover automatico sul gruppo di disponibilità secondario non è supportato.  
  
## Creare un gruppo di disponibilità distribuito  
 Per creare un gruppo di disponibilità distribuito, è necessario creare un gruppo di disponibilità e listener in ogni WSFC. È quindi possibile combinarli in un gruppo di disponibilità distribuito. La procedura seguente illustra un esempio di base in Transact-SQL. Questo esempio non descrive in dettaglio la creazione dei gruppi di disponibilità e listener, ma mette in rilievo i requisiti principali.  
  
### Creare il gruppo di disponibilità primario nel primo cluster  
 Creare un gruppo di disponibilità nel primo WSFC.   In questo esempio il gruppo di disponibilità è denominato `ag1` per il database `db1`.  
  
```tsql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
 In questo esempio viene usato il seeding diretto, dove **SEEDING_MODE** è impostato su **AUTOMATIC** per le repliche e il gruppo di disponibilità distribuito. Dopo aver stabilito questa impostazione, le repliche secondarie e il gruppo di disponibilità secondario vengono popolati automaticamente senza richiedere un backup e ripristino manuale del database primario.  
  
### Creare un join delle repliche secondarie al gruppo di disponibilità primario  
 È necessario creare un join tra tutte le repliche secondarie al gruppo di disponibilità tramite **ALTER AVAILABILITY GROUP** con l'opzione **JOIN** . Dal momento che in questo esempio viene usato il seeding diretto, è necessario chiamare anche  **ALTER AVAILABILITY GROUP** con l'opzione **GRANT CREATE ANY DATABASE** . In questo modo il gruppo di disponibilità può creare il database e avviare il seeding automatico dalla replica primaria.  
  
 In questo esempio i seguenti comandi vengono eseguiti sulla replica secondaria, `server2`, per creare un join del gruppo di disponibilità `ag1` . Il gruppo di disponibilità può quindi creare database sulla replica secondaria.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Creare un listener per il gruppo di disponibilità primario  
 Successivamente aggiungere un listener per il gruppo di disponibilità primario sul primo WSFC. In questo esempio il listener viene denominato `ag1-listener`. Per istruzioni dettagliate sulla creazione di un listener, vedere [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Creare il gruppo di disponibilità secondario nel secondo cluster  
 Creare quindi un secondo gruppo di disponibilità, `ag2`, nel secondo WSFC. In questo caso il database non è specificato, perché verrà eseguito il seeding automatico del database stesso dal gruppo di disponibilità primario.  
  
```tsql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
>  Si noti che il gruppo di disponibilità secondario deve usare lo stesso endpoint del mirroring del database (in questo esempio la porta 5022). In caso contrario, la replica verrà interrotta dopo un failover locale.  
  
### Creare un join delle repliche secondarie al gruppo di disponibilità secondario  
 In questo esempio i seguenti comandi vengono eseguiti sulla replica secondaria, `server4`, per creare un join del gruppo di disponibilità `ag2` . Il gruppo di disponibilità può quindi creare database sulla replica secondaria per supportare il seeding diretto.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### Creare un listener per il gruppo di disponibilità secondario  
 Successivamente aggiungere un listener per il gruppo di disponibilità secondario sul secondo WSFC. In questo esempio il listener viene denominato `ag2-listener`. Per istruzioni dettagliate sulla creazione di un listener, vedere [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### Creare il gruppo di disponibilità distribuito nel primo cluster  
 Creare un gruppo di disponibilità distribuito nel primo WSFC (in questo esempio denominato `distributedag`). Usare il comando **CREATE AVAILABILITY GROUP** con l'opzione **DISTRIBUTED** . Il parametro **AVAILABILITY GROUP ON** specifica i gruppi di disponibilità membri, `ag1` e `ag2`.  
  
```tsql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  Il parametro **LISTENER_URL** specifica il listener per ogni gruppo di disponibilità insieme all'endpoint del mirroring del database del gruppo di disponibilità. Questo esempio riguarda la porta `5022` (non la porta `60173` usata per creare il listener).  
  
### Creare un join del gruppo di disponibilità distribuito nel secondo cluster  
 Creare quindi un join del gruppo di disponibilità distribuito nel secondo WSFC.  
  
```tsql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

  
## Failover su un gruppo di disponibilità secondario  
 In questo momento è supportato solo il failover manuale. L'istruzione Transact-SQL seguente forza il failover sul gruppo di disponibilità distribuito denominato `distributedag`:  


1. Impostare la modalità di disponibilità sul commit sincrono per il gruppo di disponibilità secondaria. 
    
      ```tsql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH  
         ( 
          LISTENER_URL = 'tcp://ag1-listener:5022',  
          AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
  
1. Attendere che lo stato del gruppo di disponibilità distribuito diventi `SYNCHRONIZED`. Eseguire la query seguente nell'istanza di SQL Server che ospita la replica primaria del gruppo di disponibilità primario. 
    
      ```tsql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    Continuare dopo che il gruppo di disponibilità **synchronization_state_desc** diventa `SYNCHRONIZED`. Se **synchronization_state_desc** non è `SYNCHRONIZED`, eseguire il comando ogni cinque secondi fino a quando non viene modificato. Non continuare fino a **synchronization_state_desc** = `SYNCHRONIZED`. 

1. Nell'istanza di SQL Server che ospita la replica primaria del gruppo di disponibilità primario, impostare il ruolo del gruppo di disponibilità distribuito su `SECONDARY`. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
      ```  

    Nota: a questo punto, il gruppo di disponibilità distribuito non è disponibile.

1. Verificare la conformità del failover. Eseguire la query riportata di seguito:

      ```tsql
      SELECT ag.name, 
             drs.database_id, 
             drs.group_id, 
             drs.replica_id, 
             drs.synchronization_state_desc, 
             drs.end_of_log_lsn 
      FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
      WHERE drs.group_id = ag.group_id; 
      ```  
    Il gruppo di disponibilità è pronto per il failover quando **synchronization_state_desc** è `SYNCHRONIZED` e **end_of_log_lsn** è lo stesso per entrambi i gruppi di disponibilità. 

1. Failover dal gruppo di disponibilità primaria al gruppo di disponibilità secondaria. Eseguire il comando seguente nell'istanza di SQL Server che ospita la replica primaria del gruppo di disponibilità secondario. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
      ```  
      Nota: dopo questo passaggio, il gruppo di disponibilità distribuito sarà disponibile.
      
Dopo aver completato i passaggi precedenti, si verifica il failover del gruppo di disponibilità distribuito senza perdita di dati. Microsoft consiglia di riportare la modalità di disponibilità su ASYNCHRONOUS_COMMIT se i gruppi di disponibilità si trovano a una distanza geografica che ne determina la latenza. 
  
## Rimuovere un gruppo di disponibilità distribuito  
 L'istruzione Transact-SQL seguente rimuove un gruppo di disponibilità distribuito denominato `distributedag`:  
  
```tsql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## Creare un gruppo di disponibilità distribuito con istanze del cluster di failover

È possibile creare un gruppo di disponibilità distribuito usando un gruppo di disponibilità in un'istanza del cluster di failover. In questo caso, non è necessario un listener del gruppo di disponibilità. Usare il nome di rete virtuale (VNN) per la replica primaria dell'istanza FCI. L'esempio seguente illustra un gruppo di disponibilità distribuito denominato SQLFCIDAG. Un gruppo di disponibilità è SQLFCIAG. SQLFCIAG ha 2 repliche FCI. Il nome di rete virtuale per la replica primaria FCI è SQLFCIAG-1 e il nome di rete virtuale per la replica FCI secondaria è SQLFCIAG-2. Il gruppo di disponibilità distribuito include anche SQLAG-DR, per il ripristino di emergenza.

![Gruppo di disponibilità AlwaysOn distribuito](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 Il DDL seguente crea questo gruppo di disponibilità distribuito. 

```tsql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

Si noti che l'URL del listener è il nome di rete virtuale dell'istanza FCI primaria.

## Eseguire il failover manuale di FCI in un gruppo di disponibilità distribuito

Per eseguire manualmente il failover del gruppo di disponibilità FCI, aggiornare il gruppo di disponibilità distribuito in modo da riflettere la modifica dell'URL del listener. Ad esempio, eseguire il DDL seguente sul gruppo di disponibilità primaria e il gruppo di disponibilità secondaria di SQLFCIAG:

```tsql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2:5022'
    )
```  
  
## Vedere anche  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  