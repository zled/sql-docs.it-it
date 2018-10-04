---
title: Annullamento di comandi (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3b622700843e83f3308874d44a4c6af132b4d89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171945"
---
# <a name="canceling-commands-xmla"></a>Annullamento di comandi (XMLA)
  A seconda delle autorizzazioni amministrative dell'utente che invia il comando, il [annullare](../xmla/xml-elements-commands/cancel-element-xmla.md) comando nel codice XML per Analysis (XMLA) può annullare un comando in una sessione, una sessione, una connessione, un processo del server o una sessione associata o connessione.  
  
## <a name="canceling-commands"></a>Annullamento di comandi  
 Un utente può annullare il comando attualmente in esecuzione nel contesto della sessione corrente esplicita inviando un comando `Cancel` senza proprietà specificate.  
  
> [!NOTE]  
>  Un comando in esecuzione in una sessione implicita non può essere annullato da un utente.  
  
### <a name="canceling-batch-commands"></a>Annullamento di comandi batch  
 Se un utente annulla un comando `Batch`, tutti i comandi rimanenti non ancora eseguiti nel comando `Batch` vengono annullati. Se il comando `Batch` è transazionale, di tutti i comandi eseguiti prima del comando `Cancel` viene eseguito il rollback.  
  
## <a name="canceling-sessions"></a>Annullamento di sessioni  
 Specificando un identificatore di sessione per una sessione esplicita nella [SessionID](../xmla/xml-elements-properties/id-element-xmla.md) proprietà del `Cancel` comando, un amministratore del database o amministratore del server può annullare una sessione, inclusi il comando attualmente in esecuzione . Un amministratore di database può annullare solo sessioni per i database per i quali dispone delle autorizzazioni amministrative.  
  
 Un amministratore di database può recuperare le sessioni attive per un database specifico recuperando il set di righe dello schema DISCOVER_SESSIONS. Per recuperare il set di righe dello schema DISCOVER_SESSIONS, l'amministratore del database utilizza XMLA `Discover` metodo e specifica l'identificatore del database appropriato per la colonna di restrizione SESSION_CURRENT_DATABASE nella [restrizioni](../xmla/xml-elements-properties/restrictions-element-xmla.md) proprietà del `Discover` (metodo).  
  
## <a name="canceling-connections"></a>Annullamento di connessioni  
 Specificando un identificatore di connessione nel [ConnectionID](../xmla/xml-elements-properties/connectionid-element-xmla.md) proprietà del `Cancel` comando, un amministratore del server può annullare tutte le sessioni associate a una determinata connessione, inclusi tutti i comandi in esecuzione, e Annulla la connessione.  
  
> [!NOTE]  
>  Se l'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non è possibile individuare e annullare le sessioni associate a una connessione, ad esempio quando il data pump apre più sessioni fornendo contemporaneamente connettività HTTP, l'istanza non è possibile annullare la connessione. Se questa situazione si verifica durante l'esecuzione di un comando `Cancel`, si verifica un errore.  
  
 Un amministratore del server può recuperare le connessioni attive per un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] recuperando il set di righe dello schema DISCOVER_CONNECTIONS tramite il metodo `Discover` XMLA.  
  
## <a name="canceling-server-processes"></a>Annullamento di processi del server  
 Specificando un identificatore di processo server (SPID) nei [SPID](../xmla/xml-elements-properties/spid-element-xmla.md) proprietà del `Cancel` comando, un amministratore del server può annullare i comandi associati a un valore SPID specificato.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Annullamento di sessioni e connessioni associate  
 È possibile impostare il [CancelAssociated](../xmla/xml-elements-properties/cancelassociated-element-xmla.md) su true per annullare le connessioni, sessioni e comandi associati con la connessione, sessione o SPID specificato nella proprietà di `Cancel` comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Discover &#40;XMLA&#41;](../xmla/xml-elements-methods-discover.md)   
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
