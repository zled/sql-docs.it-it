---
title: Elemento radice (XMLA) | Documenti Microsoft
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
- Root Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#root
- urn:schemas-microsoft-com:xml-analysis#root
- microsoft.xml.analysis.root
helpviewer_keywords:
- root element
ms.assetid: ecd9d6e8-b16c-4d62-9a87-107c413a0056
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 972757d71db61ed5cbe82d9bf5e91b448c69260c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="root-element-xmla"></a>Elemento radice (XMLA)
  Contiene un risultato restituito dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo o un comando XML for Analysis (XMLA) eseguito utilizzando il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<return> <!-- or results-->  
   ...  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">...</root> <!-- for Execute method only -->  
   <!-- or -->  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">...</root>  
   <!-- or -->  
   <root xmlns= xmlns="urn:schemas-microsoft-com:xml-analysis:empty">...</root>  
   ...  
</return>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Vedere la tabella riportata di seguito.|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
|Ancestor|Tipo di dati|  
|--------------|---------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[Set di righe](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [set di righe](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[risultati](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md), [restituire](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **radice** elemento contiene le informazioni restituite in uno di [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) elemento restituito da una sola **Discover** chiamata al metodo, o nel [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) elemento restituito da un singolo comando XMLA eseguito da una sola **Execute** chiamata al metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
