---
title: "Configurazione di SQL Server (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b08969f-b90b-46b3-98e7-0bf7734833fc
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Configurazione di SQL Server (R Services)
Le informazioni contenute in questa sezione vengono fornite indicazioni generali sulla configurazione hardware e di rete del computer in cui viene utilizzato per ospitare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Deve essere considerato oltre generale [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] informazioni fornite in ottimizzazione delle prestazioni di [centro delle prestazioni per il motore di Database di SQL Server e Database SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## Processore

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] eseguire attività in parallelo, utilizzare i core disponibili nel computer; più core disponibili, ottenere le migliori prestazioni. Poiché [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è in genere utilizzato da più utenti contemporaneamente, l'amministratore del database deve determinare il numero ideale di core necessari per consentire i calcoli di picco del carico di lavoro. Mentre il numero di core non possono risultare utili per operazioni dei / o associate, algoritmi associate alla CPU trarranno vantaggio dalla CPU più veloci con tutti i core.

## Memoria

La quantità di memoria disponibile nel computer può avere un impatto notevole sulle prestazioni degli algoritmi analitici avanzati. Memoria insufficiente può influenzare il grado di parallelismo quando si utilizza il contesto di calcolo SQL. Può inoltre influire le dimensioni di blocco (righe per ogni operazione di lettura) che possono essere elaborate e il numero di sessioni simultanee che possono essere supportati.

È consigliabile un minimo di 32GB. Se si dispone di più di 32GB disponibili, è possibile configurare l'origine dati SQL per l'utilizzo di più righe in ogni operazione di lettura per migliorare le prestazioni.

## Opzioni risparmio energia

Nel sistema operativo Windows, il __ad alte prestazioni__ power opzione deve essere utilizzata. Utilizzando un'impostazione di alimentazione differenti comporterà incoerenti o una riduzione delle prestazioni quando si utilizza [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

## IO disco

I processi di training e la stima utilizzando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sono intrinsecamente IO associato e variano in base alla velocità di dischi che è archiviato il database in. Possono aiutare a unità più veloce, ad esempio unità disco a stato solido (SSD). 

IO disco dipende anche da altre applicazioni di accedere al disco: ad esempio, le operazioni su un database da altri client di lettura. Le prestazioni dei / o del disco possono essere influenzata anche dalle impostazioni nel file system in uso, ad esempio la dimensione del blocco utilizzata dal file system. Se sono disponibili più unità, i database dell'archivio in un'unità diversa da quella [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] in modo che le richieste per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] non raggiunge lo stesso disco come richiesto per i dati archiviati nel database.

IO disco possono anche notevolmente sulle prestazioni durante l'esecuzione di funzioni analitiche RevoScaleR che utilizzano più iterazioni durante il training. Ad esempio, `rxLogit`, `rxDTree`, `rxDForest` e `rxBTrees` utilizzano più iterazioni. Quando l'origine dati è [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], questi algoritmi utilizzano file temporanei che sono ottimizzati per acquisire i dati. Questi file vengono eliminati automaticamente al termine della sessione. Con un disco ad alte prestazioni per le operazioni di lettura/scrittura può migliorare significativamente il tempo complessivo trascorso per questi algoritmi.

> [!NOTE]
> [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] richiede il supporto di nome file 8.3 nei sistemi operativi Windows. È possibile utilizzare fsutil.exe per determinare se un'unità supporta nomi di 8.3 file o per abilitare il supporto in caso contrario. Per ulteriori informazioni sull'utilizzo di fsutil.exe con nomi di 8.3 file, vedere [8dot3name Fsutil](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

### Compressione di tabelle

Prestazioni dei / o possono spesso essere migliorate utilizzando la compressione o indici columstore. In genere, i dati sono spesso ripetuti in diverse colonne all'interno di una tabella, in modo da utilizzare un indice columnstore sfrutta queste ripetizioni quando si comprime i dati.

Un indice columnstore potrebbe non essere più efficiente se sono presenti molti degli inserimenti nella tabella, ma è una scelta ottimale se i dati statici o vengono modificati solo raramente. Se un archivio colonne non è appropriato, l'abilitazione della compressione in una tabella principale riga consente di migliorare il / o.

Per ulteriori informazioni, vedere i seguenti documenti:

* [Compressione dei dati](../../relational-databases/data-compression/data-compression.md)

* [Abilitare la compressione in una tabella o un indice](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

* [Guida agli indici columnstore](Columnstore%20Indexes%20Guide.md)

## File di paging

Il sistema operativo Windows utilizza un file di paging per gestire i dump di arresto anomalo del sistema e per l'archiviazione delle pagine di memoria virtuale. Se si nota un paging eccessivo, provare ad aumentare la memoria fisica del computer. Sebbene con quantità di memoria fisica non elimina il paging, riduce la necessità di paging.

La velocità del disco che viene memorizzato il file di paging sul inoltre può influire sulle prestazioni. Archiviare il file di pagina su un'unità SSD o utilizzo di più file di pagina tra più unità SSD, migliorare le prestazioni.

Vedere [come determinare le dimensioni di file della pagina sia appropriato per le versioni a 64 bit di Windows](https://support.microsoft.com/en-us/kb/2860880) per informazioni sul ridimensionamento del file di paging.

## Governance delle risorse

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] supporta la governance delle risorse per controllare le varie risorse usate da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Ad esempio, è limitato al 20% della memoria totale disponibile per il valore predefinito per il consumo di memoria da R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Questa operazione viene eseguita per assicurarsi che [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] i flussi di lavoro non causa gravi difficoltà da processi con esecuzione prolungata R. Questi limiti, tuttavia, possono essere modificati dall'amministratore del database. 

Le risorse limitate sono __MAX_CPU_PERCENT__, __MAX_MEMORY_PERCENT__, e __MAX_PROCESSES__. Per visualizzare le impostazioni correnti, utilizzare questo [!INCLUDE[tsql_md](../../includes/tsql-md.md)] istruzione:

```T-SQL
SELECT * FROM sys.resource_governor_external_resource_pools
``` 

Se [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene principalmente utilizzato per i servizi di R, potrebbe essere utile aumentare MAX_CPU_PERCENT fino al 40% o il 60%. Se esistono molte sessioni R utilizzando lo stesso [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] allo stesso tempo, verranno aumentati tutti e tre. Per modificare i valori di risorsa, utilizzare [!INCLUDE[tsql_md](../../includes/tsql-md.md)] istruzioni. 

In questo esempio imposta l'utilizzo della memoria al 40%:

```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)
```
Nell'esempio seguente imposta tutti e tre i valori configurabili:
```T-SQL
ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`
``` 

> [!NOTE]
> Per apportare modifiche a queste impostazioni vengono applicate immediatamente, eseguire l'istruzione `ALTER RESOURCE GOVERNOR RECONFIGURE` dopo la modifica di una memoria, CPU o l'impostazione massima del processo. 

## Vedere anche
[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

[CREARE POOL DI RISORSE ESTERNE](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [Guida di ottimizzazione delle prestazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 
 [Case Study di prestazioni](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 
 [R e ottimizzazione dei dati](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)