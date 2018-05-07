---
title: Elemento MiningStructure (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7639078695b80d45f8fc90d6d925ea2335314d15
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="miningstructure-element-assl"></a>Elemento MiningStructure (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce la struttura per un set di modelli di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CacheMode](../../../analysis-services/scripting/properties/cachemode-element-assl.md), [regole di confronto](../../../analysis-services/scripting/properties/collation-element-assl.md), [colonne](../../../analysis-services/scripting/collections/columns-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [descrizione ](../../../analysis-services/scripting/properties/description-element-assl.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md),<br /><br /> [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [Language](../../../analysis-services/scripting/properties/language-element-assl.md), [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md), [stato](../../../analysis-services/scripting/properties/state-element-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 La struttura di data mining definisce le colonne e le associazioni. Dopo avere definito una struttura di data mining, è possibile utilizzare tale struttura per definire molti modelli di data mining. La struttura di data mining e ogni modello che essa contiene possono essere elaborati indipendentemente.  
  
> [!NOTE]  
>  Le proprietà di controllo, **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, e **HoldoutActualSize**, sono state introdotte in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Consentono di definire una partizione su una struttura di data mining che si comporta da set di test per tutti i modelli di data mining associati alla struttura. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] non supportano queste proprietà. Pertanto, se si tenta di utilizzare queste proprietà su un'istanza di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verrà restituito un errore.  
  
## <a name="drillthrough-to-structure-columns"></a>Drill-through alle colonne della struttura  
 In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], è stato aggiunto un nuovo elemento di autorizzazione per il [elemento MiningStructurePermissions &#40;ASSL&#41; ](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) insieme. Se si aggiungono **AllowDrillthrough** autorizzazione sia il [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) e [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md) raccolte, il drill-through sia abilitato dal modello di data mining alla struttura, in modo che i membri di un ruolo che ha **AllowDrillthrough** autorizzazioni per il modello possono eseguire query sul modello di data mining di dati e restituire le colonne della struttura non incluse nel modello.  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario costruire la vista origine dati per mascherare le informazioni sensibili e concedere **AllowDrillthrough** autorizzazioni su una struttura di data mining solo quando necessario. Per altre informazioni, vedere [elemento AllowDrillThrough &#40;ASSL&#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MiningModel &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](../../../analysis-services/scripting/objects/objects-assl.md)   
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](../../../dmx/select-dmx.md)  
  
  
