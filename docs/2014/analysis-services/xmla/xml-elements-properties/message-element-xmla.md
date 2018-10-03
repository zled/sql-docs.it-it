---
title: Elemento (XMLA) del messaggio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Message Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.message
- http://schemas.microsoft.com/analysisservices/2003/engine#Message
- urn:schemas-microsoft-com:xml-analysis#Message
helpviewer_keywords:
- Message element
ms.assetid: 028911e2-9779-43b1-824d-6d7fb2295885
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4aebaf918701d4ce10cfda9a4f3c030b53404e9f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054066"
---
# <a name="message-element-xmla"></a>Elemento Message (XMLA)
  Contiene un messaggio restituito da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da una [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Messages>  
   ...  
   <Message>  
      <Error>...</Error>  
      <!-- or -->  
      <Warning>...</Warning>  
   </Message>  
   ...  
</Messages>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Messaggi](messages-element-xmla.md)|  
|Elementi figlio|[Errore](error-element-xmla.md), [avviso](warning-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Questo elemento viene utilizzato nei casi in cui una chiamata al metodo `Discover` o un singolo comando XMLA all'interno di una chiamata al metodo `Execute` viene completato correttamente, ma con errori o avvisi. In tali casi, all'elemento radice, dopo tutti gli altri elementi, viene aggiunto un elemento `Messages`, che contiene a sua volta uno o più elementi `Message`. Ciascuna `Message` elemento rappresenta un singolo messaggio, un errore o avviso, restituito dalla [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
