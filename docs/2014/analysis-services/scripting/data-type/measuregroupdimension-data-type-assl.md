---
title: Tipo di dati Groupdimension (ASSL) | Microsoft Docs
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
- MeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupDimension
helpviewer_keywords:
- MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcbba7071e1f2efc8ede59259a48a334652de81
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249121"
---
# <a name="measuregroupdimension-data-type-assl"></a>Tipo di dati GroupDimension (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta la relazione tra una dimensione e un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[DataMiningMeasureGroupDimension](dimension-data-type-assl.md), [DegenerateMeasureGroupDimension](measuregroupdimension-data-type-assl.md), [ManyToManyMeasureGroupDimension](manytomanymeasuregroupdimension-data-type-assl.md), [ReferenceMeasureGroupDimension](referencemeasuregroupdimension-data-type-assl.md), [RegularMeasureGroupDimension](regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md), [origine](../properties/source-element-binding-assl.md)|  
|Elementi derivati|[Dimensione](../objects/dimension-element-assl.md) ([quote](../collections/dimensions-element-assl.md) insieme [MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 Ogni `MeasureGroupDimension` è un riferimento a una delle dimensioni sul cubo. Questi definiscono quali dimensioni del cubo si applicano al gruppo di misure.  
  
 Il set di attributi fornito determina la granularità (ambito) con la quale sono note le misure sul gruppo di misure. Ad esempio, le misure che rappresentano le vendite del prodotto sono contenute nel gruppo di misure delle Vendite. Le informazioni per queste misure sono archiviate nell'origine dei dati sottostanti con una granularità mensile, piuttosto che settimanale o giornaliera. In questo caso, solo l'attributo Mese sarebbe elencato per il `MeasureGroupDimension` che descrive la relazione tra una dimensione temporale e il gruppo di misure delle Vendite. In rari casi, la granularità potrebbe essere definita in termini di set di attributi. Ad esempio, dato il set di attributi {giorno, settimana, mese anno}, dove il giorno implica settimana e mese, ma la settimana non implica il mese, le misure contenute nel gruppo di misure delle Previsioni potrebbero essere conosciute da mese e settimana, ma non dal giorno.  
  
 Se non è fornito alcun attributo, è come se solo l'attributo chiave per la dimensione venisse elencato (definizione del livello più basso della granularità). Ogni partizione di un gruppo di misure deve avere la stessa granularità. Il set di attributi elencato non deve essere ridondante riguardo alle relazioni tra attributi. Ad esempio, se il mese implica l’anno, la granularità è definita come mese, non mese e anno.  
  
 Un `MeasureGroupDimension` deve includere una gerarchia solo se ha dati specifici al riguardo. (Non c'è modo di selezionare quali gerarchie si applicano a un particolare gruppo di misure). Similmente, deve includere un [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) solo se ha dati specifici al riguardo.  
  
 Ogni gerarchia deve essere un subset delle gerarchie incluse nel [CubeDimension](cubedimension-data-type-assl.md). Non è possibile selezionare i livelli, sebbene alcuni livelli potrebbero essere disabilitati a seconda della granularità del gruppo di misure.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MeasureGroupDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
