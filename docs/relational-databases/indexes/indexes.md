---
title: "Indici | Microsoft Docs"
ms.custom: ""
ms.date: "11/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di indice [SQL Server]"
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Indici
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Nella tabella seguente sono inclusi i tipi di indici disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i collegamenti a ulteriori informazioni.  
  
|Tipo di indice|Descrizione|Informazioni aggiuntive|  
|----------------|-----------------|----------------------------|  
|Hash|Con un indice hash l'accesso ai dati viene eseguito tramite una tabella hash in memoria. Gli indici hash utilizzano una quantità di memoria fissa (una funzione del numero di bucket).|[Linee guida per l'utilizzo di indici nelle tabelle con ottimizzazione per la memoria](../Topic/Guidelines%20for%20Using%20Indexes%20on%20Memory-Optimized%20Tables.md)|  
|Indici non cluster con ottimizzazione per la memoria|Per gli indici non cluster con ottimizzazione per la memoria, l'utilizzo della memoria è una funzione del conteggio delle righe e della dimensione delle colonne chiave di indice|[Linee guida per l'utilizzo di indici nelle tabelle con ottimizzazione per la memoria](../Topic/Guidelines%20for%20Using%20Indexes%20on%20Memory-Optimized%20Tables.md)|  
|Cluster|Un indice cluster ordina e archivia le righe di dati della tabella o della vista in base alle chiavi di indice cluster. L'indice cluster viene implementato come albero B che supporta il recupero rapido delle righe in base ai rispettivi valori delle chiavi di indice cluster.|[Descrizione di indici cluster e non cluster.](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Creare indici cluster](../../relational-databases/indexes/create-clustered-indexes.md)|  
|Non cluster|Un indice non cluster può essere definito in una tabella o vista con un indice cluster o in un heap. Ogni riga di indice nell'indice non cluster contiene il valore della chiave non cluster e un indicatore di posizione delle righe. Questo indicatore punta alla riga di dati nell'indice cluster o nell'heap contenente il valore della chiave. Le righe dell'indice vengono archiviate in base all'ordine dei valori delle chiavi di indice, ma non è possibile garantire che le righe di dati abbiano un ordine specifico, a meno che nella tabella non venga creato un indice cluster.|[Descrizione di indici cluster e non cluster.](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Creare indici non cluster](../../relational-databases/indexes/create-nonclustered-indexes.md)|  
|Univoco|Un indice univoco garantisce che la chiave di indice non contenga alcun valore duplicato e che pertanto ogni riga della tabella o della vista sia univoca.<br /><br /> L'univocità può essere una proprietà sia degli indici cluster che degli indici non cluster.|[Creare indici univoci](../../relational-databases/indexes/create-unique-indexes.md)|  
|Columnstore|Un indice columnstore in memoria consente di archiviare e gestire i dati tramite l'archiviazione dei dati basata su colonne e l'elaborazione delle query basata su colonne.<br /><br /> Gli indici columnstore sono ideali per i carichi di lavoro di data warehousing che eseguono principalmente caricamenti bulk e query di sola lettura. Usare l'indice columnstore per migliorare fino a **10 volte le prestazioni delle query** rispetto all'archiviazione tradizionale orientata alle righe e fino a **7 volte la compressione dei dati** rispetto alle dimensioni dei dati non compressi.|[Guida agli indici columnstore](../Topic/Columnstore%20Indexes%20Guide.md)<br /><br /> [Utilizzo di indici columnstore non cluster](https://msdn.microsoft.com/en-us/library/dn589806.aspx)|  
|Indice con colonne|Indice non cluster esteso per includere colonne non chiave oltre alle colonne chiave.|[Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md)|  
|Indice per le colonne calcolate|Indice in una colonna derivato dal valore di una o più altre colonne, o da input deterministici specifici.|[Indici per le colonne calcolate](../../relational-databases/indexes/indexes-on-computed-columns.md)|  
|Filtrato|Indice non cluster ottimizzato, particolarmente indicato per coprire query che selezionano dati da un subset ben definito. Un indice di questo tipo utilizza un predicato del filtro per indicizzare una parte di righe nella tabella. Se confrontato con indici di tabella completa, un indice filtrato progettato correttamente consente di migliorare le prestazioni di esecuzione delle query e di ridurre i costi di manutenzione e di archiviazione dell'indice stesso.|[Creare indici filtrati](../../relational-databases/indexes/create-filtered-indexes.md)|  
|Spaziale|Un indice spaziale consente di eseguire in modo più efficiente determinate operazioni su oggetti spaziali (*dati spaziali*) in una colonna con tipo di dati **geometry**. nonché di ridurre il numero di oggetti sui quali è necessario applicare operazioni spaziali relativamente costose.|[Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)|  
|XML|Rappresentazione suddivisa e persistente degli oggetti binari di grandi dimensioni (BLOB, Binary Large OBject) XML nella colonna con tipo di dati **xml**.|[Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)|  
|Full-text|Tipo speciale di indice funzionale basato su token compilato e gestito dal motore di ricerca full-text Microsoft per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo indice offre supporto efficace per le ricerche di testo complesse nelle stringhe di caratteri.|[Popolamento degli indici full-text](../../relational-databases/search/populate-full-text-indexes.md)|  
  
## Attività correlate  
  
## Contenuto correlato  
 [Opzione SORT_IN_TEMPDB per gli indici](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
  
 [Disabilitazione di indici e vincoli](../../relational-databases/indexes/disable-indexes-and-constraints.md)  
  
 [Abilitazione di indici e vincoli](../../relational-databases/indexes/enable-indexes-and-constraints.md)  
  
 [Ridenominazione di indici](../../relational-databases/indexes/rename-indexes.md)  
  
 [Impostare le opzioni di indice](../../relational-databases/indexes/set-index-options.md)  
  
 [Requisiti di spazio su disco per operazioni DLL sugli indici](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md)  
  
 [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
 [Specificare un fattore di riempimento per un indice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
## Vedere anche  
 [Descrizione di indici cluster e non cluster.](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)  
  
  