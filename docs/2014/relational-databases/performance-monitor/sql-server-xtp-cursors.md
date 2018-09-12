---
title: XTP Cursors | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 09704cd8d4855bf082bd24d7ec35cad52c5c939e
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810087"
---
# <a name="xtp-cursors"></a>XTP Cursors
  L'oggetto prestazione XTP Cursors contiene contatori correlati ai cursori interni del motore XTP. I cursori sono gli utilizzi del motore XTP per elaborare di blocchi predefiniti di basso livello [!INCLUDE[tsql](../../includes/tsql-md.md)] le query. Di conseguenza, in genere non si ha controllo diretto su di essi.  
  
 La tabella seguente descrive la **XTP Cursors** contatori.  
  
|Contatore|Description|  
|-------------|-----------------|  
|**Eliminazioni cursori/sec**|Numero medio di eliminazioni di cursori, al secondo.|  
|**Inserimenti cursori/sec**|Numero medio di inserimenti di cursori, al secondo.|  
|**Analisi cursore avviate/sec**|Numero medio di analisi cursore avviate, al secondo.|  
|**Violazioni UNIQUE del cursore/sec**|Numero medio di violazioni di vincolo UNIQUE, al secondo.|  
|**Aggiornamenti cursori/sec**|Numero medio di aggiornamenti di cursori, al secondo.|  
|**Conflitti di scrittura cursore/sec**|Numero medio di conflitti di scrittura sulla stessa versione di riga, al secondo.|  
|**Tentativi di analisi di elementi nascosti/sec (immessi dall'utente)**|Numero medio di tentativi di analisi dovuti a conflitti di scrittura durante le operazioni su elementi nascosti eseguite da un'analisi di tabella completa dell'utente, al secondo. Si tratta di un contatore di livello molto basso, non destinato all'uso da parte del cliente.|  
|**Righe scadute rimosse/sec**|Numero medio di righe scadute rimosse dai cursori, al secondo.|  
|**Righe scadute interessate/sec**|Numero medio di righe scadute interessate dai cursori, al secondo.|  
|**Righe restituite/sec**|Numero medio di righe restituite dai cursori, al secondo.|  
|**Righe interessate/sec**|Numero medio di righe interessate dai cursori, al secondo.|  
|**Righe provvisoriamente eliminate interessate/sec**|Numero medio di righe in scadenza interessate dai cursori, al secondo. Una riga è in scadenza se la transazione che l'ha eliminata è ancora attiva (cioè non ne è stato ancora eseguito il commit o l'interruzione).|  
  
## <a name="see-also"></a>Vedere anche  
 [XTP &#40;OLTP In memoria&#41; i contatori delle prestazioni](../../integration-services/performance/performance-counters.md)  
  
  
