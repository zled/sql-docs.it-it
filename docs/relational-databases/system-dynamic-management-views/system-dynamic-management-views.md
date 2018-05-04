---
title: Viste a gestione dinamica (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], about dynamic management objects
- server state information [SQL Server]
- dynamic management functions [SQL Server]
- metadata [SQL Server], dynamic management objects
- dynamic management views [SQL Server]
- DMVs [SQL Server]
- functions [SQL Server], dynamic management
- server scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server]
ms.assetid: cf893ecb-0bf6-4cbf-ac00-8a1099e405b1
caps.latest.revision: 41
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0bdc1970662feaf12a31ec904ce5477fa110e8e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="system-dynamic-management-views"></a>Viste a gestione dinamica del sistema
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le funzioni e le viste a gestione dinamica restituiscono informazioni sullo stato del server che possono essere utilizzate per monitorare l'integrità di un'istanza del server, diagnosticare i problemi e ottimizzare le prestazioni.  
  
> [!IMPORTANT]  
>  Le funzioni e le viste a gestione dinamica restituiscono dati interni, specifici dell'implementazione, relativi allo stato. I dati restituiti e gli schemi potrebbero cambiare nelle versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le funzioni e le viste a gestione dinamica delle versioni future potrebbero pertanto non essere compatibili con quelle contenute in questa versione. Ad esempio, nelle prossime versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile che Microsoft estenda la definizione di qualsiasi vista a gestione dinamica aggiungendo colonne alla fine del relativo elenco. Non è consigliabile utilizzare la sintassi `SELECT * FROM dynamic_management_view_name` nel codice di produzione. Il numero di colonne restituite potrebbe infatti cambiare compromettendo il corretto funzionamento dell'applicazione.  
  
 Esistono due tipi di funzioni e viste a gestione dinamica:  
  
-   Funzioni e viste a gestione dinamica con ambito server. Richiedono l'autorizzazione VIEW SERVER STATE nel server.  
  
-   Funzioni e viste a gestione dinamica con ambito database. Richiedono l'autorizzazione VIEW DATABASE STATE nel database.  
  
## <a name="querying-dynamic-management-views"></a>Esecuzione di query su viste a gestione dinamica  
 È possibile fare riferimento alle viste a gestione dinamica nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando nomi composti da due, tre o quattro parti. È invece possibile fare riferimento alle funzioni a gestione dinamica nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando nomi composti da due o tre parti. Non è possibile fare riferimento a funzioni e viste a gestione dinamica nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando nomi composti da una parte.  
  
 Tutte le funzioni e le viste a gestione dinamica esistono nello schema sys e seguono questa convenzione di denominazione dm_*. Quando si utilizza una funzione o vista a gestione dinamica, è necessario anteporre al nome della funzione o vista il prefisso di schema sys. Ad esempio, per eseguire una query sulla vista a gestione dinamica dm_os_wait_stats, eseguire la query seguente:  
  
 ```sql
SELECT wait_type, wait_time_ms  
FROM sys.dm_os_wait_stats;  
```  
  
### <a name="required-permissions"></a>Autorizzazioni necessarie  
 Per eseguire una query su una funzione o una vista a gestione dinamica è necessaria l'autorizzazione SELECT per l'oggetto e l'autorizzazione VIEW SERVER STATE o VIEW DATABASE STATE. Ciò consente di restringere in maniera selettiva l'accesso di un utente o di un account a funzioni e viste a gestione dinamica. A tale scopo, è necessario innanzitutto creare l'utente nel database master e quindi negargli l'autorizzazione SELECT per le funzioni o viste a gestione dinamica per le quali si desidera impedire l'accesso. Di conseguenza, l'utente non sarà più in grado di selezionare queste funzioni e viste a gestione dinamica, indipendentemente dal relativo contesto di database.  
  
> [!NOTE]  
>  Poiché DENY è prioritaria, se a un utente sono state concesse le autorizzazioni VIEW SERVER STATE ma è stata negata l'autorizzazione VIEW DATABASE STATE, l'utente sarà in grado di visualizzare le informazioni a livello di server, ma non quelle a livello di database.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Le funzioni e le viste a gestione dinamica sono state organizzate in base alle categorie seguenti.  
  
|||  
|-|-|  
|[Gruppi di disponibilità Always On viste a gestione dinamica e Funtions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)|[Viste a gestione dinamica tabella ottimizzazione della memoria &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)|  
|[Viste a gestione dinamica correlate a Change Data Capture &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)|[Funzioni e viste a gestione dinamica relative all'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Viste a gestione dinamica relative a rilevamento delle modifiche](http://msdn.microsoft.com/library/dc8a0af9-fcd8-4c34-9453-5132717c9bdb)|[Viste a gestione dinamica relative alle notifiche delle query &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/92eb22d8-33f3-4c17-b32e-e23acdfbd8f4)|  
|[Viste a gestione dinamica relative a Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)|[Viste a gestione dinamica relative alle repliche &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)|  
|[Viste a gestione dinamica correlate il mirroring del database &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/04fb21de-1b5e-4a8e-9ca6-1b78ad278db1)|[Viste a gestione dinamica relative a Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)|  
|[Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)|[Funzioni e viste a gestione dinamica relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|[Funzioni a gestione dinamica e DMV correlate al server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Viste a gestione dinamica degli eventi estesi](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)|[Viste a gestione dinamica & #40; relative a Service Broker Transact-SQL & #41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)|  
|[FileStream e FileTable DMV &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)|[Funzioni e viste a gestione dinamica relative a dati spaziali &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/c542ac38-451f-43a5-bf8c-4edd38bb738e)|  
|[Funzioni e viste a gestione dinamica ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)|[SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)|  
|[Funzioni e viste a gestione dinamica replica geografica &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)|[Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)|  
|[Funzioni e viste a gestione dinamica relative agli indici &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)|[Estensione Database viste a gestione dinamica &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/1193efce-a105-49a9-a8b8-26b063485567)|  
|[È possibile O funzioni e viste a gestione dinamica relative &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)|[Funzioni e viste a gestione dinamica relative alle transazioni &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)|  

  
## <a name="see-also"></a>Vedere anche  
 [CONCEDERE autorizzazioni Server &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)   
 [GRANT - autorizzazioni per database &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
