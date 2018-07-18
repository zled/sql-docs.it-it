---
title: Tipo di dati MDDataSet (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDDataSet Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c1580365cc6c7949c552333728b5083b96f7ef9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165322"
---
# <a name="mddataset-data-type-xmla"></a>Tipo di dati MDDataSet (XMLA)
  Definisce un tipo di dati derivato che rappresenta dati multidimensionali restituiti dal [Execute](../xml-elements-methods-execute.md) (metodo).  
  
 **Namespace** urn: schemas-microsoft-com: XML-analysis: mddataset  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Set di risultati](resultset-data-type-xmla.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Assi](../xml-elements-properties/axes-element-xmla.md), [CellData](../xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Il tipo di dati `MDDataSet` fornisce il set di righe orientato a OLAP (o set di dati) necessario per rappresentare dati OLAP in XML. Il contenuto di questo set di righe può variare a seconda dei valori del `Content` e `Format` proprietà presenti nel [delle proprietà](../xml-elements-properties/properties-element-xmla.md) raccolta del `Execute` (metodo). Per altre informazioni sul `Content` e `Format` proprietà, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Per informazioni di base sulle strutture di set di dati OLE DB per OLAP, fare riferimento alla sezione relativa al mapping tra il tipo di dati MDDataSet e OLE DB nella specifica XML for Analysis 1.1. Per un esempio completo in linguaggio XSD (XML Schema Definition) del tipo di dati `MDDataSet`, fare riferimento all'appendice D della specifica XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
