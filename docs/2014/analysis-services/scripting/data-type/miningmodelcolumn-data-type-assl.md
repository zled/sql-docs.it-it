---
title: Tipo di dati MiningModelColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelColumn
helpviewer_keywords:
- MiningModelColumn data type
ms.assetid: de8bf815-43b4-4983-bdb9-b67e8563be0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b35f260ca14ff416ce5d931457ec741c0736d692
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079461"
---
# <a name="miningmodelcolumn-data-type-assl"></a>Tipo di dati MiningModelColumn (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni relative a una colonna in una [MiningModel](../objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelColumn>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <SourceColumnID>...</SourceColumnID>  
            <Usage>...</Usage>  
            <Translations>...</Translations>  
      <Columns>...</Columns>  
      <ModelingFlags>...</ModelingFlags>  
      <Annotations>...</Annotations>  
</MiningModelColumn>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [colonne](../collections/columns-element-assl.md), [descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [ModelingFlags](../collections/modelingflags-element-assl.md), [nome](../properties/name-element-assl.md) , [SourceColumnID](../properties/sourcecolumnid-element-assl.md), [traduzioni](../collections/translations-element-assl.md), [utilizzo](../properties/usage-element-dimensionattribute-assl.md)|  
|Elementi derivati|[Colonna](../objects/column-element-assl.md) ([colonne](../collections/columns-element-assl.md), raccolta di [MiningModel](../objects/miningmodel-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
