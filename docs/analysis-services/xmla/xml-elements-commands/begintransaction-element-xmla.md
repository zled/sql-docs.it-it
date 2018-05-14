---
title: Elemento BeginTransaction (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d8f88c11759ae746bbe6bb586fdb467d96b70f1e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="begintransaction-element-xmla"></a>Elemento BeginTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Inizia una transazione nella sessione corrente con un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <BeginTransaction />  
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
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **BeginTransaction** comando avvia una transazione attiva nella sessione corrente. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrementa il conteggio dei riferimenti delle transazioni per la sessione corrente. Diversamente, l'istanza inizierà una transazione nuova e imposterà il conteggio dei riferimenti per la sessione corrente a 1. Se una transazione attiva viene specificata in modo esplicito utilizzando il **BeginTransaction** comando, tutti i comandi successivi vengono eseguiti all'interno della transazione specificata in modo esplicito.  
  
 Quando la sessione corrente è terminata e il conteggio dei riferimenti per le transazioni è maggiore di zero, viene eseguito il rollback di tutte le transazioni attive.  
  
 Se non ci sono transazioni attive specificate in modo esplicito nella sessione corrente, ogni comando eseguito nella sessione corrente viene eseguito in una transazione implicitamente definita. Il commit della transazione implicita viene eseguito se il comando riesce, o viene eseguito il rollback se il comando si interrompe.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Cancel &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Elemento RollbackTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
