---
title: Elemento Security (XMLA) | Microsoft Docs
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
- Security Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 138b93043cbfeba51472dfa61816cf9023a3f2c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155022"
---
# <a name="security-element-xmla"></a>Elemento Security (XMLA)
  Specifica come eseguire il backup o ripristino delle definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante una [Backup](../xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
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
|Elementi padre|[Copia di backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `Security` elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database sono sottoposti a backup o ripristino durante, rispettivamente, una `Backup` o `Restore` comando. Questo elemento determina inoltre se gli account utente e i gruppi di utenti di Windows definiti come membri delle definizioni di sicurezza sono inclusi come parte del comando `Backup` o `Restore`.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza durante un comando `Backup` o `Restore`.|  
|*CopyAll*|Include le definizioni di sicurezza e le informazioni sull'appartenenza durante un comando `Backup` o `Restore`.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante un comando `Backup` o `Restore`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento SynchronizeSecurity &#40;XMLA&#41;](security-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
