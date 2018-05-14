---
title: Elemento radice (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4fc4072c7b19cff327463dd8df8af7d136e6c1e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="root-element-xmla"></a>Elemento radice (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
