---
title: Elemento HideMemberIf (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0e01cbbf403636bf42a806ba516f9947eaab20e4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="hidememberif-element-assl"></a>Elemento HideMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indica se e quando un membro di un livello deve essere nascosto per le applicazioni client.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Mai*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Mai*|I membri non vengono mai nascosti.|  
|*OnlyChildWithNoName*|Un membro viene nascosto quando è l'unico figlio del relativo padre e il suo nome è vuoto.|  
|*OnlyChildWithParentName*|Un membro viene nascosto quando è l'unico elemento figlio del relativo padre e il nome corrisponde a quello del padre.|  
|*NoName*|Un membro viene nascosto quando il suo nome è vuoto.|  
|*ParentName*|Un membro viene nascosto quando il suo nome è identico a quello del padre.|  
  
## <a name="remarks"></a>Osservazioni  
 L'enumerazione che corrisponde ai valori consentiti per **HideMemberIf** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
