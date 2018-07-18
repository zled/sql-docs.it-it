---
title: Tipo di dati ResultSet (XMLA) | Microsoft Docs
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
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d4e95d3e2b85971271cff4b1365b44e5a30ba0c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155072"
---
# <a name="resultset-data-type-xmla"></a>Tipo di dati Resultset (XMLA)
  Definisce un tipo di dati primitivo astratto che rappresenta i dati restituiti da una [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) chiamata al metodo.  
  
 **Namespace** urn: schemas-microsoft-com: XML-analysis: resultset  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[MDDataSet](mddataset-data-type-xmla.md), [olapxmla_EmptyResult](emptyresult-data-type-xmla.md), [set di righe](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Eccezione](../xml-elements-properties/exception-element-xmla.md), [messaggi](../xml-elements-properties/messages-element-xmla.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Il tipo di dati `Resultset` è un set di risultati XML autodescrittivo che può includere schema e dati, a seconda del tipo di informazioni da restituire.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
