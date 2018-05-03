---
title: Misure di elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Measure Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21296ea1c331fa30d3d826fd9f8ca786ad85c176
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="measure-element-assl"></a>Elemento Measure (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Vedere la tabella riportata di seguito.|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Nessuno|  
|[MeasureGroupBinding (out-of-line)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|[Oggetto PerspectiveMeasure](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Misure](../../../analysis-services/scripting/collections/measures-element-assl.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[AggregateFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [BackColor](../../../analysis-services/scripting/properties/backcolor-element-assl.md), [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [FontFlags](../../../analysis-services/scripting/properties/fontflags-element-assl.md), [FontName](../../../analysis-services/scripting/properties/fontname-element-assl.md), [FontSize](../../../analysis-services/scripting/properties/fontsize-element-assl.md), [ForeColor](../../../analysis-services/scripting/properties/forecolor-element-assl.md), [FormatString](../../../analysis-services/scripting/properties/formatstring-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MeasureExpression](../../../analysis-services/scripting/properties/measureexpression-element-assl.md), [nome](../../../analysis-services/scripting/properties/name-element-assl.md), [origine](../../../analysis-services/scripting/properties/source-element-measure-assl.md), [traduzioni](../../../analysis-services/scripting/collections/translations-element-assl.md), [visibile](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|Tutti gli altri|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 I dettagli relativi all'associazione possono essere forniti per una misura. Tali dettagli si comportano come impostazioni predefinite per partizione.  
  
 Nei cubi di dimensioni maggiori possono essere presenti centinaia di misure e gerarchie. Il **DisplayFolder** proprietà definisce l'aspetto utente nel client. Il valore di **DisplayFolder** proprietà può contenere uno o più delle opzioni seguenti:  
  
-   Può essere vuoto, per indicare che la misura non appartiene a una cartella.  
  
-   Contiene il nome di una sola cartella, per indicare che deve essere eseguito il rendering della misura come appartenente a una cartella con lo stesso nome.  
  
-   Contiene più nomi di cartella, separati da una barra rovesciata (\\), che indica una gerarchia di cartelle incorporata.  
  
 Il **DisplayFolder** proprietà si applica anche a misure e gerarchie calcolate.  
  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Measure> e <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
