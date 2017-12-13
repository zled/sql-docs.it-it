---
title: Annullamento di comandi (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
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
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5b6e43a5c79ccce179f960053ec7adde4e407509
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="canceling-commands-xmla"></a>Annullamento di comandi (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]A seconda delle autorizzazioni amministrative dell'utente che invia il comando, il [Annulla](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) comando nel codice XML per Analysis (XMLA) può annullare un comando in una sessione, una sessione, una connessione, un processo del server o una sessione associata o connessione.  
  
## <a name="canceling-commands"></a>Annullamento di comandi  
 Un utente può annullare il comando attualmente in esecuzione all'interno del contesto della sessione corrente esplicita inviando un **Annulla** comando senza proprietà specificate.  
  
> [!NOTE]  
>  Un comando in esecuzione in una sessione implicita non può essere annullato da un utente.  
  
### <a name="canceling-batch-commands"></a>Annullamento di comandi batch  
 Se un utente annulla una **Batch** comando, quindi tutti gli altri comandi non ancora eseguiti all'interno di **Batch** comando vengono annullate. Se il **Batch** comando è transazionale, tutti i comandi eseguiti prima di **Annulla** esecuzione del comando viene eseguito il rollback.  
  
## <a name="canceling-sessions"></a>Annullamento di sessioni  
 Specificando un identificatore di sessione per una sessione esplicita nel [SessionID](../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md) proprietà del **Annulla** comando, un amministratore del database o l'amministratore del server può annullare una sessione, tra cui il comando attualmente in esecuzione. Un amministratore di database può annullare solo sessioni per i database per i quali dispone delle autorizzazioni amministrative.  
  
 Un amministratore di database può recuperare le sessioni attive per un database specifico recuperando il set di righe dello schema DISCOVER_SESSIONS. Per recuperare il set di righe dello schema DISCOVER_SESSIONS, l'amministratore del database utilizza il codice XMLA **Discover** (metodo) e specifica l'identificatore del database appropriato per la restrizione session_current_database nella [Restrizioni](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md) proprietà del **Discover** metodo.  
  
## <a name="canceling-connections"></a>Annullamento di connessioni  
 Specificando un identificatore di connessione nel [ConnectionID](../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md) proprietà del **Annulla** comando, un amministratore del server può annullare tutte le sessioni associate a una determinata connessione, inclusi tutti esecuzione di comandi e annullare la connessione.  
  
> [!NOTE]  
>  Se l'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non è possibile individuare e annullare le sessioni associate a una connessione, ad esempio quando il data pump apre più sessioni fornendo connettività HTTP, l'istanza non è possibile annullare la connessione. Se questa situazione si verifica durante l'esecuzione di un **Annulla** comando, si verifica un errore.  
  
 Un amministratore del server può recuperare le connessioni attive per un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza recuperando il set di righe dello schema DISCOVER_CONNECTIONS tramite XMLA **Discover** metodo.  
  
## <a name="canceling-server-processes"></a>Annullamento di processi del server  
 Specificando un identificatore di processo server (SPID) nei [SPID](../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md) proprietà del **Annulla** comando, un amministratore del server può annullare i comandi associati a un valore SPID specificato.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Annullamento di sessioni e connessioni associate  
 È possibile impostare il [CancelAssociated](../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md) proprietà su true per annullare le connessioni, sessioni e comandi associati alla connessione, una sessione o un valore SPID specificato nel **Annulla** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Individuare metodo &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
