---
title: Report in modalità locale e Connessione nel Visualizzatore di Report (Reporting Services in modalità SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cbae778b06c90f1e18cb5e45119a09e25d634738
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165311"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a>Report in modalità locale e Report in modalità locale nel visualizzatore di report (Reporting Services in modalità SharePoint)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] i report possono essere configurati per l'esecuzione in *modalità locale* oppure *modalità connessa*, che usa un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report. In alternativa, è possibile utilizzare il visualizzatore di report per eseguire il rendering dei report direttamente da SharePoint quando l'estensione per i dati supporta la creazione di report in modalità locale. Questo approccio è definito *modalità locale*. Nelle versioni precedenti di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], la farm di SharePoint è necessaria essere connessi a un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server è configurato in modalità SharePoint così il controllo Visualizzatore Report è stato possibile eseguire il rendering di report. Questo approccio è definito *modalità remota* o *modalità con connessione*.  
  
 Nelle *modalità locale* è presente alcun [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report. È necessario installare il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] componente aggiuntivo per prodotti SharePoint, ma non [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è richiesto il server di report. Con la modalità locale, gli utenti possono visualizzare report ma non potranno accedere alle funzionalità lato server quali sottoscrizioni e avvisi dati.  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint|  
  
 **Contenuto dell'argomento:**  
  
-   [Confronto tra modalità locale e modalità connessa ed estensioni supportate](#bkmk_local_vs_connected)  
  
-   [Configurare la modalità locale e Access Services con SharePoint 2013](#bkmk_local_mode_sharepoint2013)  
  
-   [Configurare la creazione di report in modalità locale con SharePoint 2010](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="bkmk_local_vs_connected"></a> Confronto tra modalità locale e modalità connessa ed estensioni supportate  
 **Modalità locale:** se è disponibile un'estensione per i dati che supporta la modalità locale, il Visualizzatore report esegue direttamente il rendering dei report da SharePoint. Nelle *modalità locale* è presente alcun [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report. È necessario installare il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] componente aggiuntivo per prodotti SharePoint, ma non [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è richiesto il server di report. Con la modalità locale, gli utenti possono visualizzare report ma **non** potranno accedere alle funzionalità lato server quali sottoscrizioni e avvisi dati.  
  
 **Modalità connessa**, definita anche *modalità remota* richiede una [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report in modalità SharePoint, connesso alla farm di SharePoint in modo che il controllo Visualizzatore Report è stato possibile eseguire il rendering di report...  
  
 Di seguito è riportato un elenco delle estensioni per l'elaborazione dati che supportano la creazione di report in modalità locale:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Estensione per il reporting Access 2010. Per altre informazioni su Access Services, vedere l'articolo [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686)(Utilizzo di Access Services con SQL Reporting Services: installazione del componente aggiuntivo SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)).  
  
-   Estensione per i dati dell'elenco SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Per altre informazioni sull'estensione dati elenco SharePoint, vedere [origini dati supportate da Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
 È inoltre possibile sviluppare estensioni personalizzate per l'elaborazione dati per il supporto della modalità locale. Per ulteriori informazioni, vedere [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 Nella modalità locale è possibile eseguire il rendering di report che presentano un'origine dati incorporata o un'origine dati condivisa da un file rsds. Non è tuttavia possibile gestire il report o la relativa origine dati associata. Se si tenta di eseguire questa operazione, un errore segnalerà che tale operazione non è supportata in modalità locale. La gestione delle origini dati nel sito di SharePoint è supportata solo in modalità con connessione.  
  
> [!NOTE]  
>  Come nelle versioni precedenti, non è possibile incorporare nomi utente e password nel file con estensione rsds.  
  
##  <a name="bkmk_local_mode_sharepoint2013"></a> Configurare la modalità locale e Access Services con SharePoint 2013  
 È possibile configurare la farm di SharePoint 2013 per supportare database Web esistenti di Access 2010 e la modalità locale di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Per ulteriori informazioni, vedere l'articolo relativo all' [installazione e alla configurazione dei servizi di Access 2010 per database Web in SharePoint Server 2013](http://technet.microsoft.com/library/ee748653\(office.15\).aspx).  
  
 Non è possibile creare nuovi database Web di Access per SharePoint 2013. In Access 2013 viene utilizzato un nuovo tipo di database, *app Web Access* che si compila in Access e quindi si utilizza e condivide con altri come app SharePoint in un Web browser.  
  
 Per ulteriori informazioni, vedere quanto segue.  
  
-   [Novità di Access 2013](http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).  
  
-   [Attività di base per un'app Access](http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).  
  
##  <a name="bkmk_local_mode_sharepoint2010"></a> Configurare la creazione di report in modalità locale con SharePoint 2010  
 La modalità locale richiede lo stato della sessione ASP.NET. L'installazione di Access Services abilita lo stato delle sessioni ASP.NET. È inoltre possibile eseguire l'abilitazione tramite PowerShell.  
  
1.  Aprire la shell di gestione di SharePoint 2010.  
  
2.  Digitare il comando seguente:  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  Quando richiesto, digitare il nome del database.  
  
4.  Eseguire una reimpostazione IIS.  
  
 Per altre informazioni, vedere l'articolo [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686) (Utilizzo di Access Services con SQL Reporting Services: installazione del componente aggiuntivo SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)) e [Enable-SPSessionStateService](http://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).  
  
## <a name="connected-mode"></a>modalità connessa  
 Per informazioni aggiornate sull'uso delle estensioni ADS con [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità connessa, vedere [Report di Access Services nel sito di SharePoint viene visualizzato errore nei dati di estensione 'ADS'](http://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
