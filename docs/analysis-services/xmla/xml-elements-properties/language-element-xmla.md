---
title: Elemento di linguaggio (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Language Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Language
- microsoft.xml.analysis.language
- http://schemas.microsoft.com/analysisservices/2003/engine#Language
helpviewer_keywords:
- Language element
ms.assetid: cd998202-e43f-4c6c-8727-a15a76a520ea
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2410bfc2c98947f2ebe7144483e2f53bbb28d527
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="language-element-xmla"></a>Elemento Language (XMLA)
  Contiene l'identificatore delle impostazioni locali (LCID) per l'elemento padre [traduzione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Conversione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Language** elemento specifica l'identificatore LCID utilizzato dall'elemento padre **traduzione** elemento per assegnare il **nome** dell'elemento padre **traduzione** elemento da un membro dell'attributo, per la lingua specificata, durante un **inserire** o **aggiornamento** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserisci elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Nome elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)   
 [Elemento Update &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  