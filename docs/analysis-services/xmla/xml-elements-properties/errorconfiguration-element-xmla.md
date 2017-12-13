---
title: Elemento ErrorConfiguration (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ErrorConfiguration Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords: ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 473ca582b834dc2e9a0eca2ccbafaf5b7a0165ac
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="errorconfiguration-element-xmla"></a>Elemento ErrorConfiguration  (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Specifica le impostazioni per la gestione degli errori che possono verificarsi durante un [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) o [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Batch> <!-- or Process -->  
   ...  
   <ErrorConfiguration>  
      <KeyErrorLimit>...</KeyErrorLimit>  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
      <KeyErrorAction>...</KeyErrorAction>  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
      <KeyNotFound>...</KeyNotFound>  
      <KeyDuplicate>...</KeyDuplicate>  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
      <NullKeyNotAllowed>...<NullKeyNotAllowed>  
   </ErrorConfiguration>  
   ...  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md), [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|[KeyDuplicate](../../../analysis-services/scripting/properties/keyduplicate-element-assl.md), [KeyErrorAction](../../../analysis-services/scripting/properties/keyerroraction-element-assl.md), [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md), [KeyErrorLimitAction](../../../analysis-services/scripting/properties/keyerrorlimitaction-element-assl.md), [KeyErrorLogFile](../../../analysis-services/scripting/properties/keyerrorlogfile-element-assl.md), [ KeyNotFound](../../../analysis-services/scripting/properties/keynotfound-element-assl.md), [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md), [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 La struttura di questo elemento è identica alla struttura del **ErrorConfiguration** elemento in Analysis Services Scripting Language (ASSL). Per ulteriori informazioni sul **ErrorConfiguration** elemento, vedere [ErrorConfiguration elemento &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
