---
title: sysarticlecolumns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e9cbce9de4325e9090e7b607a63e6e899d224420
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysarticlecolumns** tabella contiene una riga per ogni colonna della tabella è pubblicata in una pubblicazione snapshot o transazionale che esegue il mapping di ogni colonna e il relativo articolo. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifica un articolo.|  
|**colid**|**smallint**|Identifica una colonna di un articolo.|  
|**is_udt**|**bit**|Indica se il tipo di dati della colonna è un tipo definito dall'utente (UDT). Il valore **1** indica una colonna di tipo definito dall'utente.|  
|**is_xml**|**bit**|Indica se la colonna è un **xml** colonna. Il valore **1** indica una colonna xml.|  
|**is_max**|**bit**|Indica se la colonna è una colonna di tipo valore di grandi dimensioni, **varchar (max)**, **nvarchar (max)**, e **varbinary (max)**. Il valore **1** indica una colonna di valori di grandi dimensioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
