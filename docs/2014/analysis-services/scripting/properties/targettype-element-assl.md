---
title: Elemento TargetType (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TargetType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e4a36c4ca0e38fe00990f2185685205840eafc66
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158750"
---
# <a name="targettype-element-assl"></a>Elemento TargetType (ASSL)
  Identifica il tipo di elemento dell'elemento identificato nel [destinazione](target-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../objects/action-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Cube*|La destinazione dell'azione è un cubo.|  
|*Celle*|La destinazione dell'azione è un sottocubo.|  
|*Set*|La destinazione dell'azione è un set.|  
|*Hierarchy*|La destinazione dell'azione è una gerarchia.|  
|*Level*|La destinazione dell'azione è un livello.|  
|*DimensionMembers*|La destinazione dell'azione sono i membri di una dimensione.|  
|*HierarchyMembers*|La destinazione dell'azione sono i membri di una gerarchia.|  
|*LevelMembers*|La destinazione dell'azione sono i membri di un livello.|  
|*AttributeMembers*|La destinazione dell'azione sono i membri di un attributo.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `TargetType` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L'elemento che corrisponde al padre di `TargetType` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  