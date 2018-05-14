---
title: Elemento CommitTransaction (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9afae9806592f09ebc32611d4566d7c67e65d743
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="committransaction-element-xmla"></a>Elemento CommitTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Esegue il commit di una transazione nella sessione corrente con un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <CommitTransaction />  
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
 Il **CommitTransaction** comando esegue il commit di una transazione attiva, definita in modo esplicito utilizzando il **BeginTransaction** elemento, nella sessione corrente. Se non è già presente alcuna transazione attiva, si verifica un errore. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] decrementa il conteggio dei riferimenti delle transazioni per la sessione corrente. Se il conteggio dei riferimenti delle transazioni attive definite in modo esplicito arriva a zero, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] esegue il commit della transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento BeginTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Elemento Cancel &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento RollbackTransaction &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
