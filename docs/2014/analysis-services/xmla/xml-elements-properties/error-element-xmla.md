---
title: Elemento Error (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b9b961a0d8d5a33cb0869b72e0250dee5456ca7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210151"
---
# <a name="error-element-xmla"></a>Elemento Error (XMLA)
  Contiene informazioni sull'errore restituita da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
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
|Elementi padre|[Message](message-element-xmla.md)|  
  
## <a name="child-elements"></a>Elementi figlio  
  
|Ancestor|Elementi figlio|  
|--------------|--------------------|  
|[Message](message-element-xmla.md)|None|  
|[Cella](cell-element-mddataset-xmla.md), [riga](description-element-xmla.md), [ErrorCode](errorcode-element-xmla.md), [HelpFile](file-element-xmla.md), [origine](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Obbligatorio `UnsignedInt` attributo (solo quando `Message` corrisponde all'elemento padre.) Contiene il codice restituito numerico dell'errore.|  
|Severity|Facoltativo `String` attributo (solo quando `Message` corrisponde all'elemento padre.) Contiene la gravità dell’errore.|  
|Description|Facoltativo `String` attributo (solo quando `Message` corrisponde all'elemento padre.) Contiene il testo descrittivo dell'errore.|  
|Origine|Facoltativo `String` attributo (solo quando `Message` corrisponde all'elemento padre.) Contiene il nome del componente che ha generato l’errore.|  
|FileGuida|Facoltativo `String` attributo (solo quando `Message` corrisponde all'elemento padre.) Contiene il percorso o URL al file Guida o all’argomento che descrive l'errore.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento warning &#40;XMLA&#41;](warning-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
