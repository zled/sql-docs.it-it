---
title: sysmergearticlecolumns (Transact-SQL) | Documenti Microsoft
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
- sysmergearticlecolumns
- sysmergearticlecolumns_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmergearticlecolumns system table
ms.assetid: 1ad8663f-a624-42a2-8641-fefac3433c97
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc764b33d64f7264fd5a45c38746dea473cb03e6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergearticlecolumns-transact-sql"></a>sysmergearticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysmergearticlecolumns** tabella contiene una riga per ogni colonna della tabella è pubblicata in una pubblicazione di tipo merge, che esegue il mapping di ogni colonna e il relativo articolo di merge. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifica un articolo.|  
|**colid**|**smallint**|Identifica una colonna di un articolo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
