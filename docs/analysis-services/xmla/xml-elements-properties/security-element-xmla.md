---
title: Elemento Security (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c4ea0e1f9bfab567c792bdd7b233bea038e87f54
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968743"
---
# <a name="security-element-xmla"></a>Elemento Security (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Specifica come eseguire il backup o ripristino delle definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante una [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*SkipMembership*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Copia di backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **sicurezza** elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un database di Analysis Services vengono sottoposti a backup o ripristinato durante, rispettivamente, un **Backup** o **Ripristinare** comando. Questo elemento determina inoltre se gli account utente di Windows e i gruppi definiti come membri delle definizioni di sicurezza sono inclusi come parte del **Backup** oppure **ripristinare** comando.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza, durante **Backup** oppure **ripristinare** comandi.|  
|*CopyAll*|Include le definizioni di sicurezza e informazioni sull'appartenenza durante **Backup** oppure **ripristinare** comandi.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante **Backup** oppure **ripristinare** comandi.|  
  
## <a name="see-also"></a>Vedere anche
 [Elemento SynchronizeSecurity &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
