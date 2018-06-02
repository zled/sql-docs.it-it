---
title: Elemento RestrictionList (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c802b20b0e2d6212f68fa4dc43c35426ff377957
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578143"
---
# <a name="restrictionlist-element-xmla"></a>Elemento RestrictionList (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di colonne e dati di restrizione utilizzati dal metodo [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
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
|Elementi padre|[Restrizioni](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Elementi figlio|Colonne e valori di restrizione (vedere la sezione Commenti).|  
  
## <a name="remarks"></a>Remarks  
 L'elemento **RestrictionList** contiene una raccolta di colonne di restrizione in base alla quale è possibile filtrare i dati restituiti dal metodo **Discover** . Ogni colonna di restrizione nell'elemento **RestrictionList** è definita da un elemento XML distinto. Il valore della colonna di restrizione corrisponde ai dati contenuti nell'elemento XML, mentre il nome della colonna di restrizione corrisponde al nome dell'elemento XML.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
