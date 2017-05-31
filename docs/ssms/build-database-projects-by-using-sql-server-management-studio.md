---
title: Compilare progetti di database con SQL Server Management Studio | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a3487f9048571511460bc22b5c0b605592ba74f5
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a>Compilazione di progetti di database utilizzando SQL Server Management Studio
Un progetto di script del database è un set organizzato di script, informazioni di connessione e modelli tutti associati a un database o a una parte di un database. [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] include [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] per l'amministrazione e la progettazione di database di [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] nel contesto di un progetto script. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] include finestre di progettazione, editor, guide e procedure guidate per assistere gli utenti nello sviluppo, nella distribuzione e nella gestione di database.  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] è un insieme di strumenti di amministrazione per la gestione dei componenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)]. Questo ambiente integrato consente l'esecuzione di un'ampia gamma di attività, quali backup dei dati, modifica delle query e automazione delle funzioni comuni, all'interno di un'unica interfaccia.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] include i seguenti strumenti:  
  
-   Editor del codice, un editor completo per la scrittura e la modifica degli script [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] offre quattro versioni dell'editor di codice: l'editor di query [!INCLUDE[ssDE](../includes/ssde_md.md)] per script [!INCLUDE[tsql](../includes/tsql_md.md)] , l'editor di query DMX, l'editor di query MDX e l'editor di query XML/A.  
  
-   Esplora oggetti, per l'individuazione, la modifica, la creazione di script o l'esecuzione di oggetti appartenenti a istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)].  
  
-   Esplora modelli, per l'individuazione e la creazione di script di modelli.  
  
-   Esplora soluzioni, per l'organizzazione e l'archiviazione di script correlati come parti di un progetto.  
  
-   Finestra Proprietà, per la visualizzazione delle proprietà correnti degli oggetti selezionati.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] supporta processi di lavoro efficienti offrendo quanto segue:  
  
-   Accesso disconnesso. È possibile creare e modificare script senza connettersi a un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)].  
  
-   Creazione di script da qualsiasi finestra di dialogo. È possibile creare uno script da qualsiasi finestra di dialogo, così da poter leggere, modificare, archiviare e riutilizzare gli script dopo averli creati.  
  
-   Finestre di dialogo non modali. Quando si accede a una finestra di dialogo dell'interfaccia utente è possibile esplorare altre risorse in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] senza chiudere la finestra.  
  
## <a name="solutions-and-script-projects"></a>Soluzioni e progetti script  
Esplora soluzioni è un'utilità per l'archiviazione e la riapertura di soluzioni di database. Le soluzioni consentono di organizzare progetti script e file correlati. I progetti script consentono di archiviare file script di [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] , modelli SQL, informazioni di connessione e file esterni. Quando uno script è salvato in un progetto script è possibile:  
  
-   Mantenere il controllo della versione degli script.  
  
-   Archiviare opzioni di risultati con gli script.  
  
-   Organizzare script correlati in un unico progetto script.  
  
-   Salvare le informazioni di connessione con gli script.  
  
Esplora soluzioni è uno strumento per gli sviluppatori che creano e riutilizzano script correlati allo stesso progetto. Se in un momento successivo si rende necessaria un'attività simile, è possibile utilizzare i gruppi di script archiviati in un progetto. Se sono state create applicazioni usando [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[vsprvs](../includes/vsprvs_md.md)], Esplora soluzioni risulterà semplice da usare.  
  
Una soluzione è costituita da uno o più progetti script. Un progetto è costituito da uno o più script o connessioni. Un progetto può anche contenere file che non sono script.  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzo di SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Scrittura, analisi e modifica di query con SQL Server Management Studio](http://msdn.microsoft.com/en-us/062051e4-4b77-4969-98ae-d2547c24ce3e)  
[Soluzioni &amp;#40;SQL Server Management Studio&amp;#41;](../ssms/solution/solutions-sql-server-management-studio.md)  
  

