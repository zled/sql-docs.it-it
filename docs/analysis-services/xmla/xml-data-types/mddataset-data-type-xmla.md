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
ms.openlocfilehash: 986fade6d9db3d6170d47181ac960d15febdf260
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573923"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni tra tipi di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Assi](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Remarks  
 Il **MDDataSet** tipo di dati è orientato a OLAP set di righe (o set di dati) necessari per rappresentare dati OLAP in XML. Il contenuto di questo set di righe può variare a seconda dei valori del **contenuto** e **formato** proprietà presenti nel [proprietà](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) insieme il  **Eseguire** metodo. Per ulteriori informazioni sul **contenuto** e **formato** delle proprietà, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Per informazioni di base sulle strutture di set di dati OLE DB per OLAP, fare riferimento alla sezione relativa al mapping tra il tipo di dati MDDataSet e OLE DB nella specifica XML for Analysis 1.1. Per un esempio di XML Schema definition language (XSD) completo del **MDDataSet** del tipo di dati, fare riferimento a "Appendice d: MDDataSet ad esempio" la specifica XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vedere anche
 [Tipi di dati XML &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
