---
title: Elemento AllowDrillThrough (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllowDrillThrough Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowDrillThrough
helpviewer_keywords:
- AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79abc9833c111c472776d0713a0ca50888cae27d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090851"
---
# <a name="allowdrillthrough-element-assl"></a>Elemento AllowDrillThrough (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|`False`|  
|Cardinalità|0-1: Elemento facoltativo che può verificarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento MiningModel](../objects/miningmodel-element-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono ai padri di `AllowDrillThrough` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission> e <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Drill-through sulle strutture di data mining  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] è possibile definire autorizzazioni `AllowDrillthrough` per strutture di data mining e modelli di data mining. Quando si assegna questa autorizzazione a un ruolo, qualsiasi membro del ruolo può eseguire query sul modello di data mining e restituire le colonne della struttura non incluse nel modello. Si supponga di creare un modello che utilizza solo le colonne relative al codice, al reddito e agli acquisti del cliente. Se si abilita il drill-through sul modello, gli utenti possono restituire le informazioni nelle altre colonne della struttura di data mining, ad esempio nomi o messaggi di posta elettronica del cliente.  
  
 Pertanto, per proteggere i dati sensibili, è necessario prestare attenzione nell'aggiunta di colonne alla struttura di data mining. Concedere inoltre l'autorizzazione `AllowDrillthrough` su una struttura solo quando necessario.  
  
 Per eseguire il drill-through nelle colonne della struttura, utilizzare una query con uno dei formati seguenti:  
  
 `SELECT * FROM <structure>.CASES`  
  
 o Gestione configurazione  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
