---
title: Elemento (ASSL) target | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 98ec5c729f5735343f5eaa87e5232fcfb138cf38
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045779"
---
# <a name="target-element-assl"></a>Elemento Target (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica la destinazione del [azione](../../../analysis-services/scripting/objects/action-element-assl.md) elemento.  
  
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
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore previsto di questo elemento dipende dal valore della [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) (elemento) per l'elemento padre **azione**. Nella tabella seguente vengono descritti i valori previsti di **destinazione** in base al valore di **TargetType**.  
  
|Valore di TargetType|Valore previsto|  
|----------------------|--------------------|  
|*Cube*|Nome di un cubo.|  
|*Celle*|Espressione di sottocubo.|  
|*Set*|Espressione set o nome di un set denominato.<br /><br /> Nota: Non è possibile utilizzare un'istruzione sub-SELECT.|  
|*Gerarchia, HierarchyMembers*|Nome di una gerarchia.|  
|*Dimensione, DimensionMembers*|Nome di una dimensione.|  
|*Livello, LevelMembers*|Nome di un livello.|  
|*Attributo, AttributeMembers*|Nome di un attributo.|  
  
 L'elemento che corrisponde al padre di **destinazione** nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
