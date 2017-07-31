---
title: "Funzionalità di SQL Server non supportate per OLTP in memoria | Microsoft Docs"
ms.custom: 
ms.date: 07/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
caps.latest.revision: 55
author: MightyPen
ms.author: genemi
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: cf8509cab2424529ca0ed16c936fa63a139dfca4
ms.openlocfilehash: 85a720edefe425146e5c54613b0a0f88007765a9
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="unsupported-sql-server-features-for-in-memory-oltp"></a>Funzionalità di SQL Server non supportate per OLTP in memoria
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Questo argomento illustra le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supportate per l'uso con oggetti con ottimizzazione per la memoria.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funzionalità non supportate per OLTP in memoria  

Le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indicate di seguito non sono supportate in un database contenente oggetti con ottimizzazione per la memoria, incluso un filegroup di dati con ottimizzazione per la memoria.  

  
|Funzionalità non supportata|Descrizione della funzionalità|  
|-------------------------|-------------------------|  
|Compressione dei dati per tabelle con ottimizzazione per la memoria.|È possibile utilizzare la funzionalità di compressione dei dati per comprimere i dati in un database e ridurre le dimensioni del database. Per altre informazioni, vedere [Data Compression](../../relational-databases/data-compression/data-compression.md).|  
|Partizionamento di tabelle con ottimizzazione per la memoria, di indici HASH e di indici non cluster.|I dati di tabelle e indici partizionati vengono divisi in unità distribuibili tra più filegroup in un database. Per altre informazioni, vedere [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).|  
| Replica | Le configurazioni di replica diverse dalla replica transazionale in tabelle con ottimizzazione della memoria nei sottoscrittori non sono compatibili con tabelle o viste che fanno riferimento a tabelle con ottimizzazione per la memoria.<br /><br />Se è presente un filegroup con ottimizzazione per la memoria, la replica con sync_mode="snapshot del database" non è supportata.<br /><br />Per altre informazioni, vedere [Replica in sottoscrittori di tabelle con ottimizzazione per la memoria](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).|
|Mirroring|Il mirroring del database non è supportato per i database con un filegroup MEMORY_OPTIMIZED_DATA. Per altre informazioni sul mirroring, vedere [Mirroring del Database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).|  
|Ricompilazione del log|La ricompilazione del log, tramite il comando attach o l'istruzione ALTER DATABASE, non è supportata per i database che contengono un filegroup MEMORY_OPTIMIZED_DATA.|  
|Server collegato|Non è possibile accedere a server collegati nella stessa query o transazione come tabelle con ottimizzazione per la memoria. Per altre informazioni, vedere [Server collegati &#40;Motore di database&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).|  
|Registrazione bulk|Indipendentemente dal modello di recupero del database, tutte le operazioni nelle tabelle durevoli con ottimizzazione per la memoria vengono sempre registrate completamente.|  
|Registrazione minima|La registrazione minima non è supportata dalle tabelle con ottimizzazione per la memoria. Per altre informazioni sulla registrazione minima, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md) e [Prerequisiti per la registrazione minima nell'importazione in blocco](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).|  
|Rilevamento modifiche|È possibile abilitare il rilevamento delle modifiche in un database con oggetti di OLTP in memoria, tuttavia le modifiche nelle tabelle con ottimizzazione per la memoria non vengono rilevate.|  
| trigger DDL | I trigger DDL a livello di database e di server non sono supportati con le tabelle di OLTP in memoria né con i moduli compilati in modo nativo. |  
| Change Data Capture (CDC) | CDC non può essere usato con un database che contiene tabelle con ottimizzazione per la memoria perché usa internamente un trigger DDL per DROP TABLE. |  
| Modalità fiber | La modalità fiber non è supportata con le tabelle con ottimizzazione per la memoria:<br /><br />Se la modalità fiber è attiva, non è possibile creare database con filegroup con ottimizzazione per la memoria o aggiungere filegroup con ottimizzazione per la memoria a database esistenti.<br /><br />È possibile abilitare la modalità fiber se sono presenti database con filegroup con ottimizzazione per la memoria. Tuttavia, l'abilitazione della modalità fiber richiede il riavvio del server. In quella situazione il recupero dei database con filegroup con ottimizzazione per la memoria avrà esito negativo. Verrà quindi visualizzato un messaggio di errore che suggerisce di disabilitare la modalità fiber per usare i database con i filegroup con ottimizzazione per la memoria.<br /><br />Se è attiva la modalità fiber, non sarà possibile allegare e ripristinare un database con filegroup con ottimizzazione per la memoria. Il database verrà contrassegnato come sospetto.<br /><br />Per altre informazioni, vedere [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md). |  
|Limitazione di Service Broker|Non è possibile accedere a una coda da una stored procedure compilata in modo nativo,<br /><br /> né a una coda in un database remoto in una transazione che accede a tabelle con ottimizzazione per la memoria.|  
|Replica nei sottoscrittori|La replica transazionale in tabelle con ottimizzazione per la memoria nei sottoscrittori è supportata con alcune restrizioni. Per altre informazioni, vedere [Replica in sottoscrittori di tabelle con ottimizzazione per la memoria](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)|  


#### <a name="cross-database-queries-and-transcations"></a>Query e transazioni tra database

Salvo alcune eccezioni, le transazioni tra database non sono supportate. Nella tabella seguente vengono descritti i casi supportati e le relative restrizioni. Vedere anche [Query tra database](../../relational-databases/in-memory-oltp/cross-database-queries.md).  


|Database|Allowed|Description|  
|---------------|-------------|-----------------|  
| Database utente, **modello** e **msdb**. | No | Nella maggior parte dei casi, query e transazioni tra database *non* sono supportate.<br /><br />Una query non è in grado di accedere ad altri database se usa una tabella con ottimizzazione per la memoria o una stored procedure compilata in modo nativo. Questa restrizione si applica sia alle transazioni che alle query.<br /><br />Le eccezioni sono i database di sistema **tempdb** e **master**. In questo caso il database **master** è disponibile per l'accesso in sola lettura. |
| Database delle **risorse**, **tempdb** | Sì | In una transazione che coinvolge gli oggetti di OLTP In memoria, i database di sistema **risorse** e **tempdb** possono essere usati senza alcuna restrizione aggiuntiva.


## <a name="scenarios-not-supported"></a>Scenari non supportati  
  
- Accesso a tabelle con ottimizzazione per la memoria usando la connessione del contesto dall'interno di stored procedure CLR.  
  
- Keyset e cursori dinamici sulle query che accedono a tabelle con ottimizzazione per la memoria. Questi cursori diventano statici e di sola lettura.  
  
- L'uso di **MERGE INTO** *target*, dove *target* è una tabella con ottimizzazione per la memoria, non è supportato.
    - **MERGE USING** *source* è supportato per le tabelle con ottimizzazione per la memoria.  
  
- Il tipo di dati ROWVERSION (TIMESTAMP) non è supportato. Per altre informazioni, vedere [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).
  
- L'opzione di chiusura automatica non è supportata con i database che contengono un filegroup MEMORY_OPTIMIZED_DATA  
  
- Gli snapshot del database non sono supportati per i database che contengono un filegroup MEMORY_OPTIMIZED_DATA.  
  
- La DDL transazionale, ad esempio le istruzioni CREATE/ALTER/DROP degli oggetti OLTP in memoria, non è supportata nelle transazioni utente.  
  
- Notifica degli eventi.  
  
- Gestione basata su criteri.
    - Le modalità "impedisci esecuzione" e "solo log" della funzionalità di gestione basata su criteri non sono supportate. La presenza di tali criteri nel server può impedire la corretta esecuzione della DDL di OLTP in memoria. Le modalità Su richiesta e Su pianificazione sono supportate.  

- L'indipendenza del database ([Database indipendenti](../../relational-databases/databases/contained-databases.md)) non è supportata con OLTP in memoria.
    - L'autenticazione di database indipendenti è supportata, Tuttavia, tutti gli oggetti OLTP in memoria sono contrassegnati come entità che interrompono il contenimento nella vista a gestione dinamica (DMV) **dm_db_uncontained_entities**.

  
## <a name="see-also"></a>Vedere anche  

- [Supporto di SQL Server per OLTP in memoria](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)

