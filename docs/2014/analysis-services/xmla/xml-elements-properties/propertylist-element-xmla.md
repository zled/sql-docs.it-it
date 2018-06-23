---
title: Elemento PropertyList (XMLA) | Documenti Microsoft
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
- PropertyList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4b49ad0cf03ce331a00a7eefc9f1302176d89e74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055355"
---
# <a name="propertylist-element-xmla"></a>Elemento PropertyList (XMLA)
  Contiene una raccolta di XML per le proprietà Analysis (XMLA) utilizzate per la [Discover](../xml-elements-methods-discover.md) e [Execute](../xml-elements-methods-execute.md) metodi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Proprietà](properties-element-xmla.md)|  
|Elementi figlio|Proprietà XMLA (vedere la sezione Osservazioni)|  
  
## <a name="remarks"></a>Remarks  
 Il `PropertyList` elemento contiene una raccolta di proprietà XMLA. ognuna delle quali consente all'utente di controllare alcuni aspetti del metodo `Discover` o `Execute`, ad esempio la definizione delle informazioni necessarie per connettersi all'origine dati, la specifica del formato del set di risultati o la specifica delle impostazioni locali con cui devono essere formattati i dati. Ogni proprietà XMLA nel `PropertyList` è definita da un elemento XML separato. Il valore della proprietà XMLA corrisponde ai dati contenuti nell'elemento XML, mentre il nome proprietà XMLA corrisponde al nome dell'elemento XML.  
  
 Le proprietà disponibili e i relativi valori possono essere ottenuti utilizzando il tipo di richiesta DISCOVER_PROPERTIES con il `Discover` metodo. Non è previsto un ordine obbligatorio per le proprietà elencate nell'elemento `PropertyList`.  
  
 Per ulteriori informazioni sulle proprietà XMLA supportate da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [proprietà XMLA supportate &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
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
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  