---
title: Elemento RestrictionList (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: RestrictionList Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords: RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af4df63d245aacd861c9f4a2a1d8a4c9d8a9b01d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="restrictionlist-element-xmla"></a>Elemento RestrictionList (XMLA)
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Restrizioni](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Elementi figlio|Colonne e valori di restrizione (vedere la sezione Commenti).|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento **RestrictionList** contiene una raccolta di colonne di restrizione in base alla quale è possibile filtrare i dati restituiti dal metodo **Discover** . Ogni colonna di restrizione nell'elemento **RestrictionList** è definita da un elemento XML distinto. Il valore della colonna di restrizione corrisponde ai dati contenuti nell'elemento XML, mentre il nome della colonna di restrizione corrisponde al nome dell'elemento XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
