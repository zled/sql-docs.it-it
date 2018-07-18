---
title: Elemento Parameters (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 68366f03168b7c7c434f05e88f512401248c1124
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050448"
---
# <a name="parameters-element-xmla"></a>Elemento Parameters (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [parametri](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) gli elementi utilizzati per il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (metodo).  
  
 **Namespace:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
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
|Elementi padre|[Eseguire](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Elementi figlio|[Parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Comandi alcune XML for Analysis (XMLA), ad esempio la [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comando, possono richiedere informazioni aggiuntive. Il **parametri** elemento fornisce un meccanismo per fornire informazioni aggiuntive, incluse le informazioni a blocchi, per un comando XMLA.  
  
 Se il comando XMLA non utilizza il **parametri** elemento, l'elemento può essere omesso quando si chiama il **Execute** (metodo).  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
