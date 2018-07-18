---
title: Elemento warning (XMLA) | Microsoft Docs
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
- Warning Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Warning
- microsoft.xml.analysis.warning
- http://schemas.microsoft.com/analysisservices/2003/engine#Warning
helpviewer_keywords:
- Warning element
ms.assetid: a34a6caa-4b68-486b-8f50-cdc124c65888
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ace514fd6a35fb376846c659ef64b9a40d1c116d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215751"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Message](message-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Obbligatorio `UnsignedInt` attributo. Contiene il codice numerico restituito dell'avviso.|  
|Severity|Facoltativo `String` attributo. Contiene la gravità dell'avviso.|  
|Description|Facoltativo `String` attributo. Contiene il testo descrittivo dell’avviso.|  
|Origine|Facoltativo `String` attributo. Contiene il nome del componente che genera l'avviso.|  
|FileGuida|Facoltativo `String` attributo. Contiene il percorso o URL al file Guida o all’argomento che descrive l'avviso.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Error &#40;XMLA&#41;](error-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
