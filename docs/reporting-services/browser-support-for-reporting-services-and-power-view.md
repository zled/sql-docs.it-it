---
title: "Supporto browser per Reporting Services e Power View | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "visualizzazione di report"
  - "script [Reporting Services], requisiti"
  - "visualizzazione di report"
  - "browser [Reporting Services]"
  - "Web browser [Reporting Services], informazioni sul supporto browser"
  - "esplorazione di report [Reporting Services]"
  - "componenti [Reporting Services], browser"
  - "Web browser [Reporting Services]"
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 121
---
# Supporto browser per Reporting Services e Power View
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

Informazioni su quali versioni dei browser sono supportate per la gestione e la visualizzazione di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], i controlli ReportViewer e Power View.
  
 **Si applica a:** modalità nativa di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] | modalità SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
##  <a name="bkmk_webportal"></a> Requisiti del browser per il [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]

Di seguito è riportato l'elenco corrente dei browser supportati per il [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*
- Microsoft Edge (+)
- Microsoft Internet Explorer 10 or 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple iOS**  
*iPhone e iPad con iOS 9*

- Apple Safari (+)

**Google Android**  
*Telefoni e tablet con Android 4.4 (KitKat) o versione successiva*

- Google Chrome (+)

 **(+)** Ultima versione rilasciata pubblicamente  
  
##  <a name="bkmk_reportviewer"></a> Requisiti del browser per il controllo Web del visualizzatore di report (2015) 
 Di seguito è riportato l'elenco corrente dei browser supportati dal controllo Web del visualizzatore di report (2015). Il visualizzatore di report supporta la visualizzazione dei report dal portale Web e dalle raccolte di SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 or 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Ultima versione rilasciata pubblicamente  
  
 Se si usa un prodotto SharePoint integrato con [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], vedere  [Pianificare il supporto dei browser in SharePoint 2016](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
###  <a name="bkmk_authentication"></a> Requisiti di autenticazione  
 I browser supportano schemi di autenticazione specifici che devono essere gestiti dal server di report affinché la richiesta del client abbia esito positivo. Nella tabella seguente sono indicati i tipi di autenticazione predefiniti supportati da ogni browser eseguito in un sistema operativo Windows.  
  
|**Tipo di browser**|**Supporti**|**Impostazione predefinita del browser**|**Impostazione predefinita del server**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|Negotiate, Kerberos, NTLM, Basic|Negotiate|Sì. Le impostazioni di autenticazione predefinite funzionano con Edge.|  
|**Microsoft Internet Explorer**|Negotiate, Kerberos, NTLM, Basic|Negotiate|Sì. Le impostazioni di autenticazione predefinite funzionano con Internet Explorer.|  
|**Google Chrome**(+)|Negotiate, NTLM, Basic|Negotiate|Sì. Le impostazioni di autenticazione predefinite funzionano con Chrome.|  
|**Mozilla Firefox**(+)|NTLM, Basic|NTLM|Sì. Le impostazioni di autenticazione predefinite funzionano con Firefox.|  
|**Apple Safari**(+)|NTLM, Basic|Basic|Sì. Le impostazioni di autenticazione predefinite funzionano con Safari.|  
  
 **(+)** Ultima versione rilasciata pubblicamente  
  
### Requisiti dello script per la visualizzazione di report  
 Per utilizzare il visualizzatore di report, configurare il browser per l'esecuzione di script.  
  
 Se lo scripting non è abilitato, all'apertura di un report verrà visualizzato un messaggio di errore simile al seguente:  
  
-   **Il browser in uso non supporta gli script oppure è stato configurato in modo da non consentire l'esecuzione di script. Fare clic qui per visualizzare il report senza script**.  
  
 Se si sceglie di visualizzare il report senza il supporto per gli script, il report verrà sottoposto a rendering in HTML senza le funzionalità del visualizzatore di report, quali la barra degli strumenti per report e la mappa documento.  
  
> [!NOTE]  
>  La barra degli strumenti report fa parte del componente Visualizzatore HTML. Per impostazione predefinita la barra degli strumenti viene visualizzata nella parte superiore di ogni report di cui viene eseguito il rendering in una finestra del browser. Nel visualizzatore di report sono disponibili funzionalità tramite cui è possibile eseguire ricerche di informazioni nel report, scorrere fino a una pagina specifica e adattare le dimensioni della pagina per la visualizzazione. Per ulteriori informazioni sulla barra degli strumenti per report o sul Visualizzatore HTML, vedere [HTML Viewer and the Report Toolbar](../reporting-services/html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Supporto del browser per controlli del server Web ReportViewer in Visual Studio  
 Il controllo server Web ReportViewer è utilizzato per incorporare la funzionalità del report in un'applicazione Web ASP.NET. I controlli sono inclusi con Visual Studio e supportano browser diversi e versioni di browser differenti rispetto agli altri componenti descritti in questo argomento. Il tipo di browser utilizzato per visualizzare l'applicazione determina il tipo di funzionalità di ReportViewer che è possibile fornire nell'applicazione. Utilizzare la tabella fornita in questo argomento per determinare quali browser supportati sono soggetti a restrizioni di funzionalità e quali piattaforme sono supportate.  
  
 Utilizzare un browser in cui il supporto per gli script è abilitato. Se il browser non può eseguire script, non è possibile visualizzare il report.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 or 11
- Google Chrome (+)
- Mozilla Firefox (+)
  
 **(+)** Ultima versione rilasciata pubblicamente  
  
##  <a name="bkmk_powerview"></a> Supporto browser per Power View  

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Internet Explorer 10 or 11
- Mozilla Firefox (+)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Ultima versione rilasciata pubblicamente  
  
 Per altre informazioni sul supporto browser per SharePoint 2016, vedere [Pianificare il supporto dei browser in SharePoint 2013](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
## Vedere anche  
[Ricerca e visualizzazione dei report nel portale web &#40;Generatore Report e SSRS&#41;](http://msdn.microsoft.com/it-it/8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Strumenti di Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
[Portale Web (modalità nativa SSRS)](http://msdn.microsoft.com/it-it/7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[Visualizzatore HTML e barra degli strumenti dei report](../reporting-services/html-viewer-and-the-report-toolbar.md)  
[Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
