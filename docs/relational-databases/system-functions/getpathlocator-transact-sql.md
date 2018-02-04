---
title: GetPathLocator (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d74dda3f9ee67c76e90967d3ced6c43951a225a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore dell'ID localizzatore del percorso per la directory o il file specificato in una tabella FileTable.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>Argomenti  
 *filenamespace_path*  
 Percorso dello spazio dei nomi nella tabella FileTable. Il percorso dello spazio dei nomi è di tipo **nvarchar (max)**.  
  
 Quando il database appartiene a un gruppo di disponibilità Always On, il **GetPathLocator** funzione accetta il nome di rete virtuale (VNN) o il nome del computer.  
  
## <a name="return-type"></a>Tipo restituito  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per altre informazioni, vedere [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Esempi  
 È possibile utilizzare il **GetPathLocator** funzione quando si è la migrazione dei file da un file server a una tabella FileTable. In questo scenario si desidera spostare i file nella tabella FileTable, quindi sostituire il percorso UNC originale per ogni file con il percorso UNC della tabella FileTable. Per un esempio completo, vedere [caricare file in Filetable](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
