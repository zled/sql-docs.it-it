---
title: Valore elemento (Parameter) (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbd4dd56bedf53d4f0bc7374e9389221acb092d7
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34576753"
---
# <a name="value-element-parameter-xmla"></a>Elemento Value (Parameter) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il valore di un parametro rappresentato dal [parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Parameter>  
   ...  
   <Value>...</Value>  
   ...  
</Parameter>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il **valore** elemento possibile memorizzare qualsiasi tipo XML semplice, nonché il codice XML for Analysis (XMLA) **set di righe** il tipo di dati, per i parametri utilizzati dai comandi XMLA nel [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
