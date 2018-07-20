---
title: IHcolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
- IHcolumns_TSQL
- IHcolumns
dev_langs:
- TSQL
helpviewer_keywords:
- IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2f0235a7c4e1b13d6e85e59afd7bf0ffd57ba705
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103729"
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHcolumns** tabella di sistema contiene una riga per ogni colonna pubblicata. Questa tabella viene utilizzata per definire la modalità di rappresentazione quando pubblicato, i tipi di dati colonna dalla pubblicazione non SQL Server che esegue praticamente il mapping dei tipi di dati tra un sistemi di gestione database (DBMS) non SQL Server e SQL Server. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|Identifica una colonna pubblicata.|  
|**publishercolumn_id**|**int**|Associa i metadati della colonna archiviati in una colonna pubblicata la [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) tabella di sistema.|  
|**name**|**sysname**|Specifica il nome della colonna.|  
|**article_id**|**int**|Identifica l'articolo al quale appartiene la colonna.|  
|**column_ordinal**|**int**|Identifica la colonna in base all'ordine.|  
|**mapped_type**|**tinyint**|Tipo di dati della colonna di destinazione nel Sottoscrittore.|  
|**mapped_length**|**bigint**|Lunghezza della colonna nel Sottoscrittore.|  
|**mapped_prec**|**int**|Precisione della colonna nel Sottoscrittore.|  
|**mapped_scale**|**int**|Scala della colonna nel Sottoscrittore.|  
|**mapped_nullable**|**bit**|Indica se la colonna nel Sottoscrittore ammette valori NULL, dove **1** significa che i valori NULL vengono accettati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;vista di sistema&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
