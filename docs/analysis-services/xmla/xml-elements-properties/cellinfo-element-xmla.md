---
title: Elemento CellInfo (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: b2e26f0b4adb6872fed90fcab1a84b2ff83c90a1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="cellinfo-element-xmla"></a>Elemento CellInfo (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Rappresenta i metadati contenuti dall'elemento padre della cella [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) elemento.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
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
  
  
