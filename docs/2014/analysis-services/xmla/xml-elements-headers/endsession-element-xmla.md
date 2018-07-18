---
title: Elemento EndSession (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- EndSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords:
- EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32c76318f05dbb628dd23de825203429ee0a22f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148122"
---
# <a name="endsession-element-xmla"></a>Elemento EndSession (XMLA)
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per terminare una sessione esistente in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
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
|Elementi padre|None|  
|Elementi figlio|None|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|SessionId|L'attributo `String` obbligatorio che identifica la sessione da terminare. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza un identificatore univoco globale (GUID) per identificare una sessione.|  
  
## <a name="remarks"></a>Note  
 L'elemento dell'intestazione `EndSession` è parte della richiesta SOAP inviata a una sessione esistente, avviata in modo esplicito su un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Se l'elemento dell'intestazione `EndSession` viene inviato, ma contiene un identificatore di sessione non più valido, viene restituito un errore SOAP che indica che la sessione non può essere trovata.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento BeginSession &#40;XMLA&#41;](session-element-xmla.md)   
 [Elemento Session &#40;XMLA&#41;](session-element-xmla.md)   
 [Gestione di connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
