---
title: Elemento Row (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- row Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e28026dda3ddb43e1ed43ac427851b8fa4ff773c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="row-element-xmla"></a>Elemento row (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene una singola riga di dati per un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento che contiene i dati tabulari restituiti da una [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) (utilizzando la [set di righe](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) tipo di dati)|  
|Elementi figlio|Uno o più elementi di colonna.|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni riga restituita da un **radice** elemento che contiene i dati tabulari ha un corrispondente **riga** elemento. Ogni colonna di **radice** elemento è rappresentato da un elemento XML separato. Il valore della colonna per il **riga** elemento corrisponde ai dati contenuti nell'elemento XML, mentre il nome della colonna corrisponde al nome dell'elemento XML.  
  
 Ci sono due modalità per esprimere un valore null per una colonna all'interno di una riga:  
  
-   Un elemento della colonna mancante implica che la colonna è null.  
  
-   L'elemento della colonna può utilizzare l'attributo `xsi:nil='true'` per indicare che ha un valore null.  
  
 Se, ad esempio, una riga ha una singola colonna denominata Store_Name e il valore è NULL, tale riga può essere rappresentata nel modo seguente:  
  
```  
<row>  
</row>  
```  
  
 Oppure:  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 Se un elemento di colonna contiene un errore, un **errore** elemento fornisce informazioni sull'errore, come descritto nell'esempio seguente:  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Per ulteriori informazioni sull'assegnazione di nomi di colonna e informazioni sullo schema per i dati tabulari, vedere [il tipo di dati di set di righe &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
