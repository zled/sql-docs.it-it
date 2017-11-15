---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: b13b71f78995fc1c516e5dba76953f91b541bfd4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2546|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_INDEX_MARKED_DISABLED|  
|Testo del messaggio|L'indice 'INDEX_NAME' della tabella 'OBJECT_NAME' è contrassegnato come disabilitato. Ricompilare l'indice per riportarlo online.|  
  
## <a name="explanation"></a>Spiegazione  
L'indice specificato è contrassegnato come offline oppure è disabilitato e pertanto non può essere controllato.  
  
## <a name="user-action"></a>Azione dell'utente  
Ricompilare l'indice utilizzando ALTER INDEX.  
  
## <a name="see-also"></a>Vedere anche  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[Riorganizzare e ricompilare gli indici](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
