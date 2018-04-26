---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 662226bb89efe4b28731aebe4cb708eea96ee9bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41305"></a>MSSQLSERVER_41305
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41305|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_TX_COMMIT_RR_VALIDATION|  
|Testo del messaggio|Impossibile eseguire il commit della transazione corrente a causa di un errore di convalida di lettura ripetibile.|  
  
## <a name="explanation"></a>Spiegazione  
La transazione ha rilevato un errore di convalida ed è stata eliminata.  
  
Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="user-action"></a>Azione dell'utente  
Ripetere la transazione non riuscita.  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
