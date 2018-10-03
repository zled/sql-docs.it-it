---
title: Elemento RollbackTransaction (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RollbackTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords:
- RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ae78f589c1c85713c751a737d6fb93fac9efeda
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218813"
---
# <a name="rollbacktransaction-element-xmla"></a>Elemento RollbackTransaction (XMLA)
  Il rollback di una transazione nella sessione corrente con un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
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
 Il comando `RollbackTransaction` esegue il rollback di tutte le transazioni attive, definite in modo esplicito utilizzando l'elemento `BeginTransaction`, nella sessione corrente. Se non è già presente alcuna transazione attiva, si verifica un errore. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] decrementa a zero il conteggio dei riferimenti delle transazioni per la sessione corrente, eseguendo il rollback di tutte le transazioni attive.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento BeginTransaction &#40;XMLA&#41;](begintransaction-element-xmla.md)   
 [Elemento Cancel &#40;XMLA&#41;](cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40;XMLA&#41;](committransaction-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
