---
title: INDEXPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INDEXPROPERTY
- INDEXPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INDEXPROPERTY function
- indexes [SQL Server], viewing
- indexes [SQL Server], properties
ms.assetid: 998d5788-4871-44a8-8125-0d9390868b84
caps.latest.revision: 56
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 2f793612ff0fa46e2fd72f6a51e48eae30602fdf
ms.contentlocale: it-it
ms.lasthandoff: 10/24/2017

---
# <a name="indexproperty-transact-sql"></a>INDEXPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il valore delle proprietà di indice o statistiche specificate in base al numero di identificazione della tabella, al nome dell'indice o delle statistiche e al nome della proprietà. Restituisce NULL per gli indici XML.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
INDEXPROPERTY ( object_ID , index_or_statistics_name , property )   
```  
  
## <a name="arguments"></a>Argomenti  
 *object_ID*  
 Espressione che contiene il numero di identificazione della tabella o vista indicizzata di cui si desidera ottenere informazioni sulla proprietà dell'indice. *object_ID* è **int**.  
  
 *index_or_statistics_name*  
 Espressione che contiene il nome dell'indice o delle statistiche per cui si desidera ottenere informazioni sulle proprietà. *index_or_statistics_name* è **nvarchar (128)**.  
  
 *proprietà*  
 Espressione che contiene il nome della proprietà del database da restituire. *proprietà* è **varchar (128)**, i possibili valori sono i seguenti.  
  
> [!NOTE]  
>  Se non diversamente specificato, viene restituito NULL quando *proprietà* non è un nome di proprietà valido, *object_ID* non è un ID di oggetto valido, *object_ID* è un tipo di oggetto non supportato per la proprietà specificata o il chiamante non dispone dell'autorizzazione per visualizzare i metadati dell'oggetto.  
  
|Proprietà|Description|Valore|  
|--------------|-----------------|-----------|  
|**IndexDepth**|Dettagli dell'indice.|Numero di livelli dell'indice.<br /><br /> NULL = indice XML o input non valido.|  
|**IndexFillFactor**|Valore del fattore di riempimento utilizzato quando l'indice è stato creato o ricompilato per l'ultima volta.|Fattore di riempimento|  
|**IndexID**|ID dell'indice della tabella o vista indicizzata specificata.|ID dell'indice|  
|**IsAutoStatistics**|Le statistiche sono state generate mediante l'opzione AUTO_CREATE_STATISTICS di ALTER DATABASE.|1 = True<br /><br /> 0 = False o indice XML.|  
|**IsClustered**|Indice cluster.|1 = True<br /><br /> 0 = False o indice XML.|  
|**IsDisabled**|L'indice è disabilitato.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Input non valido.|  
|**IsFulltextKey**|L'indice è la chiave di indicizzazione full-text e semantica per una tabella.|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False o indice XML.<br /><br /> NULL = Input non valido.|  
|**IsHypothetical**|L'indice è ipotetico e non può essere utilizzato direttamente come percorso di accesso ai dati. Gli indici ipotetici contengono statistiche a livello di colonna e vengono gestiti e utilizzati da Ottimizzazione guidata motore di database.|1 = True<br /><br /> 0 = false o indice XML.<br /><br /> NULL = Input non valido.|  
|**IsPadIndex**|All'indice è associata la quantità di spazio da lasciare aperto in ogni nodo interno.|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False o indice XML.|  
|**IsPageLockDisallowed**|Valore per il blocco di pagina impostato mediante l'opzione ALLOW_PAGE_LOCKS di ALTER INDEX.|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = il blocco di pagina è disattivato.<br /><br /> 0 = il blocco di pagina è attivato.<br /><br /> NULL = Input non valido.|  
|**IsRowLockDisallowed**|Valore per il blocco di riga impostato tramite l'opzione ALLOW_ROW_LOCKS di ALTER INDEX.|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = il blocco di riga è disattivato.<br /><br /> 0 = il blocco di riga è attivato.<br /><br /> NULL = Input non valido.|  
|**IsStatistics**|*index_or_statistics_name* è statistiche create dall'istruzione CREATE STATISTICS o dall'opzione AUTO_CREATE_STATISTICS di ALTER DATABASE.|1 = True<br /><br /> 0 = False o indice XML.|  
|**IsUnique**|Indice univoco.|1 = True<br /><br /> 0 = False o indice XML.|  
|**IsColumnstore**|L'indice è un indice columnstore con ottimizzazione per la memoria xVelocity.|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="exceptions"></a>Eccezioni  
 Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto.  
  
 Un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come INDEXPROPERTY possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce i valori per il **IsClustered**, **IndexDepth**, e **IndexFillFactor** le proprietà per il `PK_Employee_BusinessEntityID` indice del `Employee`tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.  
  
```  
SELECT   
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IsClustered')AS [Is Clustered],  
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IndexDepth') AS [Index Depth],  
    INDEXPROPERTY(OBJECT_ID('HumanResources.Employee'),  
        'PK_Employee_BusinessEntityID','IndexFillFactor') AS [Fill Factor];  
  
```  
  
 Set di risultati:  
  
```  
Is Clustered Index Depth Fill Factor   
------------ ----------- -----------   
1            2           0  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente vengono esaminate le proprietà di uno degli indici nel `FactResellerSales` tabella.  
  
```  
-- Uses AdventureWorks  
  
SELECT   
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IsClustered') AS [Is Clustered],  
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IsColumnstore') AS [Is Columnstore Index],  
INDEXPROPERTY(OBJECT_ID('dbo.FactResellerSales'),  
    'ClusteredIndex_6d10fa223e5e4c1fbba087e29e16a7a2','IndexFillFactor') AS [Fill Factor];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [Statistiche](../../relational-databases/statistics/statistics.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Sys. stats_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  


