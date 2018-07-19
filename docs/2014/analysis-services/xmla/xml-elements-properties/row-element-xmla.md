---
title: Elemento Row (XMLA) | Microsoft Docs
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
- row Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17bc202bb7e1d2c0701b478409b02f4bbb160958
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223991"
---
# <a name="row-element-xmla"></a>Elemento row (XMLA)
  Contiene una singola riga di dati per un [radice](root-element-xmla.md) elemento contenente dati tabulari restituiti da una [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) chiamata al metodo.  
  
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
|Elementi padre|[radice](root-element-xmla.md) (usando il [set di righe](../xml-data-types/rowset-data-type-xmla.md) tipo di dati)|  
|Elementi figlio|Uno o più elementi di colonna.|  
  
## <a name="remarks"></a>Note  
 Ogni riga restituita da un elemento `root` contenente dati tabulari ha un elemento `row` corrispondente. Ogni colonna nell'elemento `root` è rappresentata da un elemento XML distinto. Il valore della colonna per l'elemento `row` corrisponde ai dati contenuti nell'elemento XML, mentre il nome della colonna corrisponde al nome dell'elemento XML.  
  
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
  
 Se un elemento di colonna contiene un errore, un elemento `Error` fornisce le informazioni sull'errore, come descritto nell'esempio seguente:  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Per altre informazioni sulla denominazione delle colonne e le informazioni sullo schema per i dati tabulari, vedere [tipo di dati di set di righe &#40;XMLA&#41;](../xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
