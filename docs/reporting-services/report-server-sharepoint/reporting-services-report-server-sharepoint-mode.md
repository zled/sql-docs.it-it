---
title: "Server Reporting Services Report (modalità SharePoint) | Documenti Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a8cd1bd00ec92535fff73c5eaa4ff9bbe9274ef2
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---

# <a name="reporting-services-report-server-sharepoint-mode"></a>Server di report di Reporting Services (modalità SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Un server di report di Reporting Services configurato per **modalità SharePoint** può essere eseguito in una distribuzione di un prodotto SharePoint. Tramite un server di report in modalità SharePoint è possibile utilizzare le funzionalità di collaborazione e gestione di SharePoint per report e altri tipi di contenuto di [!INCLUDE[ssRSnfoversion_md](../../includes/ssrsnoversion-md.md)] . Modalità SharePoint è necessario installare la versione appropriata del componente aggiuntivo Reporting Services per prodotti SharePoint in SharePoint Web front-end di.  
  
> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

 Per ulteriori informazioni sull'installazione e sulla configurazione, vedere quanto riportato di seguito:  
  
-   [Installare la modalità SharePoint di Reporting Services per SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c).  
  
-   [Aggiungere un ulteriore Server di Report a una farm](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
## <a name="feature-summary"></a>Riepilogo delle funzionalità

 Quando si configura un server di report per l'esecuzione in modalità integrata SharePoint vengono aggiunte le funzionalità seguenti, che sono disponibili solo quando si distribuisce un server di report in tale modalità:  
  
-   Funzionalità di gestione dei documenti e collaborazione di SharePoint, inclusi avvisi. Un sito di SharePoint costituisce un portale unificato per l'accesso e la gestione di tutti gli elementi del report da un'unica posizione.  
  
-   Provider di autenticazione e autorizzazioni di SharePoint, per controllare l'accesso a report, modelli e altri elementi.  
  
-   Topologie di distribuzione di SharePoint per la distribuzione di report fuori dal firewall tramite una connessione Internet. Il server di report fornisce i servizi di report ed elaborazione dati nel contesto di una distribuzione di SharePoint più ampia, configurata per l'accesso a Internet.  
  
-   Gestione di report, modelli, origini dei dati, pianificazioni e cronologia dei report in pagine di applicazione personalizzate in un sito di SharePoint. È possibile impostare proprietà, definire pianificazioni e sottoscrizioni, nonché creare e gestire cronologie di report in un sito di SharePoint esattamente come avviene con gli altri strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pubblicazione o caricamento di report, modelli di report, risorse e file di origini dati condivise in una raccolta di SharePoint, incluso il Centro report in Office SharePoint Server.  
  
     Utilizzo di Progettazione report, Progettazione modelli e Generatore report per creare report e origini dati da pubblicare direttamente in una raccolta di SharePoint. È inoltre possibile utilizzare l'azione Carica in un sito di SharePoint per aggiungere qualsiasi definizione di report e modello di report a una raccolta di SharePoint.  
  
     Poiché il server di report elabora le definizioni dei report sempre allo stesso modo, indipendentemente dalla modalità del server utilizzata, il layout e i dati del report sono indipendenti dalla modalità del server. Tutti i report eseguibili in un server di report in modalità nativa possono essere eseguiti anche in un server di report configurato per la modalità integrata SharePoint.  
  
-   Sottoscrizione e recapito di report a una raccolta di SharePoint tramite una nuova estensione per il recapito di SharePoint. I report possono essere recapitati anche per posta elettronica o a una cartella condivisa. Per recapitare i report vengono utilizzate le estensioni per il recapito del server di report. È possibile creare sottoscrizioni guidate dai dati per una distribuzione di report su vasta scala utilizzando i dati del sottoscrittore sottoposti a query in fase di esecuzione.  
  
-   Una web part Visualizzatore Report è possibile aggiungere alle pagine di SharePoint per visualizzare un report all'interno dell'applicazione web di SharePoint. La web part include lo spostamento di pagina, ricercare, stampare e le funzionalità di esportazione.  
  
-   Utilizzo di un nuovo endpoint SOAP per la realizzazione di applicazioni personalizzate da integrare con un sito di SharePoint. È inoltre possibile utilizzare il provider WMI (Windows Management Instrumentation, Strumentazione gestione Windows) aggiornato per configurare a livello di programmazione un'istanza del server di report eseguita in modalità integrata SharePoint.  
  
-   Creazione di report di servizi Microsoft Access in modalità connessa.  
  
-   Aree AAM, distribuzioni che si interfacciano a Internet e token utenti di SharePoint per elenchi SharePoint.  
  
## <a name="connected-mode-and-local-mode"></a>Modalità locale e modalità connessa

 Con la versione SQL Server 2008 R2 viene introdotta una nuova *modalità locale* per la visualizzazione di report da un server SharePoint 2010 in cui è installato il componente aggiuntivo Reporting Services di Microsoft SQL Server 2008 R2 o versione successiva per prodotti SharePoint 2010.  
  
-   *Modalità locale*: modalità locale consente di eseguire il rendering in locale dalla raccolta documenti di SharePoint, senza l'integrazione con un server di report di Reporting Services. Il componente aggiuntivo di Reporting Services per prodotti SharePoint è obbligatorio, ma non è un server di report di Reporting Services. Il componente aggiuntivo può essere installato in diversi modi, tra cui l'Utilità preparazione prodotti Microsoft SharePoint 2010. Per ulteriori informazioni sulla modalità locale, vedere [modalità locale e report nel Visualizzatore di Report](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md) e [dove trovare il componente aggiuntivo di Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Modalità connessa*: modalità connessa è supportata tramite l'integrazione di un server di report di Reporting Services nella farm di SharePoint utilizzando Amministrazione centrale SharePoint. L'integrazione con un server di report consente la creazione completa di report, fornendo le funzionalità di collaborazione di SharePoint 2010 e le funzionalità basate su server di un server di report, tra cui sottoscrizioni, snapshot ed elaborazione basata su server.  
  
## <a name="unsupported-sharepoint-features"></a>Funzionalità di sharePoint non supportate

 Non tutte le funzionalità di SharePoint sono disponibili per le operazioni in modalità integrata. Di seguito è riportato un elenco di funzionalità SharePoint di in che Reporting Services non direttamente integrate:  
  
-   Servizio di archiviazione sicura.  
  
-   In una raccolta documenti non è possibile utilizzare l'integrazione con il calendario di Outlook in SharePoint o la funzionalità di pianificazione di SharePoint per i file di Reporting Services.  
  
-   Catalogo dati business di SharePoint.  
  
-   Personalizzazione di SharePoint non supportata neanche nelle pagine di Reporting Services. L'integrazione del server di report non è supportata se l'applicazione Web di SharePoint è abilitata per l'accesso anonimo.  
  
-   SQL Server Reporting Services **non** supporta il controllo della versione della raccolta documenti di SharePoint. Se si salvano gli elementi del report in una raccolta documenti configurata con la cronologia delle versioni dei documenti abilitata, le funzionalità di Reporting Services non funzioneranno correttamente e verranno generati errori nel log ULS. Di seguito è riportato un esempio di errore nel log ULS:  
  
    -   "Un'origine dati associata al report è stata disabilitata".  
  
     La cronologia delle versioni della raccolta documenti viene configurata nella pagina "Impostazioni controllo versioni" di "Impostazioni raccolta".  
  
## <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a>Combinazioni supportate del server di SharePoint componente aggiuntivo e report

 Non tutte le funzionalità sono supportate in tutte le combinazioni di server di report, componente aggiuntivo di Reporting Services per SharePoint e prodotti SharePoint. Per ulteriori informazioni, vedere [combinazioni supportate di SharePoint e Server di Reporting Services e componente aggiuntivo](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  La versione corretta del componente aggiuntivo di Reporting Services deve essere utilizzata con la versione corrispondente dei prodotti SharePoint.  
  
## <a name="components-that-provide-integration"></a>Componenti che offrono funzionalità di integrazione

 Per combinare i server in un'unica distribuzione, integrare un'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services con un'istanza di prodotti SharePoint  
  
 Integrazione viene realizzata tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il componente aggiuntivo di Reporting Services per prodotti SharePoint. Il componente aggiuntivo di Reporting Services è un componente distribuito gratuitamente, che è possibile scaricare e quindi installare in un server che esegue la versione appropriata di SharePoint.  
  
> [!TIP]  
>  Non tutte le funzionalità sono supportate in tutte le combinazioni di server di report, componente aggiuntivo di Reporting Services per SharePoint e prodotti SharePoint. Per ulteriori informazioni, vedere [combinazioni supportate di SharePoint e Server di Reporting Services e componente aggiuntivo](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   In SharePoint, il componente aggiuntivo di Reporting Services fornisce l'endpoint proxy ReportServer, una web part Visualizzatore Report e pagine dell'applicazione in modo che è possibile visualizzare, archiviare e gestire il contenuto di server di report in un sito di SharePoint o una farm.  
  
-   In Reporting Services fornisce file di programma aggiornati, un endpoint SOAP e le estensioni di sicurezza e il recapito personalizzate. È necessario configurare il server di report affinché venga eseguito in modalità integrata SharePoint e sia dedicato esclusivamente al supporto del recapito e dell'accesso ai report tramite il sito di SharePoint.  
  
 Dopo avere installato il componente aggiuntivo di Reporting Services in SharePoint e configurare i due server per l'integrazione, è possibile caricare o pubblicare i tipi di contenuto di server di report in una raccolta di SharePoint e quindi visualizzare e gestire tali documenti da un sito di SharePoint. Il caricamento o pubblicazione di contenuto del server di report è un importante primo passaggio; la web part e le pagine diventano disponibili quando si seleziona le definizioni dei report (con estensione rdl), modelli (con estensione SMDL) di report e origini dati condivise (rsds) in un sito di SharePoint.  
  
##  <a name="language-considerations"></a>Considerazioni sul linguaggio

 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] e [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] sono disponibili in molte più lingue rispetto a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Quando si configura un server di report per l'esecuzione in una distribuzione di un prodotto SharePoint, è possibile che i vari elementi vengano visualizzati in lingue diverse. L'interfaccia utente, la documentazione e i messaggi verranno visualizzati nelle lingue seguenti:  
  
-   Tutte le pagine dell'applicazione, strumenti, gli errori, avvisi e i messaggi che provengono da Reporting Services verranno visualizzati nella lingua utilizzata dall'istanza di Reporting Services in uno del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lingue.  
  
-   Pagine dell'applicazione che vengono aperti in un sito di SharePoint, web part Visualizzatore Report e Generatore Report saranno visualizzati in una delle lingue supportate per il componente aggiuntivo di Reporting Services. Per visualizzare l'elenco delle lingue supportate, visitare [download di SQL Server](http://msdn.microsoft.com/sql/downloads/) e cercare la pagina di download per SQL Server 2016 Reporting Services Add-in.  
  
-   I siti di SharePoint, Amministrazione centrale SharePoint, la Guida online e i messaggi sono disponibili nelle lingue supportate dai prodotti Office Server.  
  
 Se la lingua del prodotto SharePoint o della tecnologia è diversa dalla lingua del server di report, Reporting Services tenterà di utilizzare la lingua della stessa famiglia di linguaggio che fornisce la corrispondenza più vicina. Se non è disponibile un sostituto sufficientemente simile, per il server di report verrà utilizzata la lingua inglese.  
  
## <a name="related-tasks"></a>Attività correlate

 Nella tabella seguente vengono riepilogate le attività correlate a un server di report in modalità SharePoint di Reporting Services:  
  
|**Attività**|**Collegamento**|  
|--------------|--------------|  
|Procedura dettagliata per l'installazione e configurazione di Reporting Services in modalità SharePoint.|[Installare la modalità SharePoint di Reporting Services per SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c) e [aggiungere un ulteriore Server di Report a una farm](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Scalabilità orizzontale la distribuzione di SharePoint di Reporting Services tramite l'aggiunta di server di report aggiuntivi.|[Aggiungere un ulteriore Server di Report a una Farm](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) e [topologie di distribuzione per le funzionalità di SQL Server Business Intelligence di SharePoint](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26).|  
|Aggiungere altre web front-end SharePoint che includono i componenti di Reporting Services installati per gli elementi del report e la visualizzazione.|[Aggiungere un ulteriore web front-end di Reporting Services a una farm](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Configurare la posta elettronica del server di report all'interno di SharePoint.|[Configurare la posta elettronica per un'applicazione di servizio Reporting Services](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|
|Informazioni recenti per questa versione, disponibili nel sito Wiki TechNet.|[Suggerimenti di SQL Server 2012 Reporting Services, suggerimenti e risoluzione dei problemi](http://go.microsoft.com/fwlink/?LinkId=221297).|  

## <a name="next-steps"></a>Passaggi successivi

[Installare o disinstallare Reporting Services sdd aggiuntivo per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
[Report web part del visualizzatore in un sito di SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
[Quiz: Configurazione di SSRS 2012 per l'integrazione con SharePoint](http://go.microsoft.com/fwlink/?LinkId=306443)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
