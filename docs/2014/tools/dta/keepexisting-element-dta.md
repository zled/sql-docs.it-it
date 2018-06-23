---
title: Elemento KeepExisting (DTA) | Documenti Microsoft
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
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a74552aa4cf5b18273c42250f85bc48a794e1731
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069739"
---
# <a name="keepexisting-element-dta"></a>Elemento KeepExisting (DTA)
  Specifica le strutture di progettazione fisica (indici, viste indicizzate o partizionamento) che Ottimizzazione guidata motore di database deve mantenere quando genera l'indicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|`string`, limite della lunghezza imposto dal server.|  
|**Valori consentiti**|**NONE**<br /> Nessuna struttura esistente.<br /><br /> **ALL**<br /> Tutte le strutture esistenti.<br /><br /> **ALIGNED**<br /> Tutte le strutture con partizionamento allineato.<br /><br /> **CL_IDX**<br /> Tutti gli indici cluster nelle tabelle.<br /><br /> **IDX**<br /> Tutti gli indici cluster e non cluster nelle tabelle.<br /><br /> Utilizzare solo uno dei valori seguenti con questo elemento.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Facoltativo. Può utilizzare una sola volta per ogni `TuningOptions` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  