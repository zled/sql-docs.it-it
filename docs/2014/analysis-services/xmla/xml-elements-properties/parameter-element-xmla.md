---
title: Elemento Parameter (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Parameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parameter
- microsoft.xml.analysis.parameter
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameter
helpviewer_keywords:
- Parameter element
ms.assetid: fe31ac3d-a3e8-4f60-a81a-c43271ddbed4
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 6e39068ff0fc5c1e0bf866029ad2e4413768c1c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157590"
---
# <a name="parameter-element-xmla"></a>Elemento Parameter (XMLA)
  Contiene il nome e il valore di un parametro utilizzato per il [Execute](../xml-elements-methods-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
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
|Elementi padre|[Parametri](parameters-element-xmla.md)|  
|Elementi figlio|[Nome](name-element-parameter-xmla.md), [valore](value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Comandi di alcuni XML for Analysis (XMLA), ad esempio il [processo](../xml-elements-commands/process-element-xmla.md) command, possono richiedere informazioni aggiuntive. L'elemento `Parameter` fornisce un meccanismo per fornire informazioni aggiuntive, incluse le informazioni a blocchi, per un comando XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  