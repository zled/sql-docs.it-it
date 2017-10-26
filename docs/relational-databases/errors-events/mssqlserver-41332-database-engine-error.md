---
title: MSSQLSERVER_41332 | Microsoft Docs
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
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: be21e36f47e2bae00387e1f5aed087c94688f930
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41332"></a>MSSQLSERVER_41332
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41332|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Testo del messaggio|Non è possibile creare o accedere alle tabelle con ottimizzazione per la memoria e alle stored procedure compilate in modo nativo quando la sessione TRANSACTION ISOLATION LEVEL è impostata su SNAPSHOT.|  
  
## <a name="explanation"></a>Spiegazione  
La transazione è stata avviata nel livello di isolamento dello snapshot e quindi ha tentato di utilizzare una funzionalità non compatibile.  
  
## <a name="user-action"></a>Azione dell'utente  
Avviare la transazione con un livello di isolamento diverso. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

