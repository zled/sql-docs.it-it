---
title: Elemento MiningStructurePermission (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MiningStructurePermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MiningStructurePermission
helpviewer_keywords: MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 56d22082d2e948881de36ae0a834ff68be2ad4be
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="miningstructurepermission-element-assl"></a>Elemento MiningStructurePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce le autorizzazioni che i membri di un [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento dispone di un singolo [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], l'autorizzazione **AllowDrillthrough** è stato esteso per applicarla a una struttura di data mining. Quando si assegna questa autorizzazione a un ruolo, qualsiasi utente membro di tale ruolo può eseguire una query direttamente sulla struttura di data mining utilizzando la sintassi seguente:  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 Inoltre, se **AllowDrillthrough** è abilitato nella struttura di data mining e il modello di data mining, gli utenti possono recuperare le colonne della struttura non incluse nel modello di data mining utilizzando la sintassi seguente:  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 Si supponga di creare un modello utilizzando solo le colonne relative al codice, al reddito e agli acquisti del cliente. Il drill-through consente a un utente di restituire le altre colonne della struttura non incluse nel modello di data mining, ad esempio quelle relative alle informazioni di contatto del cliente.  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario costruire la vista origine dati per mascherare informazioni personali e concedere **AllowDrillthrough** autorizzazioni su una struttura solo quando necessario.  
  
 Per altre informazioni, vedere [Query drill-through &#40;Data mining&#41;](../../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
