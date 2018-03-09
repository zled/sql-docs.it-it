---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c233a31bd2f0c17ef8081db3a42e4be89b753092
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41359|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Testo del messaggio|Una query che accede a tabelle con ottimizzazione per la memoria utilizzando il livello di isolamento READ COMMITTED non può accedere alle tabelle basate su disco quando l'opzione di database READ_COMMITTED_SNAPSHOT è impostata su ON. Specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint di tabella, ad esempio WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Spiegazione  
Il database con READ_COMMITTED_SNAPSHOT=ON non supporta le transazioni che accedono sia alle tabelle ottimizzate per la memoria che a tabelle basate su disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare READ_COMMITTED_SNAPSHOT su OFF o specificare un livello di isolamento supportato per la tabella ottimizzata per la memoria utilizzando un hint a livello di tabella, ad esempio WITH (SNAPSHOT). Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
