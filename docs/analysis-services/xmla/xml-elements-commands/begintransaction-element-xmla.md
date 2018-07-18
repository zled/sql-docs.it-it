---
title: Elemento BeginTransaction (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb4a4dea3658ad03fd6205f9076bd1cb65ca9ba7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038379"
---
# <a name="begintransaction-element-xmla"></a>Elemento BeginTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Inizia una transazione nella sessione corrente con un'istanza di Analysis Services.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **BeginTransaction** comando avvia una transazione attiva nella sessione corrente. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrementa il conteggio dei riferimenti delle transazioni per la sessione corrente. Diversamente, l'istanza inizierà una transazione nuova e imposterà il conteggio dei riferimenti per la sessione corrente a 1. Se una transazione attiva viene specificata in modo esplicito utilizzando il **BeginTransaction** comando, tutti i comandi successivi vengono eseguiti all'interno della transazione specificata in modo esplicito.  
  
 Quando la sessione corrente è terminata e il conteggio dei riferimenti per le transazioni è maggiore di zero, viene eseguito il rollback di tutte le transazioni attive.  
  
 Se non ci sono transazioni attive specificate in modo esplicito nella sessione corrente, ogni comando eseguito nella sessione corrente viene eseguito in una transazione implicitamente definita. Il commit della transazione implicita viene eseguito se il comando riesce, o viene eseguito il rollback se il comando si interrompe.  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Cancel &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Elemento RollbackTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
