---
title: Elemento Security (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14cbfaf2e50a2eb77b3918317113823a342857cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="security-element-xmla"></a>Elemento Security (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Specifica la modalità di backup o il ripristino delle definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante un [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*SkipMembership*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **sicurezza** elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database vengono sottoposti a backup o ripristinato durante, rispettivamente, un **Backup** o **ripristinare** comando. Questo elemento determina inoltre se gli account utente di Windows e i gruppi definiti come membri delle definizioni di sicurezza sono inclusi come parte di **Backup** o **ripristinare** comando.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza durante **Backup** o **ripristinare** comandi.|  
|*CopyAll*|Include le definizioni di sicurezza e informazioni sull'appartenenza durante **Backup** o **ripristinare** comandi.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante **Backup** o **ripristinare** comandi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento SynchronizeSecurity &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
