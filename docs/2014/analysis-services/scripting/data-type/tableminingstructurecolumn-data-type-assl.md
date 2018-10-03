---
title: Tipo di dati TableMiningStructureColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableMiningStructureColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableMiningStructureColumn
helpviewer_keywords:
- TableMiningStructureColumn data type
ms.assetid: 350358b0-f2fc-43c3-957d-884c59fa879e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5195118322ff7de4b618dbbe11743639101c625
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082771"
---
# <a name="tableminingstructurecolumn-data-type-assl"></a>Tipo di dati TableMiningStructureColumn (ASSL)
  Definisce un tipo di dati derivato che rappresenta un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) elemento che contiene tabelle nidificate, a differenza dei valori scalari associati con la [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) elemento che contiene valori scalari.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TableMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <ForeignKeyColumn>..</ForeignKeyColumn>  
   <SourceMeasureGroup>..</SourceMeasureGroup>  
   <Columns>..</Columns>  
   <Translations>..</Translations>  
</TableMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[MiningStructureColumn](miningstructurecolumn-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le colonne](../collections/columns-element-assl.md), [ForeignKeyColumn](../objects/column-element-assl.md), [SourceMeasureGroup](../objects/group-element-assl.md), [traduzioni](../collections/translations-element-assl.md)|  
|Elementi derivati|[Colonna](../objects/column-element-assl.md) ([colonne](../collections/columns-element-assl.md) insieme [MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
