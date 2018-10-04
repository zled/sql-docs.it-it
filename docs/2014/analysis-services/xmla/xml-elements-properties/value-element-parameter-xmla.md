---
title: Valore elemento (Parameter) (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Value Element (Parameter)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: e590d189-91aa-40c7-8669-09c87812f4ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 875ea2b6f4c1dd1754fea1909b8a72daf55820d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133373"
---
# <a name="value-element-parameter-xmla"></a>Elemento Value (Parameter) (XMLA)
  Contiene il valore di un parametro rappresentato dal [parametro](parameter-element-xmla.md) elemento.  
  
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
|Elementi padre|[Parametro](parameter-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `Value` elemento può archiviare qualsiasi tipo XML semplice, come pure di XML for Analysis (XMLA) `Rowset` tipo di dati, per i parametri utilizzati dai comandi XMLA nel [Execute](../xml-elements-methods-execute.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
