---
title: Elemento warning (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
apiname: Warning Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Warning
- microsoft.xml.analysis.warning
- http://schemas.microsoft.com/analysisservices/2003/engine#Warning
helpviewer_keywords: Warning element
ms.assetid: a34a6caa-4b68-486b-8f50-cdc124c65888
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46c133bf25acd198fee38e3a0e26a612c3d0625d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="warning-element-xmla"></a>Elemento Warning (XMLA)
  Contiene informazioni su un avviso restituito da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Message>  
   <Warning   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
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
|Elementi padre|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|ErrorCode|Attributo **UnsignedInt** obbligatorio. Contiene il codice numerico restituito dell'avviso.|  
|Gravità|Attributo **String** facoltativo. Contiene la gravità dell'avviso.|  
|Descrizione|Attributo **String** facoltativo. Contiene il testo descrittivo dell’avviso.|  
|Origine|Attributo **String** facoltativo. Contiene il nome del componente che genera l'avviso.|  
|FileGuida|Attributo **String** facoltativo. Contiene il percorso o URL al file Guida o all’argomento che descrive l'avviso.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Errore elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
