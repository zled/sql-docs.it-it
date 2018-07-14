---
title: XTP Phantom Processor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1218f92622f9294c15afe417bcebbe84ad0df5da
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175878"
---
# <a name="xtp-phantom-processor"></a>XTP Phantom Processor
  L'oggetto prestazione XTP Phantom Processor contiene contatori correlati al sottosistema di elaborazione fantasma del motore XTP. Con questo componente è possibile rilevare le righe fantasma nelle transazioni in esecuzione a livello di isolamento SERIALIZABLE.  
  
 La tabella seguente descrive la **XTP Phantom Processor** contatori.  
  
|Contatore|Description|  
|-------------|-----------------|  
|**Tentativi di analisi di elementi nascosti/sec (eseguiti dal processore fantasma)**|Numero medio di tentativi di analisi dovuti a conflitti di scrittura durante le operazioni su elementi nascosti eseguite dal processore fantasma, al secondo. Si tratta di un contatore di livello molto basso, non destinato all'uso da parte del cliente.|  
|**Righe fantasma scadute rimosse/sec**|Numero medio di righe scadute rimosse dalle analisi fantasma, al secondo.|  
|**Righe fantasma scadute interessate/sec**|Numero medio di righe scadute interessate dalle analisi fantasma, al secondo.|  
|**Righe fantasma in scadenza interessate/sec**|Numero medio di righe in scadenza interessate dalle analisi fantasma, al secondo.|  
|**Righe fantasma interessate/sec**|Numero medio di righe interessate dalle analisi fantasma, al secondo.|  
|**Analisi fantasma avviate/sec**|Numero medio di analisi fantasma avviate, al secondo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XTP &#40;OLTP In memoria&#41; i contatori delle prestazioni](../../integration-services/performance/performance-counters.md)  
  
  
