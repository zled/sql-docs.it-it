---
title: Tipo di dati ResultSet (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a34b99aa63608faafa42d94aaf8938f86bb3894c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205491"
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
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|[MDDataSet](mddataset-data-type-xmla.md), [olapxmla_EmptyResult](emptyresult-data-type-xmla.md), [set di righe](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Eccezione](../xml-elements-properties/exception-element-xmla.md), [messaggi](../xml-elements-properties/messages-element-xmla.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Note  
 Il tipo di dati `Resultset` è un set di risultati XML autodescrittivo che può includere schema e dati, a seconda del tipo di informazioni da restituire.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
