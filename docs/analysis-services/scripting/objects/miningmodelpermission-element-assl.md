---
title: Elemento MiningModelPermission (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f05a12d5be30826e5a826320f2eb5a6c604456e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031272"
---
# <a name="miningmodelpermission-element-assl"></a>Elemento MiningModelPermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce i membri di autorizzazioni di un [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento dispone di un singolo [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|  
|Elementi figlio|[AllowBrowsing](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], è possibile abilitare il drill-through sulle strutture di data mining aggiungendo il **AllowDrillthrough** dell'autorizzazione per la [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) insieme. Se **AllowDrillthrough** è abilitata la struttura di data mining sia il modello di data mining, qualsiasi membro di un ruolo che ha [AllowDrillThrough elemento &#40;ASSL&#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) le autorizzazioni per il modello possono eseguire una query modello di dati di data mining e restituiscono le colonne della struttura non incluse nel modello, utilizzando la sintassi seguente:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario concedere l' autorizzazione **AllowDrillthrough** su un modello di data mining solo quando è necessario. Per altre informazioni, vedere [elemento AllowDrillThrough &#40;ASSL&#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
