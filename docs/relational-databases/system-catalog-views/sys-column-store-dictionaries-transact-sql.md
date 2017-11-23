---
title: Sys. column_store_dictionaries (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs: TSQL
helpviewer_keywords: sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e540f8bea10bb627554ebee15254112e3e4d71c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni dizionario utilizzato negli indici columnstore con ottimizzazione per la memoria xVelocity. I dizionari vengono utilizzati per codificare alcuni tipi di dati, ma non tutti. Pertanto non tutte le colonne in un indice columnstore contengono dizionari. Un dizionario può essere presente come dizionario primario (per tutti i segmenti) e possibilmente per altri dizionari secondari utilizzati per un subset di segmenti della colonna.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|ID dell'heap o dell'indice ad albero B (HoBT) per la tabella a cui appartiene l'indice columnstore.|  
|**column_id**|**int**|ID della colonna columnstore a partire da 1. La prima colonna con ID = 1, la seconda colonna con ID = 2, e così via.|  
|**dictionary_id**|**int**|Possono essere presenti due tipi di dizionari, globali e locali, associati a un segmento di colonna. Un dictionary_id 0 rappresenta il dizionario globale condivisa tra tutti i segmenti di colonna (uno per ogni gruppo di righe) per la colonna.|  
|**version**|**int**|Versione del formato del dizionario.|  
|**tipo**|**int**|Tipo di dizionario:<br /><br /> 1: dizionario hash contenente **int** valori<br /><br /> 2: non utilizzato<br /><br /> 3: dizionario hash contenente valori stringa<br /><br /> 4: dizionario hash contenente **float** valori<br /><br /> Per ulteriori informazioni sui dizionari, vedere [Guida agli indici Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**int**|L'ultimo ID dati nel dizionario.|  
|**entry_count**|**bigint**|Numero di voci nel dizionario.|  
|**on_disc_size**|**bigint**|Dimensioni del dizionario in byte.|  
|**partition_id**|**bigint**|Indica l'ID della partizione. Valore univoco all'interno di un database.|  
  
## <a name="permissions"></a>Permissions  
 Tutte le colonne richiedono almeno l'autorizzazione VIEW DEFINITION sulla tabella. Le colonne seguenti restituiscono null a meno che l'utente ha inoltre **selezionare** autorizzazione: last_id, entry_count, data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [L'esecuzione di query di catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Sys.ALL_COLUMNS &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [Sys. computed_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

