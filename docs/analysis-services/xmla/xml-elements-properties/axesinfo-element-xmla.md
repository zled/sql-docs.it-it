---
title: Elemento AxesInfo (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c766cc155b0e0b04af65c34653fbd5a5dcef4e64
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575823"
---
# <a name="axesinfo-element-xmla"></a>Elemento AxesInfo (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md) elementi, che rappresenta i metadati dell'asse contenuti dall'elemento padre [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<OlapInfo>  
   ...  
   <AxesInfo>  
      <AxisInfo>...</AxisInfo>  
   </AxesInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementi figlio|[AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Il **AxesInfo** elemento contiene una **AxisInfo** elemento per ogni asse all'interno del dataset multidimensionale restituito da un **radice** elemento utilizzando il  **MDDataSet** tipo di dati.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
