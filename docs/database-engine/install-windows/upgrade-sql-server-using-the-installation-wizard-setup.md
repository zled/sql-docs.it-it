---
title: Aggiornare SQL Server usando l'Installazione guidata (programma di installazione) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading Database Engine
- Database Engine [SQL Server], upgrading
ms.assetid: cef118a5-a7ce-4bfa-8b9d-c81996284cfc
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 840849b3d08feac21dd5b96235405773fc06f64c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607161"
---
# <a name="upgrade-sql-server-using-the-installation-wizard-setup"></a>Aggiornare SQL Server usando l'Installazione guidata (programma di installazione)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce un singolo albero delle funzionalità per l'aggiornamento sul posto dei componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla versione più recente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
>[!WARNING]  
>Quando si aggiorna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene sovrascritta e non sarà più disponibile nel computer. 
>
>Prima dell'aggiornamento, eseguire il backup dei database di SQL Server e degli altri oggetti associati all'istanza di SQL Server precedente.  
  
> [!CAUTION]  
> Per molti ambienti di produzione e alcuni ambienti di sviluppo, è consigliabile eseguire un nuovo aggiornamento dell'installazione o un aggiornamento in sequenza anziché un aggiornamento sul posto.  Per altre informazioni sui metodi di aggiornamento, vedere:
> * [Scegliere un metodo di aggiornamento del motore di database](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)
> * [Aggiornare Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)
> * [Aggiornare Integration Services](../../integration-services/install-windows/upgrade-integration-services.md)
> * [Aggiornare Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md)
> * [Eseguire l'aggiornamento e la migrazione di Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)
> * [Aggiornare Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)
> * [Aggiornare Power Pivot per SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md).  
  
## <a name="prerequisites"></a>Prerequisites  
È necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio che disponga di autorizzazioni di lettura ed esecuzione per questa condivisione remota e che a eseguire l'operazione sia un amministratore locale.  
  
> [!WARNING]  
>  Non è possibile modificare le funzionalità da aggiornare, né aggiungere funzionalità durante l'operazione di aggiornamento. Per altre informazioni su come aggiungere funzionalità a un'istanza aggiornata di [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] dopo aver completato l'aggiornamento, vedere [Aggiungere funzionalità a un'istanza di SQL Server &#40;programma di installazione&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
  
 Se si sta aggiornando il motore di database [!INCLUDE[ssDE](../../includes/ssde-md.md)], vedere [Pianificare e testare il piano di aggiornamento del motore di database](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md) , quindi eseguire queste attività in base all'ambiente in cui si opera:  
  
-   Eseguire il backup di tutti i file di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dall'istanza da aggiornare, in modo che sia possibile ripristinarli se necessario.  
  
-   Eseguire i comandi DBCC (Database Console Commands) appropriati sui database da aggiornare per assicurarne la consistenza.  
  
-   Valutare lo spazio su disco necessario per l'aggiornamento dei componenti di SQL Server, oltre che dei database utente. Per informazioni sullo spazio su disco necessario per i componenti di SQL Server, vedere [Requisiti hardware e software per l'installazione di SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Verificare che i database di sistema di SQL Server esistenti, ovvero master, model, msdb e tempdb, siano configurati per l'aumento automatico delle dimensioni e abbiano una quantità di spazio su disco sufficiente.  
  
-   Verificare che nel database master siano disponibili le informazioni di accesso per tutti i server di database. Si tratta di un elemento importante per il ripristino di un database, in quanto le informazioni di accesso al sistema risiedono nel database master.  
  
-   Disabilitare tutte le stored procedure di avvio perché i servizi verranno avviati e arrestati nell'istanza di SQL Server in fase di aggiornamento. Le stored procedure elaborate all'avvio potrebbero bloccare il processo di aggiornamento.  
  
-   In caso di aggiornamento di istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene integrato nelle relazioni MSX/TSX, aggiornare i server di destinazione prima di quelli master. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non sarà in grado di connettersi alle istanze master di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Uscire da tutte le applicazioni, inclusi tutti i servizi con dipendenze da SQL Server. L'aggiornamento potrebbe avere esito negativo se le applicazioni locali sono connesse all'istanza in fase di aggiornamento.  
  
-   Verificare che la replica sia corrente, quindi arrestare la replica.   
    Per i passaggi dettagliati dell'esecuzione di un aggiornamento in sequenza in un ambiente replicato, vedere [Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md).
  
## <a name="procedure"></a>Procedura  
  
### <a name="to-upgrade-includessnoversionincludesssnoversion-mdmd"></a>Per eseguire l'aggiornamento a [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)]  
  
1.  Inserire il supporto di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , quindi nella cartella radice fare doppio clic sul file Setup.exe. Per eseguire l'installazione da una condivisione di rete, passare alla cartella radice nella condivisione, quindi fare doppio clic sul file Setup.exe.  
  
2.  L'Installazione guidata consente di avviare il Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per aggiornare un'istanza esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], fare clic su **Installazione** nell'area di navigazione a sinistra, quindi fare clic su **Aggiorna da...** versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Nella pagina relativa al codice Product Key selezionare un'opzione per indicare se si intende eseguire l'aggiornamento a un'edizione gratuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o se si dispone di una chiave PID per una versione di produzione del prodotto. Per altre informazioni, vedere [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) e [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
4.  Nella pagina Condizioni di licenza leggere il contratto di licenza e, per accettare, selezionare la casella di controllo **Accetto le condizioni di licenza** , quindi fare clic su **Avanti**. Per migliorare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è inoltre possibile abilitare l'opzione relativa all'utilizzo delle funzionalità e inviare report a [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
5.  Nella finestra Regole globali, con la procedura di installazione si passerà automaticamente alla finestra Aggiornamenti prodotti se non vi sono errori di regole.  
  
6.  La pagina di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update verrà visualizzata successivamente se la casella di controllo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update non è selezionata in Pannello di controllo\Tutti gli elementi del Pannello di controllo\Windows Update\Modifica impostazioni. Se si seleziona la pagina [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, le impostazioni del computer vengono modificate per includere gli aggiornamenti quando si effettua l'analisi di Windows Update.  
  
7.  Nella pagina Aggiornamenti prodotto vengono visualizzati gli aggiornamenti più recenti sul prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se non si vogliono includere gli aggiornamenti, deselezionare la casella di controllo **Includi aggiornamenti prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**. Se non viene individuato alcun aggiornamento del prodotto, durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa pagina non viene visualizzata e viene aperta automaticamente la pagina **Installazione dei file di installazione** .  
  
8.  Nella pagina Installazione dei file di installazione viene mostrato lo stato del download, dell'estrazione e dell'installazione dei file di installazione. Se viene individuato un aggiornamento per il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e ne viene specificata l'inclusione, verrà installato anche questo aggiornamento.  
  
9. Nella finestra Regole di aggiornamento, con la procedura di installazione si passerà automaticamente alla finestra Seleziona istanza se non vi sono errori di regole.  
  
10. Nella pagina Seleziona istanza specificare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da aggiornare. Per aggiornare gli strumenti di gestione e le funzionalità condivise, selezionare **Aggiorna solo le funzionalità condivise**.  
  
11. Nella pagina Seleziona funzionalità le funzionalità da aggiornare saranno preselezionate. Dopo aver selezionato il nome della funzionalità desiderata, nel riquadro a destra verrà visualizzata una descrizione per ogni gruppo di componenti.  
  
     I prerequisiti per le funzionalità selezionate vengono visualizzati nel riquadro di destra. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno installati i prerequisiti che non sono stati ancora installati durante la procedura di installazione descritta più avanti in questo argomento.  
  
    > [!NOTE]  
    >  Se si è scelto di aggiornare le funzionalità condivise selezionando **\<Aggiorna solo le funzionalità condivise>** nella pagina **Seleziona istanza**, tutte le funzionalità condivise sono preselezionate nella pagina Selezione funzionalità. Tutti i componenti condivisi vengono aggiornati contemporaneamente.  
  
12. Nella pagina Configurazione istanza specificare l'ID istanza per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     **ID istanza** : per impostazione predefinita, come ID istanza viene utilizzato il nome dell'istanza. Tale nome viene utilizzato per identificare le directory di installazione e le chiavi del Registro di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si tratta del caso delle istanze predefinite e delle istanze denominate. Per un'istanza predefinita, il nome di istanza e l'ID istanza sono MSSQLSERVER. Per utilizzare un ID istanza non predefinito, specificare un valore per la casella di testo **ID istanza** .  
  
     Tutti i Service Pack e gli aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno applicati a ogni componente di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     **Istanze installate**  : la griglia visualizzerà le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenti nel computer in cui viene eseguita l'installazione. Se nel computer è già installata un'istanza predefinita, è necessario installare un'istanza denominata di [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)].  
  
13. Il flusso di lavoro relativo alla parte rimanente di questo articolo dipende dalle funzionalità specificate per l'installazione. Le pagine visualizzate dipendono dalle selezioni effettuate.  
  
14. Nella pagina Configurazione server - Account di servizio gli account del servizio predefiniti vengono visualizzati per i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I servizi effettivamente configurati in questa pagina dipendono dalle funzionalità sottoposte ad aggiornamento.  
  
     Le informazioni relative all'autenticazione e all'accesso verranno trasferite dall'istanza precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile assegnare lo stesso account di accesso a tutti i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure configurare singolarmente l'account di ogni servizio. È inoltre possibile specificare se i servizi verranno avviati automaticamente, manualmente o se sono disabilitati. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di configurare singolarmente gli account del servizio in modo da garantire ai servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le autorizzazioni minime necessarie per completare le attività. Per altre informazioni, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Per specificare lo stesso account di accesso per tutti gli account del servizio nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], immettere le credenziali nei campi visualizzati nella parte inferiore della pagina.  
  
     **Nota sulla sicurezza** [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
     Dopo aver specificato le informazioni di accesso per i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fare clic su **Avanti**.  
  
15. Nella pagina Opzioni di aggiornamento della ricerca full-text specificare le opzioni per i database da aggiornare. Per altre informazioni, vedere [Opzioni di aggiornamento della ricerca full-text](https://msdn.microsoft.com/library/16c9376b-5fbb-4495-a429-06a2493849c9).  
  
16. Se tutte le regole vengono soddisfatte si procede automaticamente dalla finestra Regole funzionalità.  
  
17. Nella pagina Inizio aggiornamento è presente una visualizzazione albero delle opzioni specificate durante l'installazione. Per continuare, fare clic su **Installa**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno innanzitutto installati i prerequisiti obbligatori per le funzionalità selezionate e, successivamente, le funzionalità stesse.  
  
18. Durante l'installazione, nella pagina relativa allo stato è possibile monitorare lo stato di avanzamento dell'installazione.  
  
19. Al termine dell'installazione nella pagina Operazione completata viene visualizzato un collegamento al file di log di riepilogo del processo di installazione e ad altre note importanti. Per completare il processo di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fare clic su **Chiudi**.  
  
20. Se viene richiesto, riavviare il computer. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni sui file di log del programma di installazione, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="next-steps"></a>Next Steps  
 Al termine dell'aggiornamento a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], completare le attività seguenti:  
  
-   **Registrare i server** : poiché l'operazione di aggiornamento rimuove le impostazioni del Registro di sistema per la precedente istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in seguito all'aggiornamento è necessario registrare nuovamente i server.  
  
-   **Aggiornare le statistiche** : per ottimizzare le prestazioni delle query, in seguito all'aggiornamento è consigliabile aggiornare le statistiche per tutti i database. Utilizzare la stored procedure **sp_updatestats** per aggiornare le statistiche nelle tabelle definite dall'utente dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Configurare la nuova installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: per ridurre la superficie di attacco di un sistema, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati e abilitati in modo selettivo i servizi e le funzionalità principali. Per ulteriori informazioni sulla configurazione della superficie di attacco, vedere il file Leggimi per questa versione.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire l'aggiornamento di SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)   
 [Backward Compatibility_deleted](https://msdn.microsoft.com/library/15d9117e-e2fa-4985-99ea-66a117c1e9fd)  
  
  
