---
title: sysarticlecolumns (vista di sistema) (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
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
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93590ffdd531827104b70d9b1d0f3c4ee2eee3f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (vista di sistema) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysarticlecolumns** Vista espone informazioni aggiuntive sulle colonne degli articoli pubblicati. Questa vista è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifica un articolo.|  
|**colid**|**int**|Identifica una colonna di un articolo.|  
|**is_udt**|**int**|Indica se il tipo di dati della colonna è un tipo definito dall'utente (UDT). Il valore **1** indica una colonna di tipo definito dall'utente.|  
|**is_xml**|**int**|Indica se la colonna è un **xml** colonna. Il valore **1** indica un **xml** colonna.|  
|**is_max**|**int**|Indica se la colonna è una colonna di tipo di dati di valori di grandi dimensioni (**varchar (max)**, **nvarchar (max)** o **varbinary (max)**). Il valore **1** indica una colonna di valori di grandi dimensioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
