---
title: Elemento Perspective (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Perspective Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ed510b7c4b9a9c023c6bad875ed2e6293ac2ac4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168231"
---
# <a name="perspective-element-assl"></a>Elemento Perspective (ASSL)
  Definisce i dettagli di una prospettiva di un [cubo](cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
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
|Elementi padre|[Prospettive](../collections/perspectives-element-assl.md)|  
|Elementi figlio|[Le azioni](../collections/actions-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [calcoli](../collections/calculations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultMeasure](measure-element-assl.md), [ Descrizione](../properties/description-element-assl.md), [quote](../collections/dimensions-element-assl.md), [ID](../properties/id-element-assl.md), [KPI](../collections/kpis-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../collections/groups-element-assl.md), [Name](../properties/name-element-assl.md), [traduzioni](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Una prospettiva fornisce un subset di un cubo, con la selezione di dimensioni, gerarchie, attributi e altri dettagli da specificare e la definizione della sezione di dati da includere. Una prospettiva appartiene a un singolo cubo. Non è possibile ignorare o aggiungere oggetti all'interno di una prospettiva. Tutte le dimensioni, le gerarchie e gli altri dettagli devono essere presenti nel cubo sottostante. Non è possibile includere oggetti e contrassegnarli come non visibili.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
