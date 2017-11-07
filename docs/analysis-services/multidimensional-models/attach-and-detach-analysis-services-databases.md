---
title: Collegamento e scollegamento di database di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.ssmsimbi.AttachDatabase.f1
- sql13.asvs.ssms.attachdatabase.f1
- sql13.asvs.ssmsimbi.DetachDatabase.f1
- sql13.asvs.ssms.detachdatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f4c193def48b92245c1e2f2955262d3fb0850957
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="attach-and-detach-analysis-services-databases"></a>Collegamento e scollegamento di database di Analysis Services
  Spesso, un amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vuole portare un database offline per un determinato periodo e quindi riportarlo online nella stessa istanza del server o in una diversa. Queste situazioni spesso sono determinate da esigenze aziendali, ad esempio lo spostamento del database in un disco diverso per migliorare le prestazioni, la necessità di ottenere più spazio per la crescita del database oppure per aggiornare un prodotto. In questi e in molti altri casi, i comandi **Attach** e **Detach** consentono agli amministratori di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di portare il database offline e di riportarlo online con pochi passaggi.  
  
## <a name="attach-and-detach-commands"></a>Comandi Attach e Detach  
 Il comando **Attach** consente di portare online un database in precedenza portato offline. È possibile collegare il database all'istanza del server originale o a un'altra istanza. Quando si collega un database, l'utente può specificare l'impostazione **ReadWriteMode** per il database. Il comando **Detach** consente di portare un database offline dal server.  
  
## <a name="attach-and-detach-usage"></a>Utilizzo di Attach e Detach  
 Il comando **Attach** consente di portare online una struttura del database esistente. Se il database è collegato in modalità **ReadWrite** , può essere collegato solo una volta a un'istanza del server. Se invece è collegato in modalità **ReadOnly** , può essere collegato più volte a diverse istanze del server. Tuttavia, non è possibile collegare lo stesso database più di una volta alla stessa istanza del server. Se si tenta di collegare lo stesso database più di una volta, verrà generato un errore, anche se i dati sono stati copiati in cartelle distinte.  
  
> [!IMPORTANT]  
>  Se per lo scollegamento del database è stata richiesta una password, è necessario utilizzare la stessa password per collegare il database.  
  
 Il comando **Detach** consente di portare offline una struttura del database esistente. Quando un database viene scollegato, è consigliabile fornire una password per proteggere i metadati riservati.  
  
> [!IMPORTANT]  
>  Per proteggere il contenuto dei file di dati, utilizzare un elenco di controllo di accesso per la cartella, le sottocartelle e i file di dati.  
  
 Quando si scollega un database, nel server vengono effettuati i passaggi seguenti.  
  
|Scollegamento di un database di lettura/scrittura|Scollegamento di un database di sola lettura|  
|--------------------------------------|-------------------------------------|  
|1) Il server invia una richiesta per un blocco CommitExclusive sul database<br /><br /> 2) Il server attende il commit o il rollback di tutte le transazioni in corso<br /><br /> 3) Il server compila tutti i metadati necessari per scollegare il database<br /><br /> 4) Il database viene contrassegnato come eliminato<br /><br /> 5) Il server esegue il commit della transazione|1) Il database viene contrassegnato come eliminato<br /><br /> 2) Il server esegue il commit della transazione<br /><br /> Nota: la password di scollegamento non può essere modificata per un database di sola lettura. Se viene fornito il parametro password per un database collegato che contiene già una password, verrà generato un errore.|  
  
 I comandi **Attach** e **Detach** devono essere eseguiti come singole operazioni. Non possono essere combinati con altre operazioni nella stessa transazione. Inoltre, i comandi **Attach** e **Detach** sono comandi transazionali atomici, ovvero l'operazione avrà esito positivo o negativo. Nessun database verrà lasciato in uno stato incompleto.  
  
> [!IMPORTANT]  
>  Per eseguire il comando **Detach** , sono necessari privilegi di amministratore del database o di amministratore del server.  
  
> [!IMPORTANT]  
>  Per eseguire il comando **Attach** , sono necessari privilegi di amministratore del server.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Spostare un Database di Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Passare a un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Elemento Detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Elemento Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  

