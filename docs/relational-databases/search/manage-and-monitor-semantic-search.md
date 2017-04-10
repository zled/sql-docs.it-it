---
title: "Gestire e monitorare la ricerca semantica | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ricerca semantica [SQL Server], gestione"
  - "ricerca semantica [SQL Server], monitoraggio"
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Gestire e monitorare la ricerca semantica
  Vengono illustrati il processo di indicizzazione semantica e le attività correlate alla gestione e al monitoraggio degli indici.  
  
##  <a name="HowToMonitorStatus"></a> Procedura: Monitoraggio dello stato dell'indicizzazione semantica  
 **Verifica del completamento della prima fase dell'indicizzazione semantica**  
 Eseguire una query sulla DMV [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md) e verificare lo **stato** e le colonne **status_description**.  
  
 La prima fase dell'indicizzazione include il popolamento dell'indice di parole chiave full-text e dell'indice di frasi chiave semantico, nonché l'estrazione dei dati di somiglianza dei documenti.  
  
```tsql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Verifica del completamento della seconda fase dell'indicizzazione semantica**  
 Eseguire una query sulla DMV [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md) e verificare lo **stato** e le colonne **status_description**.  
  
 La seconda fase dell'indicizzazione include il popolamento dell'indice di somiglianza dei documenti semantico.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="HowToCheckSize"></a> Procedura: Verificare le dimensioni degli indici semantici  
 **Individuazione della dimensione logica di un indice di frasi chiave semantico o di un indice di somiglianza dei documenti semantico**  
 Eseguire una query sulla DMV [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md).  
  
 La dimensione logica viene visualizzata in numero di pagine di indice.  
  
```tsql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Individuazione delle dimensioni totali degli indici full-text e semantici per un catalogo full-text**  
 Eseguire una query sulla proprietà **IndexSize** della funzione per i metadati [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).  
  
```tsql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 **Individuazione del numero di elementi indicizzati negli indici full-text e semantico per un catalogo full-text**  
 Eseguire una query sulla proprietà **ItemCount** della funzione per i metadati [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).  
  
```tsql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="HowToForcePopulation"></a> Procedura: Forzare il popolamento degli indici semantici  
 È possibile forzare il popolamento degli indici full-text e semantici utilizzando la clausola START/STOP/PAUSE o RESUME POPULATION con la stessa sintassi e lo stesso comportamento descritti per gli indici full-text. Per altre informazioni, vedere [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md) e [Popolamento degli indici full-texts](../../relational-databases/search/populate-full-text-indexes.md).  
  
 Poiché l'indicizzazione semantica dipende dall'indicizzazione full-text, gli indici semantici vengono popolati solo al popolamento degli indici full-text associati.  
  
 **Esempio: Avviare un popolamento completo di indici full-text e semantici**  
  
 Nell'esempio seguente viene avviato il popolamento completo degli indici semantici e full-text mediante la modifica di un indice full-text esistente nella tabella **Production.Document** del database di esempio AdventureWorks2012.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="HowToDisableIndexing"></a> Procedura: Disabilitare o riabilitare l'indicizzazione semantica  
 È possibile abilitare o disabilitare l'indicizzazione full-text o semantica utilizzando la clausola ENABLE/DISABLE con la stessa sintassi e lo stesso comportamento descritti per gli indici full-text. Per altre informazioni, vedere [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
 Quando l'indicizzazione semantica è disabilitata e sospesa, le query sui dati semantici continuano a funzionare correttamente e a restituire dati precedentemente indicizzati. Questo comportamento non è coerente con quello della ricerca full-text.  
  
```tsql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="SemanticIndexing"></a> Fasi di indicizzazione semantica  
 Tramite la ricerca semantica vengono indicizzati due tipi di dati per ogni colonna in cui è abilitata:  
  
1.  **Frasi chiave**  
  
2.  **Somiglianza dei documenti**  
  
 L'indicizzazione semantica viene eseguita in due fasi, insieme all'indicizzazione full-text:  
  
1.  **Fase 1**. L'indice delle parole chiave full-text e l'indice delle frasi chiave semantico vengono popolati in parallelo. In questa fase vengono anche estratti i dati necessari per indicizzare la somiglianza dei documenti.  
  
2.  **Fase 2**. Viene quindi popolato l'indice di somiglianza dei documenti semantico. Questo indice dipende da entrambi gli indici popolati nella fase precedente.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="ProblemNotPopulated"></a> Problema: gli indici semantici non vengono popolati  
 **Verificare se gli indici full-text associati sono stati popolati.**  
 Poiché l'indicizzazione semantica dipende dall'indicizzazione full-text, gli indici semantici vengono popolati solo al popolamento degli indici full-text associati.  
  
 **Verificare se la ricerca full-text e la ricerca semantica sono state installate e configurate correttamente.**  
 Per altre informazioni, vedere [Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
 **Controllare se il servizio FDHOST è disponibile o se si è verificata un'altra condizione che provoca la mancata esecuzione dell'indicizzazione full-text.**  
 Per altre informazioni, vedere [Risoluzione dei problemi nell'indicizzazione full-text](../../relational-databases/search/troubleshoot-full-text-indexing.md).  
  
  