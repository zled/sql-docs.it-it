---
title: Elemento Cancel (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cancel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords:
- Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b106806118649d35e7be239b4ceea7201f349d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055211"
---
# <a name="cancel-element-xmla"></a>Elemento Cancel (XMLA)
  Annulla un comando attualmente in esecuzione un' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Cancel>  
      <ConnectionID>...</ConnectionID>  
      <SessionID>...</SessionID>  
      <SPID>...</SPID>  
      <CancelAssociated>...</CancelAssociated>  
   </Cancel>  
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
|Elementi figlio|[CancelAssociated](../xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../xml-elements-properties/id-element-xmla.md), [SessionID](../xml-elements-properties/sessionid-element-xmla.md), [SPID](../xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `Cancel` annulla comandi attualmente in esecuzione all'interno del contesto di una sessione. Se l'applicazione client non ha richiesto una sessione, un comando non può essere annullato.  
  
 Se il comando `Cancel` viene eseguito durante l'esecuzione di un comando `Batch`, l'intero comando `Batch` viene annullato. Se il comando `Batch` è transazionale, per tutti i comandi contenuti dal comando `Batch` viene eseguito il. Se il comando `Batch` non è transazionale, il rollback viene eseguito solo per i comandi contenuti dal comando `Batch` in esecuzione nel momento in cui il comando `Cancel` viene eseguito. Il rollback non viene eseguito per i comandi in un comando `Batch` non transazionale che era già stato eseguito.  
  
 In genere, il comando `Cancel` viene utilizzato per annullare l'esecuzione di comandi nella sessione attualmente attiva. In quel caso, nessuno degli elementi figlio per il comando `Cancel` deve essere specificato. Il comando `Cancel` può essere utilizzato anche dagli amministratori per annullare comandi eseguiti in connessioni o sessioni diverse dalla sessione attualmente attiva. Membri di un ruolo che ha autorizzazioni di amministratore per un database specificato possono annullare comandi per connessioni e sessioni applicabili a quel database, mentre gli amministratori del server possono annullare comandi per connessioni e sessioni per un'istanza di Analysis Services specificata.  
  
 Per recuperare informazioni su connessioni e sessioni correnti per un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] può essere eseguito il metodo `Discover` per richiedere, rispettivamente, i set di righe dello schema di DISCOVER_CONNECTIONS e di DISCOVER_SESSIONS. Membri di un ruolo che ha autorizzazioni di amministratore per un database specificato possono restituire sessioni solo per un database specificato, riportando tale database nella colonna restrizione SESSION_CURRENT_DATABASE per il set di righe dello schema di DISCOVER_SESSIONS. Per altre informazioni sul `Discover` metodo, vedere [metodo Discover &#40;XMLA&#41;](../xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento batch &#40;XMLA&#41;](batch-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
