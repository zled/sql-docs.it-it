---
title: Creare il Database di gestione temporanea per Parallel Data Warehouse
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: SQL Server Parallel Data Warehouse (PDW) utilizza un database di gestione temporanea per archiviare i dati durante il processo di caricamento.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 6d0b2726-4772-4858-b700-885cc12219b2
caps.latest.revision: "20"
ms.openlocfilehash: f88e2c45aaed8b6f2b3bfb6fe610a0f228c4449e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="staging-database"></a>Database di gestione temporanea 
SQL Server Parallel Data Warehouse (PDW) utilizza un database di gestione temporanea per archiviare i dati durante il processo di caricamento. Per impostazione predefinita, SQL Server PDW utilizza il database di destinazione come database di gestione temporanea che può provocare la frammentazione di tabella. Per ridurre la frammentazione della tabella, è possibile creare un database di gestione temporanea definita dall'utente. In alternativa, quando il rollback di un errore di caricamento non è un problema, è possibile utilizzare la modalità di caricamento di fastappend per migliorare le prestazioni ignorando la tabella temporanea e caricamento direttamente nella tabella di destinazione.  
  
## <a name="StagingDatabase"></a>Nozioni fondamentali sui database di gestione temporanea  
Oggetto *database di gestione temporanea* è un database PDW creati dall'utente che archivia i dati temporaneamente, mentre viene caricato nel dispositivo. Quando per un carico viene specificato un database di gestione temporanea, il dispositivo prima copia i dati al database di gestione temporanea e quindi copia dei dati dalle tabelle temporanee nel database di gestione temporanea alle tabelle permanenti nel database di destinazione.  
  
Quando un database di gestione temporanea non è specificato per un carico, ServerPDW SQL crea le tabelle temporanee nel database di destinazione e li utilizza per archiviare i dati caricati prima di inserire i dati caricati nelle tabelle di destinazione permanente.  
  
Quando viene utilizzato un carico di *modalità fastappend*, ServerPDW SQL ignora completamente l'utilizzo di tabelle temporanee e aggiunge i dati direttamente alla tabella di destinazione. La modalità fastappend migliora le prestazioni di caricamento per gli scenari ELT dove vengono caricati i dati in una tabella che è una tabella temporanea dal punto di vista dell'applicazione. Ad esempio, un processo ELT Impossibile caricare i dati in una tabella temporanea, elaborare i dati dalla pulizia e la deallocazione duping e quindi inserire i dati nella tabella dei fatti di destinazione. In questo caso, non è necessario per PDW da caricare per prima i dati in una tabella temporanea interna prima di inserire i dati nella tabella temporanea dell'applicazione. La modalità fastappend evita il passaggio di carico aggiuntivo, che migliora notevolmente le prestazioni del carico. Si noti che per utilizzare la modalità fastappend, è necessario utilizzare modalità multi-transazione, il che significa che il ripristino da un carico interrotto o non deve essere gestito dal proprio processo di caricamento.  
  
**Vantaggi di database di gestione temporanea**  
  
Il vantaggio principale di un database di gestione temporanea è per ridurre la frammentazione della tabella. Se non viene utilizzato un database di gestione temporanea, i dati vengono caricati in tabelle temporanee nel database di destinazione. Quando le tabelle temporanee ottengano vengono create ed eliminate nel database di destinazione, le pagine per le tabelle temporanee e tabelle permanenti diventano interleave. Nel corso del tempo, provocando la frammentazione di tabella e comporta una riduzione delle prestazioni. Al contrario, un database di gestione temporanea assicura che le tabelle temporanee vengono create ed eliminate in uno spazio di file distinto rispetto a tabelle permanenti.  
  
**Strutture di tabelle di database di gestione temporanea**  
  
La struttura di archiviazione per ogni tabella di database dipende dalla tabella di destinazione.  
  
-   Per i caricamenti in un heap o un indice columnstore cluster, la tabella di gestione temporanea è un heap.  
  
-   Per i caricamenti in un indice cluster rowstore, tabella di gestione temporanea è un indice rowstore cluster.  
  
## <a name="Permissions"></a>Permissions  
Richiede l'autorizzazione di creazione (per la creazione di una tabella temporanea) nel database di gestione temporanea. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Procedure consigliate per la creazione di un database di gestione temporanea  
  
1.  Deve essere presente solo un database di gestione temporanea per dispositivo. Questo può essere condiviso da tutti i processi di caricamento per tutti i database di destinazione.  
  
2.  La dimensione del database di gestione temporanea è specifico del cliente. Inizialmente, durante il popolamento prima il dispositivo, il database di gestione temporanea deve essere grande abbastanza da contenere i processi di caricamento iniziale. Questi caricare i processi tendono a essere di grandi dimensioni perché più caricamenti possono venire generati contemporaneamente. Dopo aver completato i processi di caricamento iniziale e il sistema è in produzione, le dimensioni di ogni processo di caricamento sono probabile che siano di dimensioni ridotte. In questo caso, è possibile ridurre le dimensioni del database di gestione temporanea per supportare il carico alle dimensioni minori. Per ridurre le dimensioni, è possibile eliminare il database di gestione temporanea e crearlo nuovamente con allocazioni di dimensioni inferiori, oppure è possibile utilizzare il [ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md) istruzione.  
  
    Quando si crea il database di gestione temporanea, utilizzare le linee guida seguenti.  
  
    -   Le dimensioni della tabella replicata devono essere la dimensione stimata, per ogni nodo di calcolo, di tutte le tabelle replicate che verranno caricati contemporaneamente. Si tratta in genere 25-30 GB.  
  
    -   Le dimensioni della tabella distribuita devono essere la dimensione stimata, per ogni dispositivo, di tutte le tabelle distribuite che verranno caricati contemporaneamente.  
  
    -   Le dimensioni del log sono in genere è simile a quella tabella replicata.  
  
## <a name="Examples"></a>Esempi  
  
### <a name="a-create-a-staging-database"></a>A. Creare un database di gestione temporanea 
L'esempio seguente crea un database di gestione temporanea, Stagedb, per l'utilizzo con tutti i carichi nel dispositivo. Si supponga che si prevede che cinque tabelle replicate al fine di dimensioni caricherà contemporaneamente 5 GB. Ciò comporta l'allocazione di almeno 25 GB per le dimensioni della replica. Si supponga che si prevede che sei distribuito di tabelle di dimensioni 100, 200, 400, 500, 500 e 550 GB caricherà contemporaneamente. Ciò comporta l'allocazione di almeno 2 250 GB per le dimensioni della tabella distribuita.  
  
```sql  
CREATE DATABASE Stagedb  
WITH (  
  
    AUTOGROW = ON,  
  
    REPLICATED_SIZE = 25 GB,  
  
    DISTRIBUTED_SIZE = 2250 GB,  
  
    LOG_SIZE = 25 GB  
  
);  
```  

<!-- MISSING LINKS
 
## See Also  
[Common metadata query examples](metadata-query-examples.md)  

-->
  
