---
title: Elemento Partitioning (DTA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 379e5dae0c70278b7c0b576190faffea84c8fa19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068375"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|`string`, lunghezza illimitata.|  
|**Valori consentiti**|**NONE**<br /> Nessun partizionamento.<br /><br /> **FULL**<br /> Partizionamento completo. Migliora le prestazioni.<br /><br /> **ALIGNED**<br /> Partizionamento allineato. Migliora la gestibilità.<br /><br /> Utilizzare solo uno dei valori seguenti con questo elemento.<br /><br /> **ALIGNED** significa che nell'indicazione generata da Ottimizzazione guidata motore di database ogni indice proposto viene partizionato esattamente come la tabella sottostante per la quale viene definito l'indice. Gli indici non cluster in una vista indicizzata sono allineati in base alla vista indicizzata.|  
|**Valore predefinito**|**NONE**|  
|**Occorrenza**|Obbligatorio una sola volta per l'elemento `TuningOptions`, a meno che non venga utilizzato l'elemento `DropOnlyMode`. Se `DropOnlyMode` viene utilizzata, non è possibile utilizzare `Partitioning`. Questi elementi si escludono a vicenda.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  