---
title: Elemento BeginTransaction (XMLA) | Microsoft Docs
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
- BeginTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1685c1c61c248cf37672cab17ccf3144e7d5e7ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253043"
---
# <a name="begintransaction-element-xmla"></a>Elemento BeginTransaction (XMLA)
  Inizia una transazione nella sessione corrente con un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <BeginTransaction />  
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
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il comando `BeginTransaction` inizia una transazione attiva nella sessione corrente. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrementa il conteggio dei riferimenti delle transazioni per la sessione corrente. Diversamente, l'istanza inizierà una transazione nuova e imposterà il conteggio dei riferimenti per la sessione corrente a 1. Se una transazione attiva viene specificata utilizzando in modo esplicito il comando `BeginTransaction`, tutti i comandi successivi vengono eseguiti nella transazione specificata in modo esplicito.  
  
 Quando la sessione corrente è terminata e il conteggio dei riferimenti per le transazioni è maggiore di zero, viene eseguito il rollback di tutte le transazioni attive.  
  
 Se non ci sono transazioni attive specificate in modo esplicito nella sessione corrente, ogni comando eseguito nella sessione corrente viene eseguito in una transazione implicitamente definita. Il commit della transazione implicita viene eseguito se il comando riesce, o viene eseguito il rollback se il comando si interrompe.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Cancel &#40;XMLA&#41;](cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](committransaction-element-xmla.md)   
 [Elemento RollbackTransaction &#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
