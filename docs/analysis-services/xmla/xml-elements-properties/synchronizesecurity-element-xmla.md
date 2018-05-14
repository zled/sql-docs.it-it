---
title: Elemento SynchronizeSecurity (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a30e7c484f318fb64daa138591ad9ef4045bbf47
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="synchronizesecurity-element-xmla"></a>Elemento SynchronizeSecurity (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Specifica come sincronizzare definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante un [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
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
|Elementi padre|[Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **sicurezza** elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database sono sincronizzati durante un **Sincronizza**  comando. Questo elemento determina inoltre se gli account utente di Windows e i gruppi definiti come membri delle definizioni di sicurezza sono inclusi come parte di **Sincronizza** comando.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza durante un **Sincronizza** comando.|  
|*CopyAll*|Include le definizioni di sicurezza e informazioni sull'appartenenza durante un **Sincronizza** comando.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante un **Sincronizza** comando.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di sicurezza &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
