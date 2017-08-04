---
title: Elemento FeatureSet (DTA) | Documenti Microsoft
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
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 44937796c574f852b47de5bd681a8550b0aa3f6e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="featureset-element-dta"></a>Elemento FeatureSet (DTA)
  Contiene le strutture di progettazione fisica, ad esempio indici o viste indicizzate, che dovranno essere utilizzate da Ottimizzazione guidata motore di database durante l'analisi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valori consentiti**|**IDX_IV**<br /> Indici e viste indicizzate.<br /><br /> **IDX**<br /> Solo indici.<br /><br /> **IV**<br /> Solo viste indicizzate.<br /><br /> **NCL_IDX**<br /> Solo indici non cluster.<br /><br /> Con questo elemento utilizzare solo uno di questi valori.|  
|**Valore predefinito**|**IDX**|  
|**Occorrenza**|Obbligatorio una sola volta per ogni elemento **TuningOptions** , a meno che non venga usato l'elemento **DropOnlyMode** . Se si usa **DropOnlyMode** , non è possibile usare **FeatureSet**. Questi elementi si escludono a vicenda.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
