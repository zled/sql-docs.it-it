---
title: Il tipo di dati MDDataSet (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDDataSet Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6ed0c285f34f55f89b571cf671cf6601e5a81490
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mddataset-data-type-xmla"></a>Tipo di dati MDDataSet (XMLA)
  Definisce un tipo di dati derivato che rappresenta dati multidimensionali restituiti dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Assi](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **MDDataSet** tipo di dati è orientato a OLAP set di righe (o set di dati) necessari per rappresentare dati OLAP in XML. Il contenuto di questo set di righe può variare a seconda dei valori del **contenuto** e **formato** proprietà presenti nel [proprietà](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) insieme il  **Eseguire** metodo. Per ulteriori informazioni sul **contenuto** e **formato** proprietà, vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Per informazioni di base sulle strutture di set di dati OLE DB per OLAP, fare riferimento alla sezione relativa al mapping tra il tipo di dati MDDataSet e OLE DB nella specifica XML for Analysis 1.1. Per un esempio di XML Schema definition language (XSD) completo del **MDDataSet** del tipo di dati, fare riferimento a "Appendice d: MDDataSet ad esempio" la specifica XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
