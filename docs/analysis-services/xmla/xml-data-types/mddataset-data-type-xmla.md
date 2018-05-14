---
title: Il tipo di dati MDDataSet (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b5f42140d8987cb36ea95c4c4314798a1ee7633
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="mddataset-data-type-xmla"></a>Tipo di dati MDDataSet (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 Il **MDDataSet** tipo di dati è orientato a OLAP set di righe (o set di dati) necessari per rappresentare dati OLAP in XML. Il contenuto di questo set di righe può variare a seconda dei valori del **contenuto** e **formato** proprietà presenti nel [proprietà](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) insieme il  **Eseguire** metodo. Per ulteriori informazioni sul **contenuto** e **formato** delle proprietà, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Per informazioni di base sulle strutture di set di dati OLE DB per OLAP, fare riferimento alla sezione relativa al mapping tra il tipo di dati MDDataSet e OLE DB nella specifica XML for Analysis 1.1. Per un esempio di XML Schema definition language (XSD) completo del **MDDataSet** del tipo di dati, fare riferimento a "Appendice d: MDDataSet ad esempio" la specifica XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
