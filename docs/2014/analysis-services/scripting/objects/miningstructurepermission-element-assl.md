---
title: Elemento MiningStructurePermission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructurePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructurePermission
helpviewer_keywords:
- MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 89521b4201e3956ab6d44d95d7234321a0948f56
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197621"
---
# <a name="miningstructurepermission-element-assl"></a>Elemento MiningStructurePermission (ASSL)
  Definisce le autorizzazioni che i membri di un [ruolo](role-element-assl.md) elemento dispone di un singolo [MiningStructure](miningstructure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructurePermissions>  
   <MiningStructurePermission xsi:type="Permission">  
      <AllowDrillthrough>...</AllowDrillthrough>  
  
      <!-- This element also inherits all the child elements listed in Permission -->  
   </MiningStructurePermission>  
</MiningStructurePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../data-type/permission-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] l'autorizzazione `AllowDrillthrough` è stata estesa in modo da applicarla a una struttura di data mining. Quando si assegna questa autorizzazione a un ruolo, qualsiasi utente membro di tale ruolo può eseguire una query direttamente sulla struttura di data mining utilizzando la sintassi seguente:  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 Inoltre, se l'autorizzazione `AllowDrillthrough` è abilitata sia sulla struttura di data mining sia sul modello di data mining, gli utenti possono eseguire una query sulle colonne della struttura non incluse nel modello utilizzando la sintassi seguente:  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 Si supponga di creare un modello utilizzando solo le colonne relative al codice, al reddito e agli acquisti del cliente. Il drill-through consente a un utente di restituire le altre colonne della struttura non incluse nel modello di data mining, ad esempio quelle relative alle informazioni di contatto del cliente.  
  
 Pertanto, per proteggere dati sensibili o informazioni personali, è necessario costruire la vista origine dati in modo da mascherare le informazioni personali e concedere l'autorizzazione `AllowDrillthrough` su una struttura solo se necessario.  
  
 Per altre informazioni, vedere [Query drill-through &#40;Data mining&#41;](../../data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
