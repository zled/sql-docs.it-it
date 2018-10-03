---
title: Elemento PropertyList (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3eb6da43b5487efa93f3901c866a1183e77d978
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068911"
---
# <a name="propertylist-element-xmla"></a>Elemento PropertyList (XMLA)
  Contiene una raccolta di XML delle proprietà Analysis (XMLA) usate per la [Discover](../xml-elements-methods-discover.md) e [Execute](../xml-elements-methods-execute.md) metodi.  
  
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
  
## <a name="remarks"></a>Note  
 Il `PropertyList` elemento contiene una raccolta di proprietà XMLA. ognuna delle quali consente all'utente di controllare alcuni aspetti del metodo `Discover` o `Execute`, ad esempio la definizione delle informazioni necessarie per connettersi all'origine dati, la specifica del formato del set di risultati o la specifica delle impostazioni locali con cui devono essere formattati i dati. Ogni proprietà XMLA nel `PropertyList` elemento è definito da un elemento XML distinto. Il valore della proprietà XMLA corrisponde ai dati contenuti nell'elemento XML, mentre il nome proprietà XMLA corrisponde al nome dell'elemento XML.  
  
 Le proprietà disponibili e i relativi valori possono essere ottenuti utilizzando il tipo di richiesta DISCOVER_PROPERTIES con il `Discover` (metodo). Non è previsto un ordine obbligatorio per le proprietà elencate nell'elemento `PropertyList`.  
  
 Per altre informazioni sulle proprietà XMLA supportate da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [proprietà XMLA supportate &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
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
  
  
