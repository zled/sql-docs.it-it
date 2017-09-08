---
title: Elemento MiningModelPermission (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningModelPermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2cd366179355590dca84fb84f8a00e8dfc103a3f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelpermission-element-assl"></a>Elemento MiningModelPermission (ASSL)
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
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], è possibile abilitare il drill-through sulle strutture di data mining aggiungendo il **AllowDrillthrough** dell'autorizzazione per la [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) insieme. Se **AllowDrillthrough** è abilitato nella struttura di data mining sia il modello di data mining, qualsiasi membro di un ruolo che ha [elemento AllowDrillThrough &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) autorizzazioni per il modello possono eseguire una query il modello di data mining e restituire le colonne della struttura non incluse nel modello, utilizzando la sintassi seguente:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario concedere l' autorizzazione **AllowDrillthrough** su un modello di data mining solo quando è necessario. Per ulteriori informazioni, vedere [elemento AllowDrillThrough &#40; ASSL &#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
