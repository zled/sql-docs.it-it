---
title: Elemento Subscribe (XMLA) | Microsoft Docs
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
- Subscribe Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97b473820ee809f5a606e8bb9f30be6e315a2801
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247261"
---
# <a name="subscribe-element-xmla"></a>Elemento Subscribe (XMLA)
  Sottoscrive una traccia e restituisce un set di righe che contiene gli eventi di traccia da un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
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
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `Subscribe` comando sottoscrive e trasmette di nuovo un set di righe da una traccia specificata su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Se un oggetto diverso da una traccia viene specificato nella `Object` si verifica un errore di elemento.  
  
 Se l'elemento `Object` non viene specificato, una traccia della sessione viene definita e sottoscritta sull'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La traccia della sessione restituisce un set fisso di eventi traccia dalla sessione corrente.  
  
 Il flusso di set di righe restituito da questo comando viene concluso se l'applicazione client chiude la connessione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza, o se la sessione sulla quale il `Subscribe` comando viene eseguito viene terminata.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
