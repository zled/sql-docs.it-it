---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb3f01e875daa3ee2a12c0a7d7f927f1cd106ebd
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
