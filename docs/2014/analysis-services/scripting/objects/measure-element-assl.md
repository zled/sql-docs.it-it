---
title: Misurare l'elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Measure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1079cd11970fad7299064fbbfefe1d476b0daed7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059391"
---
# <a name="measure-element-assl"></a>Elemento Measure (ASSL)
  Definisce una misura.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Measures>  
   <Measure> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <AggregateFunction>...</AggregateFunction>  
            <DataType>...</DataType>  
            <Source>...</Source>  
      <Visible>...</Visible>  
      <MeasureExpression>...</MeasureExpression>  
      <DisplayFolder>...</DisplayFolder>  
      <FormatString>...</FormatString>  
      <BackColor>...</BackColor>  
      <ForeColor>...</ForeColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Measure>  
   <!-- or  -->  
   <Measure xsi:type="AggregationInstanceMeasure">...</Measure> <!-- parent: AggregationInstance -->  
      <!-- or  -->  
   <Measure xsi:type="MeasureBinding">...</Measure> <!-- ancestor: MeasureGroupBinding (out-of-line) -->  
   <!-- or  -->  
   <Measure xsi:type="PerspectiveMeasure">...</Measure> <!-- ancestor: PerspectiveMeasureGroup -->  
</Measures>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[Elemento AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[Gruppo di misure](group-element-assl.md)|None|  
|[MeasureGroupBinding (out-of-line)](../data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Misure](../collections/measures-element-assl.md)|  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Elemento MeasureGroup](../properties/aggregatefunction-element-assl.md), [annotazioni](../collections/annotations-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [DataType](../properties/datatype-element-assl.md), [descrizione](../properties/description-element-assl.md), [DisplayFolder ](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString ](../properties/formatstring-element-assl.md), [ID](../properties/id-element-assl.md), [MeasureExpression](../properties/expression-element-assl.md), [nome](../properties/name-element-assl.md), [origine](../properties/source-element-measure-assl.md), [traduzioni](../collections/translations-element-assl.md), [Visibili](../properties/visible-element-assl.md)|  
|Tutti gli altri|None|  
  
## <a name="remarks"></a>Note  
 I dettagli relativi all'associazione possono essere forniti per una misura. Tali dettagli si comportano come impostazioni predefinite per partizione.  
  
 Nei cubi di dimensioni maggiori possono essere presenti centinaia di misure e gerarchie. La proprietà `DisplayFolder` definisce l'aspetto utente nel client. Il valore della proprietà `DisplayFolder` può contenere una delle opzioni seguenti:  
  
-   Può essere vuoto, per indicare che la misura non appartiene a una cartella.  
  
-   Contiene il nome di una sola cartella, per indicare che deve essere eseguito il rendering della misura come appartenente a una cartella con lo stesso nome.  
  
-   Contiene più nomi di cartella separati da una barra rovesciata (\\), che indica una gerarchia di cartelle incorporata.  
  
 La proprietà `DisplayFolder` si applica anche a misure e gerarchie calcolate.  
  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Measure> e <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
