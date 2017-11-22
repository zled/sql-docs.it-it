---
title: Il tipo di dati ResultSet (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Resultset Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords: Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 70010fe50f92d74b653080654e0e5da3c8e79875
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="resultset-data-type-xmla"></a>Tipo di dati Resultset (XMLA)
  Definisce un tipo di dati primitivo astratto che rappresenta i dati restituiti da una [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
 **Namespace** urn: schemas-microsoft-com: XML-analysis: resultset  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|Nessuno|  
|Tipi di dati derivati|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md), [olapxmla_EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md), [set di righe](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Eccezione](../../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md), [messaggi](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Resultset** tipo di dati è un set di risultati XML autodescrittivo che può includere schema e dati, a seconda del tipo di informazioni da restituire.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
