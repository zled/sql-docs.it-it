---
title: Elemento Row (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78745ed581642092c17190c4b81eb3f9ab6df853
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="row-element-xmla"></a>Elemento row (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una singola riga di dati per un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento che contiene i dati tabulari restituiti da una [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
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
  
 Per ulteriori informazioni sull'assegnazione di nomi di colonna e informazioni sullo schema per i dati tabulari, vedere [il tipo di dati di set di righe & #40; XMLA & #41; ](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
