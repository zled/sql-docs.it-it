---
title: Elemento AllowDrillThrough (ASSL) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 25bad363975494fc8bd6c8cb343a165d8bb85f85
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036012"
---
# <a name="allowdrillthrough-element-assl"></a>Elemento AllowDrillThrough (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina se il drill-through è permesso sull'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|**False**|  
|Cardinalità|0-1: Elemento facoltativo che può verificarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **AllowDrillThrough** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, e <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Drill-through sulle strutture di data mining  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], è possibile definire **AllowDrillthrough** le autorizzazioni per strutture di data mining, nonché modelli di data mining. Quando si assegna questa autorizzazione a un ruolo, qualsiasi membro del ruolo può eseguire query sul modello di data mining e restituire le colonne della struttura non incluse nel modello. Si supponga di creare un modello che utilizza solo le colonne relative al codice, al reddito e agli acquisti del cliente. Se si abilita il drill-through sul modello, gli utenti possono restituire le informazioni nelle altre colonne della struttura di data mining, ad esempio nomi o messaggi di posta elettronica del cliente.  
  
 Pertanto, per proteggere i dati sensibili, è necessario prestare attenzione nell'aggiunta di colonne alla struttura di data mining. Concedere inoltre l'autorizzazione **AllowDrillthrough** su una struttura solo quando necessario.  
  
 Per eseguire il drill-through nelle colonne della struttura, utilizzare una query con uno dei formati seguenti:  
  
 `SELECT * FROM <structure>.CASES`  
  
 o  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
