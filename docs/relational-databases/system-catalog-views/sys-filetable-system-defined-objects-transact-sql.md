---
title: filetable_system_defined_objects (Transact-SQL) | Documenti Microsoft
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
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3bd6bd8368525c94ce0d999af921c76c2cade96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene un elenco degli oggetti definiti dal sistema correlati a tabelle FileTable. Contiene una riga per ogni oggetto definito dal sistema.  
  
 Quando si crea una tabella FileTable, vengono creati contemporaneamente anche gli oggetti correlati, quali vincoli e indici. Non è possibile modificare o eliminare questi oggetti, che verranno eliminato solo all'eliminazione della tabella FileTable stessa.  
  
 Per ulteriori informazioni su tabelle Filetable, vedere [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto definito dal sistema correlato a una tabella FileTable.<br /><br /> Fa riferimento all'oggetto in **Sys. Objects**.|  
|**parent_object_id**|**int**|ID oggetto della tabella FileTable padre.<br /><br /> Fa riferimento all'oggetto in **Sys. Objects**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare, modificare e rilasciare FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Gestire tabelle FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
