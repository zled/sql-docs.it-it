---
title: Elemento Partitioning (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c84705492db53c29b2f430d6e105a239e4393de
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="partitioning-element-dta"></a>Elemento Partitioning (DTA)
  Contiene lo schema di partizione che dovrà essere utilizzato da Ottimizzazione guidata motore di database durante l'analisi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valori consentiti**|**NONE**<br /> Nessun partizionamento.<br /><br /> **FULL**<br /> Partizionamento completo. Migliora le prestazioni.<br /><br /> **ALIGNED**<br /> Partizionamento allineato. Migliora la gestibilità.<br /><br /> Utilizzare solo uno dei valori seguenti con questo elemento.<br /><br /> **ALIGNED** significa che nell'indicazione generata da Ottimizzazione guidata motore di database ogni indice proposto viene partizionato esattamente come la tabella sottostante per la quale viene definito l'indice. Gli indici non cluster in una vista indicizzata sono allineati in base alla vista indicizzata.|  
|**Valore predefinito**|**NONE**|  
|**Occorrenza**|Obbligatorio una sola volta per l'elemento **TuningOptions** , a meno che non venga usato l'elemento **DropOnlyMode** . Se si usa **DropOnlyMode** , non è possibile usare **Partitioning**. Questi elementi si escludono a vicenda.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
