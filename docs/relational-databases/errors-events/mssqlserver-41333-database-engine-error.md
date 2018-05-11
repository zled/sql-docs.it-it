---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5e81abcdbc7d02da7c419b9e80ff2b4955600358
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41333|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Testo del messaggio|Le seguenti transazioni devono accedere a tabelle con ottimizzazione per la memoria e stored procedure compilate in modo nativo con isolamento SNAPSHOT: transazioni REPEATABLEREAD, SERIALIZABLE e transazioni che accedono a tabelle senza ottimizzazione per la memoria con isolamento REPEATABLEREAD o SERIALIZABLE.|  
  
## <a name="explanation"></a>Spiegazione  
Sono presenti restrizioni relative all'uso di livelli di isolamento più elevati tra le transazioni basate su disco e le transazioni di XTP.  
  
## <a name="user-action"></a>Azione dell'utente  
Non tentare operazioni con un livello di isolamento alto nelle tabelle ottimizzate per la memoria (e procedure compilate in modo nativo) e nelle tabelle basate su disco.  
  
Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
