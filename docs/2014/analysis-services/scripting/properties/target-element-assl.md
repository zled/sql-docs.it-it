---
title: Elemento (ASSL) di destinazione | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Target Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Target
helpviewer_keywords:
- Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 65150d66769a2ebdb67609989efbc1a7f81e9f89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062477"
---
# <a name="target-element-assl"></a>Elemento Target (ASSL)
  Identifica la destinazione del [azione](../objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../objects/action-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore previsto di questo elemento dipende dal valore della [TargetType](targettype-element-assl.md) per l'elemento padre `Action`. Nella tabella seguente vengono descritti i valori previsti di `Target` in base al valore di `TargetType`.  
  
|Valore di TargetType|Valore previsto|  
|----------------------|--------------------|  
|*Cube*|Nome di un cubo.|  
|*Celle*|Espressione di sottocubo.|  
|*Set*|Espressione set o nome di un set denominato. **Nota:** un'istruzione sub-SELECT non può essere utilizzata.|  
|*Gerarchia, HierarchyMembers*|Nome di una gerarchia.|  
|*Dimensione, DimensionMembers*|Nome di una dimensione.|  
|*Livello, LevelMembers*|Nome di un livello.|  
|*Attributo, AttributeMembers*|Nome di un attributo.|  
  
 L'elemento che corrisponde al padre di `Target` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  