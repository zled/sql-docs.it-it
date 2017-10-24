---
title: Elemento TestServer (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e41f3ba8bd88de8a3cb1744a29c92be2265fdbb1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="testserver-element-dta"></a>Elemento TestServer (DTA)
  Indica il server di prova da utilizzare durante l'ottimizzazione di un server di produzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Facoltativa. È possibile utilizzarlo una volta per ogni elemento **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Riduzione del carico di ottimizzazione del server di produzione](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

