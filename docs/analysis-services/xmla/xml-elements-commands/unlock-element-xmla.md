---
title: Elemento Unlock (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfilee"
ms.openlocfilehash: eb9cced037ab7fcf7072e6db56cb645333a02311
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="unlock-element-xmla"></a>Elemento Unlock (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sblocca un blocco specificato in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Unlock>  
      <ID>...</ID>  
   </Unlock>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il comando **Unlock** rimuove un blocco applicato all'interno del contesto della transazione attualmente attiva. Solo gli amministratori del database o gli amministratori del server possono eseguire in modo esplicito un comando **Unlock** .  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Bloccare l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
