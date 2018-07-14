---
title: Elemento MiningModel (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MiningModel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModel
helpviewer_keywords:
- MiningModel element
ms.assetid: a61d935f-c8f6-457d-ad0c-44f58bb286f5
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ba98443b953f4107b209dd06af74349a81bb2a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224541"
---
# <a name="miningmodel-element-assl"></a>Elemento MiningModel (ASSL)
  Definisce un singolo modello di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModels>  
      <MiningModel>  
      <Name>...</Name>  
            <ID>...</ID>  
      <Description>...</<Descrip  
            <Algorithm>...</Algorithm>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <AlgorithmParameters>...</AlgorithmParameters>  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <Translations>...</Translations>  
      <Columns>...</Columns>  
      <State>...</State>  
      <MiningModelPermissions>...</MiningModelPermissions>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Annotations>...</Annotations>  
            <ddl100_100:FoldingParameters>   </FoldingParameters>  
   </MiningModel>  
</MiningModels>  
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
|Elementi padre|[MiningModels](../collections/miningmodels-element-assl.md)|  
|Elementi figlio|[Algoritmo](../properties/algorithm-element-assl.md), [AlgorithmParameters](algorithmparameter-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [delle regole di confronto](../properties/collation-element-assl.md), [ Le colonne](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [linguaggio](../properties/language-element-assl.md), [ LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md), [nome](../properties/name-element-assl.md), [stato](../properties/state-element-assl.md), [ Le traduzioni](../collections/translations-element-assl.md),<br /><br /> [FoldingParameters](../properties/foldingparameters-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `FoldingParameters` del modello di data mining è destinato a un uso interno da parte del server e non è supportato per l'utilizzo nelle istruzioni DDL.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningModel>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
