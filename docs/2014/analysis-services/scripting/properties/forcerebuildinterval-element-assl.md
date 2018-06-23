---
title: Elemento ForceRebuildInterval (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ForceRebuildInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForceRebuildInterval
helpviewer_keywords:
- ForceRebuildInterval element
ms.assetid: d068f92e-4213-471c-a3a4-aec5af4b8ebf
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e3b05eaf87d17c730186dd1b9c7385f3d323ccf4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158538"
---
# <a name="forcerebuildinterval-element-assl"></a>Elemento ForceRebuildInterval (ASSL)
  Determina la quantità di tempo, da quando diventa disponibile un'immagine OLAP (MOLAP) multidimensionale aggiornata, dopo il quale viene avviata la creazione di un'immagine MOLAP in modo incondizionato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <ForceRebuildInterval>...</ForceRebuildInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Durata XML|  
|Valore predefinito|Infinite|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `ForceRebuildInterval` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  