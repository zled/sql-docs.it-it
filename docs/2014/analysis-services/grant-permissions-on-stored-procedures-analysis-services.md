---
title: Concedere le autorizzazioni per stored procedure (Analysis Services) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01793166-a3e5-4856-8302-21b82d494e69
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c82a2df266f9e6dce2767ecceb3e2af9bd12fc1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170489"
---
# <a name="grant-permissions-on-stored-procedures-analysis-services"></a>Concedere le autorizzazioni per le stored procedure (Analysis Services)
  Stored procedure o gli assembly, in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sono routine esterne, scritte in un [!INCLUDE[msCoName](../includes/msconame-md.md)] linguaggio di programmazione .NET, che estendono le funzionalità di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Gli assembly permettono allo sviluppatore di sfruttare tutte le potenzialità di integrazione tra più linguaggi, gestione delle eccezioni e supporto per il controllo delle versioni, per la distribuzione e per il debug.  
  
 Per registrare un assembly, è necessario essere un amministratore del server. Vedere [concedere le autorizzazioni di amministratore del Server &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md).  
  
## <a name="security-context-for-stored-procedure-execution"></a>Contesto di sicurezza per l'esecuzione di stored procedure  
 Una stored procedure può essere chiamata da qualsiasi utente. In base al modo in cui è stata configurata, una stored procedure può essere eseguita nel contesto dell'utente che chiama la procedura o nel contesto di un utente anonimo. Poiché un utente anonimo non dispone di un contesto di sicurezza, utilizzare questa funzionalità quando si configura l'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in modo da concedere l'accesso anonimo.  
  
 Dopo che l'utente chiama una stored procedure ma prima che [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] esegui la stored procedure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] valuta le azioni all'interno della stored procedure. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] valuta le azioni in una stored procedure in base all'intersezione delle autorizzazioni concesse all'utente e al set di autorizzazioni utilizzato per eseguire la routine. Se la stored procedure contiene un'azione che non può essere eseguita dal ruolo del database a cui appartiene l'utente, l'azione non viene eseguita.  
  
 Di seguito sono indicati i set di autorizzazioni utilizzati per eseguire le stored procedure:  
  
-   **-Safe** set di autorizzazioni con il sicure, una stored procedure non è possibile accedere alle risorse protette nel [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework. Questo set di autorizzazioni consente esclusivamente i calcoli. Si tratta del set di autorizzazioni che offre la protezione maggiore. Le informazioni non vengono propagate al di fuori di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le autorizzazioni non possono essere innalzate e il rischio di attacchi di manomissione dei dati è ridotto al minimo.  
  
-   **L'accesso esterno** set di autorizzazioni con External Access, una stored procedure può accedere alle risorse esterne utilizzando codice gestito. L'impostazione di questo set di autorizzazioni per una stored procedure non causa errori di programmazione che potrebbero portare all'instabilità del server. Questo set di autorizzazioni, tuttavia, potrebbe consentire la propagazione delle informazioni al di fuori del server e potrebbe offrire la possibilità di innalzamento delle autorizzazioni e di attacchi di manomissione dei dati.  
  
-   **Senza restrizioni** set di autorizzazioni con il senza restrizioni, una stored procedure può accedere alle risorse esterne utilizzando codice. Con questo set di autorizzazioni non vi sono garanzie di sicurezza o di affidabilità per le stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modello multidimensionale](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  