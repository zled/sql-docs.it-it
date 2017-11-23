---
title: IHpublishercolumnindexes (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs: TSQL
helpviewer_keywords: IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21370e81d1be10aef58a5dda779f765417fc0a54
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHpublishercolumnindexes** tabella di sistema esegue il mapping di colonne di una pubblicazione non SQL Server nel [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) agli indici della tabella di sistema di [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)tabella di sistema. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifica la colonna da [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) con l'indice associato.|  
|**publisherindex_id**|**int**|Identifica un indice di [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) associata alla colonna di tabella.|  
|**indid**|**int**|Indica la posizione della colonna nella tabella pubblicata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
