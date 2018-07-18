---
title: Elemento warning (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 73662315d294cade8b344f8967923fe15e94f886
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576733"
---
# <a name="warning-element-xmla"></a>Elemento Warning (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni su un avviso restituito da un'istanza di Analysis Services.  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Attributo **UnsignedInt** obbligatorio. Contiene il codice numerico restituito dell'avviso.|  
|Gravità|Attributo **String** facoltativo. Contiene la gravità dell'avviso.|  
|Description|Attributo **String** facoltativo. Contiene il testo descrittivo dell’avviso.|  
|Origine|Attributo **String** facoltativo. Contiene il nome del componente che genera l'avviso.|  
|FileGuida|Attributo **String** facoltativo. Contiene il percorso o URL al file Guida o all’argomento che descrive l'avviso.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Error &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
