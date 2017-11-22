---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3235cee13ecfc73cc3a3fee5e83a320c8f25b842
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2530|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_INDEX_IS_OFFLINE|  
|Testo del messaggio|L'indice "%.*ls" sulla tabella "%.\*ls" è disabilitato.|  
  
## <a name="explanation"></a>Spiegazione  
L'istruzione DBCC non può proseguire perché l'indice specificato è disabilitato. Dopo che un indice viene disabilitato, resta in questo stato fino a quando non viene ricompilato o eliminato e quindi ricreato.  
  
## <a name="user-action"></a>Azione dell'utente  
  
1.  Abilitare l'indice disabilitato utilizzando uno dei metodi seguenti:  
  
    -   Istruzione ALTER INDEX con la clausola REBUILD  
  
    -   Istruzione CREATE INDEX con la clausola DROP_EXISTING  
  
    -   DBCC DBREINDEX  
  
2.  Rieseguire l'istruzione DBCC.  
  
## <a name="see-also"></a>Vedere anche  
[Abilitare indici e vincoli](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
