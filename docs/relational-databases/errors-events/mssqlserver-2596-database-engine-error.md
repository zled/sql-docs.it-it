---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 669ad8fa565b39b8a589bf2940b91059d6355bb0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2596|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Testo del messaggio|L'istruzione di correzione non è stata elaborata. Il database non può essere in modalità sola lettura.|  
  
## <a name="explanation"></a>Spiegazione  
Il messaggio indica che il database è in modalità sola lettura. Non è possibile implementare correzioni quando un database si trova in tale modalità.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare il database per l'accesso in lettura/scrittura utilizzando ALTER DATABASE e quindi eseguire nuovamente il comando DBCC.  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  

