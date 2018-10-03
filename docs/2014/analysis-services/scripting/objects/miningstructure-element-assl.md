---
title: Elemento MiningStructure (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningStructure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d03e52ccb38dc35fada602b6a293d018150efd5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052091"
---
# <a name="miningstructure-element-assl"></a>Elemento MiningStructure (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MiningStructures](../collections/miningstructures-element-assl.md)|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [CacheMode](../properties/cachemode-element-assl.md), [regole di confronto](../properties/collation-element-assl.md), [colonne](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [descrizione ](../properties/description-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../properties/holdoutseed-element.md),<br /><br /> [ID](../properties/id-element-assl.md), [Language](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModels](../collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md), [Name](../properties/name-element-assl.md), [origine](../properties/source-element-binding-assl.md), [stato](../properties/state-element-assl.md), [traduzioni](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 La struttura di data mining definisce le colonne e le associazioni. Dopo avere definito una struttura di data mining, è possibile utilizzare tale struttura per definire molti modelli di data mining. La struttura di data mining e ogni modello che essa contiene possono essere elaborati indipendentemente.  
  
> [!NOTE]  
>  Le proprietà di controllo, `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` e `HoldoutActualSize`, sono state introdotte in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Consentono di definire una partizione su una struttura di data mining che si comporta da set di test per tutti i modelli di data mining associati alla struttura. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] non supportano queste proprietà. Pertanto, se si tenta di utilizzare queste proprietà su un'istanza di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verrà restituito un errore.  
  
## <a name="drillthrough-to-structure-columns"></a>Drill-through alle colonne della struttura  
 Nelle [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], è stato aggiunto un nuovo elemento di autorizzazione di [elemento MiningStructurePermissions &#40;ASSL&#41; ](../collections/miningstructurepermissions-element-assl.md) raccolta. Se si aggiungono `AllowDrillthrough` l'autorizzazione per entrambe le [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) e [MiningModelPermission](miningmodelpermission-element-assl.md) raccolte, drill-through sia abilitato dal modello di data mining alla struttura, in modo che i membri di un ruolo che dispone di `AllowDrillthrough` delle autorizzazioni per il modello possono eseguire query sul modello di data mining di dati e restituire le colonne della struttura non incluse nel modello.  
  
 Pertanto, per proteggere dati riservati o informazioni personali, è necessario costruire la vista origine dati in modo da mascherare le informazioni confidenziali e concedere l'autorizzazione `AllowDrillthrough` su una struttura di data mining solo se necessario. Per altre informazioni, vedere [elemento AllowDrillThrough &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)   
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](/sql/dmx/select-dmx)  
  
  
