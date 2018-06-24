---
title: Collegamento e scollegamento di database di Analysis Services | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f8c997e90d611f1ab574ae483d4c71ee5d8fa777
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062995"
---
# <a name="attach-and-detach-analysis-services-databases"></a>Collegamento e scollegamento di database di Analysis Services
  Spesso, un amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vuole portare un database offline per un determinato periodo e quindi riportarlo online nella stessa istanza del server o in una diversa. Queste situazioni spesso sono determinate da esigenze aziendali, ad esempio lo spostamento del database in un disco diverso per migliorare le prestazioni, la necessità di ottenere più spazio per la crescita del database oppure per aggiornare un prodotto. Per tutti i casi e altro ancora, la `Attach` e `Detach` comandi viene abilitato il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba per impostare il database offline e attivare la modalità di nuovo online con un minimo sforzo.  
  
## <a name="attach-and-detach-commands"></a>Comandi Attach e Detach  
 Il `Attach` comando consente di portare online un database che è stato portato offline. È possibile collegare il database all'istanza del server originale o a un'altra istanza. Quando si collega un database, l'utente può specificare l'impostazione **ReadWriteMode** per il database. Il comando `Detach` consente di portare un database offline dal server.  
  
## <a name="attach-and-detach-usage"></a>Utilizzo di Attach e Detach  
 Il `Attach` comando consente di portare online una struttura di database esistente. Se il database viene collegato `ReadWrite` modalità, può essere collegato solo una volta a un'istanza del server. Tuttavia, se il database viene collegato `ReadOnly` modalità, può essere collegato più volte a diverse istanze del server. Tuttavia, non è possibile collegare lo stesso database più di una volta alla stessa istanza del server. Se si tenta di collegare lo stesso database più di una volta, verrà generato un errore, anche se i dati sono stati copiati in cartelle distinte.  
  
> [!IMPORTANT]  
>  Se per lo scollegamento del database è stata richiesta una password, è necessario utilizzare la stessa password per collegare il database.  
  
 Il `Detach` comando viene utilizzato per portare offline una struttura di database esistente. Quando un database viene scollegato, è consigliabile fornire una password per proteggere i metadati riservati.  
  
> [!IMPORTANT]  
>  Per proteggere il contenuto dei file di dati, utilizzare un elenco di controllo di accesso per la cartella, le sottocartelle e i file di dati.  
  
 Quando si scollega un database, nel server vengono effettuati i passaggi seguenti.  
  
|Scollegamento di un database di lettura/scrittura|Scollegamento di un database di sola lettura|  
|--------------------------------------|-------------------------------------|  
|1) Il server invia una richiesta per un blocco CommitExclusive sul database<br />2) Il server attende il commit o il rollback di tutte le transazioni in corso<br />3) Il server compila tutti i metadati necessari per scollegare il database<br />4) Il database viene contrassegnato come eliminato<br />5) Il server esegue il commit della transazione|1) Il database viene contrassegnato come eliminato<br />2) Il server esegue il commit della transazione<br /><br /> <br /><br /> Nota: la password di scollegamento non può essere modificata per un database di sola lettura. Se viene fornito il parametro password per un database collegato che contiene già una password, verrà generato un errore.|  
  
 I comandi `Attach` e `Detach` devono essere eseguiti come singole operazioni. Non possono essere combinati con altre operazioni nella stessa transazione. Inoltre, il `Attach` e `Detach` comandi sono comandi transazionali atomici. ovvero l'operazione avrà esito positivo o negativo. Nessun database verrà lasciato in uno stato incompleto.  
  
> [!IMPORTANT]  
>  Sono necessari privilegi di amministratore di database o server per eseguire il `Detach` comando.  
  
> [!IMPORTANT]  
>  Per eseguire il comando `Attach`, sono necessari privilegi di amministratore del server.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Spostare un Database di Analysis Services](move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](database-readwritemodes.md)   
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Elemento Detach](../xmla/xml-elements-commands/detach-element.md)   
 [Elemento Attach](../xmla/xml-elements-commands/attach-element.md)  
  
  