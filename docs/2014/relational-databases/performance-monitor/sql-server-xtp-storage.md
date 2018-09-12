---
title: Archiviazione XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: 3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6e08f36a46b7c8e1762380e30da1dd939dfb2ad9
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43817707"
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
  
  
