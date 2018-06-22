---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 41e4f62a27a3f4a126c9d25b00c03f7f4c31b933
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055250"
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
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Riorganizzare e ricompilare gli indici](../indexes/indexes.md)  
  
  
