---
title: Tipo di dati TableMiningStructureColumn (ASSL) | Documenti Microsoft
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
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9a57859ca60ae7fa83ec4bb4ea8f6a4e742a74f3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054619"
---
# <a name="tableminingstructurecolumn-data-type-assl"></a>Tipo di dati TableMiningStructureColumn (ASSL)
  Definisce un tipo di dati derivato che rappresenta un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) elemento che contiene tabelle nidificate, a differenza dei valori scalari associati con il [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) elemento che contiene valori scalari.  
  
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
|Elementi derivati|[Colonna](../objects/column-element-assl.md) ([le colonne](../collections/columns-element-assl.md) insieme [MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  