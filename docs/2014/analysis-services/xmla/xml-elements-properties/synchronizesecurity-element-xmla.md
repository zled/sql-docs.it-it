---
title: Elemento SynchronizeSecurity (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SynchronizeSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e43831854720e8a2525edae06165334443dad3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224543"
---
# <a name="synchronizesecurity-element-xmla"></a>Elemento SynchronizeSecurity (XMLA)
  Specifica come sincronizzare definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante una [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*SkipMembership*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Sincronizza](../xml-elements-commands/synchronize-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `Security` elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database sono sincronizzati durante un `Synchronize` comando. Questo elemento determina anche se gli account utente di Windows e i gruppi definiti come membri delle definizioni di sicurezza sono inclusi come parte del comando `Synchronize`.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza durante un comando `Synchronize`.|  
|*CopyAll*|Include le definizioni di sicurezza e le informazioni sull'appartenenza durante un comando `Synchronize`.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante un comando `Synchronize`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di sicurezza &#40;XMLA&#41;](security-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
