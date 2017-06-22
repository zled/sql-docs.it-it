---
title: "Le impostazioni del sito e le funzionalità del sito (modalità SharePoint) di Reporting Services | Documenti Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
caps.latest.revision: 10
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 044346bd4532c691861689662edbcbb37812b7ff
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="site-settings-and-features---reporting-services"></a>Le impostazioni del sito e funzionalità - Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] La modalità SharePoint include diverse funzionalità personalizzate a livello di sito e la funzionalità del sito che può essere gestita dalla pagina Impostazioni sito SharePoint. Le impostazioni sono a livello di sito e riguardano tutte le applicazioni di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per visualizzare questa pagina, è necessario disporre delle autorizzazioni Gestione contenuto e Amministratore sistema.  
  
|Impostazione del sito|Description|  
|------------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Impostazioni sito|Le impostazioni a livello di sito descritte in questo argomento.|  
|Gestisci avvisi dati|Funzionalità di gestione dei dati di avviso.|  
|Sincronizzazione file server di report|Funzionalità a livello di sito che è disattivata per impostazione predefinita.<br /><br /> Sincronizza i file del server di report (estensioni .rdl, .rsds, .smdl, .rsd, .rsc, .rdlx) da una raccolta documenti di SharePoint al server di report quando i file vengono aggiunti o aggiornati direttamente nella raccolta documenti.<br /><br /> Per altre informazioni, vedere [Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>Per aprire la pagina Impostazioni sito di Reporting Services  
  
1.  Scegliere **Impostazioni sito** dal menu **Azioni sito**del sito di SharePoint.  
  
2.  Nella sezione **Reporting Services** fare clic su **Impostazioni del sito per Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Opzioni per Impostazioni del sito per Reporting Services  
  
|Opzione|Description|  
|------------|-----------------|  
|**Consenti download del controllo ActiveX RSClientPrint**|Il controllo visualizza una finestra di dialogo di stampa personalizzata che supporta funzionalità comuni ad altre finestre di dialogo di stampa, inclusi l'anteprima di stampa, la selezione delle pagine per specificare pagine e intervalli, i margini delle pagine e l'orientamento. Per altre informazioni sul controllo, vedere [Utilizzo del controllo RSClientPrint in applicazioni personalizzate](../../reporting-services/report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Abilita i messaggi di errore in modalità locale**|Mostra o nasconde i messaggi di errore dettagliati nei computer remoti quando in esecuzione in modalità locale. Se viene visualizzato un messaggio di errore simile al seguente è possibile che l'abilitazione di errori remoti sia utile:<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Abilita i metadati di accessibilità per i report**|Abilita i metadati di accessibilità nell'output HTML per i report|  
|**Abilita ridimensionamento visualizzazioni di dati esatto per i report**|Configurare il comportamento di adattamento per la visualizzazione dei dati in una tablix, in modo che si adattino esattamente. Sono inclusi grafici, misuratori e mappe. Se l'opzione è disabilitata, il comportamento per la visualizzazione dei dati consiste nell'adattamento approssimativo che potrebbe lasciare spazi vuoti. Questa impostazione si applica solo al rendering nella Web part del visualizzatore di report. Per gestire questo comportamento per il rendering lato server è necessario modificare il file **rsreportserver.config** . Per altre informazioni, vedere quanto segue:<br /><br /> [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Personalizzare i parametri di estensione per il rendering in RSReportServer.config](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [Impostazioni relative alle informazioni sul dispositivo HTML](../../reporting-services/html-device-information-settings.md).<br /><br /> L'abilitazione del ridimensionamento esatto può avere impatto sulle prestazioni perché l'elaborazione per determinare la dimensione esatta potrebbe impiegare più molto tempo di un adattamento approssimativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire un'applicazione di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
