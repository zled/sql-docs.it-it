---
title: Archiviazione XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 628e93e1ceef7bd34b55860370fc7b1ab98a020c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227633"
---
# <a name="xtp-storage"></a>Archiviazione XTP
  L'oggetto prestazione XTP Storage contiene contatori correlati all'archiviazione XTP di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La tabella seguente descrive la **XTP Storage** contatori.  
  
|Contatore|Description|  
|-------------|-----------------|  
|**Checkpoint chiusi**|Conteggio di checkpoint chiusi eseguiti dall'agente online.|  
|**Checkpoint completati**|Conteggio di checkpoint elaborati dal thread offline dei checkpoint.|  
|**Operazioni di unioni principali completate**|Numero di operazioni di unioni principali completate dal thread di lavoro di tipo merge. Queste operazioni devono ancora essere installate.|  
|**Valutazioni dei criteri di unione**|Numero di valutazioni dei criteri di unione dall'avvio del server.|  
|**Richieste di tipo merge in sospeso**|Numero di richieste di tipo merge in sospeso dall'avvio del server.|  
|**Operazioni di unione abbandonate**|Numero di operazioni di unione abbandonate a causa di un errore.|  
|**Operazioni di unione installate**|Numero di operazioni di unione installate correttamente.|  
|**File totali uniti**|Numero totale di file di origine uniti. Questo numero può essere utilizzato per trovare il numero medio di file di origine nell'unione.|  
  
## <a name="see-also"></a>Vedere anche  
 [XTP &#40;OLTP In memoria&#41; i contatori delle prestazioni](../../integration-services/performance/performance-counters.md)  
  
  
