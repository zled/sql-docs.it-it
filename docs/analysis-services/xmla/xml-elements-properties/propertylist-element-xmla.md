---
title: Elemento PropertyList (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3e773de16e65aa9c7f1be521214088aa9f06b369
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036709"
---
# <a name="propertylist-element-xmla"></a>Elemento PropertyList (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di XML delle proprietà Analysis (XMLA) usate per la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Proprietà](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|Elementi figlio|Proprietà XMLA (vedere la sezione Osservazioni)|  
  
## <a name="remarks"></a>Note  
 L'elemento **PropertyList** contiene una raccolta di proprietà XMLA, ognuna delle quali consente all'utente di controllare alcuni aspetti del metodo **Discover** o **Execute** , ad esempio la definizione delle informazioni necessarie per connettersi all'origine dati, la specifica del formato del set di risultati o la specifica delle impostazioni locali con cui devono essere formattati i dati. Ogni proprietà XMLA nell'elemento **PropertyList** è definita da un elemento XML separato. Il valore della proprietà XMLA corrisponde ai dati contenuti nell'elemento XML, mentre il nome proprietà XMLA corrisponde al nome dell'elemento XML.  
  
 Le proprietà disponibili e i relativi valori possono essere ottenuti utilizzando il tipo di richiesta DISCOVER_PROPERTIES con il metodo **Discover** . Non è previsto un ordine obbligatorio per le proprietà elencate nell'elemento **PropertyList** .  
  
 Per altre informazioni sulle proprietà XMLA supportate da Analysis Services, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
## <a name="example"></a>Esempio  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
