---
title: Elemento Error (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 48413d3b21f2a1fce57e30956f5da4b2fe80d404
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="error-element-xmla"></a>Elemento Error (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Ancestor|Elementi figlio|  
|--------------|--------------------|  
|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|Nessuno|  
|[Cell](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [row](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Descrizione](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|ErrorCode|Richiesto **UnsignedInt** attributo (solo quando **messaggio** è l'elemento padre.) Contiene il codice restituito numerico dell'errore.|  
|Severity|Parametro facoltativo **stringa** attributo (solo quando **messaggio** è l'elemento padre.) Contiene la gravità dell’errore.|  
|Description|Parametro facoltativo **stringa** attributo (solo quando **messaggio** è l'elemento padre.) Contiene il testo descrittivo dell'errore.|  
|Origine|Parametro facoltativo **stringa** attributo (solo quando **messaggio** è l'elemento padre.) Contiene il nome del componente che ha generato l’errore.|  
|FileGuida|Parametro facoltativo **stringa** attributo (solo quando **messaggio** è l'elemento padre.) Contiene il percorso o URL al file Guida o all’argomento che descrive l'errore.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Warning & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
