---
title: Sys. filetables (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- filetables
- filetables_TSQL
- sys.filetables
- sys.filetables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetables catalog view
ms.assetid: a740be59-cd52-4707-9ad2-5203669a63ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0b047ba0650302857775b62214a7771c7e1f6a0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletables-transact-sql"></a>sys.filetables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene restituita una riga per ogni oggetto FileTable in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per ulteriori informazioni su tabelle Filetable, vedere [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).    
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**||Numero di identificazione dell'oggetto. Valore univoco all'interno di un database.<br /><br /> Per ulteriori informazioni, [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_enabled**|**bit**|1 = Lo stato dell'oggetto FileTable è "abilitato".|  
|**directory_name**|**varchar (255)**|Nome della directory radice per un oggetto FileTable.|  
|**filename_collation_id**||Identificatore delle regole di confronto definito per l'oggetto FileTable.|  
|**filename_collation_name**||Nome delle regole di confronto definito per l'oggetto FileTable.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di tabelle Filetable](../../relational-databases/blob/manage-filetables.md)   
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
  
  
