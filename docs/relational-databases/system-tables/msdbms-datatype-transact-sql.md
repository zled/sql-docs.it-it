---
title: MSdbms_datatype (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd690436908a61b43b4e7af829e8bc3528fd5305
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msdbmsdatatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdbms_datatype** tabella contiene l'elenco completo dei tipi di dati nativi in ogni sistema di gestione di database supportate (DBMS) utilizzato come server di pubblicazione o sottoscrittore nella replica di database eterogenei. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|Identifica ogni tipo di dati univoco.|  
|**dbms_id**|**int**|Identifica il sistema DBMS al quale appartiene il tipo.|  
|**tipo**|**sysname**|Nome del tipo di dati (nativo).|  
|**CreateParams**|**int**|Mappa di bit che descrive la combinazione di lunghezza, precisione e scala valida per ogni tipo di dati, che include:<br /><br /> **0x1** = precisione.<br /><br /> **0x2** = scala.<br /><br /> **0x4** = lunghezza.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa tabella contiene le voci per i tipi di dati SQL Server perché un'istanza di SQL Server può sottoscrivere un database non SQL Server e a un sottoscrittore non SQL Server di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
