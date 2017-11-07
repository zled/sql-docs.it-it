---
title: Elemento CellInfo (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CellInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a7b38201d5ba5c051cfacfb139ea52a6b93fb09
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cellinfo-element-xmla"></a>Elemento CellInfo (XMLA)
  Rappresenta i metadati contenuti dall'elemento padre della cella [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementi figlio|Una o più definizioni di proprietà della cella|  
  
## <a name="remarks"></a>Osservazioni  
 Il **CellInfo** elemento contiene una raccolta di proprietà della cella per le celle incluse nel set di dati multidimensionale restituito da un **radice** elemento utilizzando il **MDDataSet**tipo di dati. Ogni proprietà della cella nel **CellInfo** è definito l'elemento da un elemento XML separato, ognuno con un **nome** attributo e un **tipo** attributo. Il **nome** attributo della proprietà della cella corrisponde al nome di OLE DB per la proprietà di cella OLAP rappresentata dall'elemento, XML e **tipo** attributo rappresenta il tipo di dati XML della cella proprietà. Il nome dell'elemento XML viene utilizzato per identificare il valore della proprietà della cella per le celle contenute nel **CellData** elemento il **radice** elemento.  
  
 Nella sintassi seguente è descritta una definizione di proprietà della cella:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Le proprietà disponibili e i relativi valori possono essere ottenuti utilizzando il tipo di richiesta DISCOVER_PROPERTIES con il metodo **Discover** . Non è previsto un ordine obbligatorio per le proprietà elencate nell'elemento **PropertyList** .  
  
 Un provider può specificare i valori predefiniti per singole proprietà di membro o della cella nel **AxisInfo** o **CellInfo** sezione. I valori predefiniti possono fornire un risultato più piccolo se la proprietà ha sempre o quasi sempre lo stesso valore. Per indicare un valore predefinito per una proprietà, il**predefinito** elemento facoltativamente può essere specificato come elemento figlio di uno degli elementi di definizione di proprietà della cella. L'assenza di una proprietà del membro o della cella nel risultato indica pertanto che l'impostazione predefinita specificata corrisponde al valore per la proprietà della cella.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come le proprietà della cella VALUE, FORMATTED_VALUE e FORMAT_STRING sono rappresentate nel **CellInfo** elemento.  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

