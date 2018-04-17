---
title: IHpublishercolumns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06d0d772ee3def5c7b3823735793127bbe5cb26b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ihpublishercolumns-transact-sql"></a>IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHpublishercolumns** tabella di sistema rappresenta i metadati archiviati nel server di pubblicazione. Questa tabella contiene una riga per ogni colonna replicata da Server di pubblicazione non SQL utilizzando il server di distribuzione corrente. Informazioni nel tipo di dati **IHpublishercolumns** è specifico del sistema non SQL Server di gestione database (DBMS) da cui i dati vengono pubblicati. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifica una colonna pubblicata.|  
|**table_id**|**int**|Identifica la tabella di origine da [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) a cui appartiene la colonna.|  
|**publisher_id**|**smallint**|Identifica la pubblicazione non SQL Server da cui la colonna è pubblicata.|  
|**name**|**sysname**|Nome della colonna pubblicata.|  
|**column_ordinal**|**int**|Identifica la colonna in base all'ordine.|  
|**type**|**varchar(255)**|Tipo di dati della colonna di origine nel server di pubblicazione.|  
|**lunghezza**|**bigint**|Lunghezza della colonna di origine nel server di pubblicazione.|  
|**Prec**|**int**|Precisione della colonna di origine nel server di pubblicazione.|  
|**scala**|**int**|Scala della colonna di origine nel server di pubblicazione.|  
|**IsNullable**|**bit**|Indica se la colonna accetta valori NULL, in cui **1** significa che i valori NULL vengono accettati.|  
|**iscaptured**|**bit**|Indica se esiste un trigger nella colonna. Il trigger potrebbe esistere anche se la colonna non è pubblicata in un articolo. Il valore **1** significa che il trigger esiste nella colonna.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns &#40;vista di sistema&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
