---
title: Elemento AxisInfo (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 858cb8be01a16d9ccb7d6455043d370865f1c3e6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="axisinfo-element-xmla"></a>Elemento AxisInfo (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Rappresenta i metadati di un singolo asse contenuto nell'elemento padre [AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AxesInfo>  
   ...  
   <AxisInfo name="string">  
      <HierarchyInfo>...</HierarchyInfo>  
   </AxisInfo>  
   ...  
</AxesInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md)|  
|Elementi figlio|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|Nome|Richiesto **stringa** attributo. Nome dell'asse.|  
  
## <a name="remarks"></a>Osservazioni  
 In un **radice** elemento che utilizza il **MDDataSet** oggetto, un **AxisInfo** elemento contiene una raccolta di **HierarchyInfo** gli elementi che , combinato con il valore di **nome** attributo, rappresenta la definizione di un singolo asse restituita nel dataset multidimensionale.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
