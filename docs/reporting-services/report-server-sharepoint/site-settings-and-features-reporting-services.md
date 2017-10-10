---
title: "Impostazioni del sito di Reporting Services e del sito di funzionalità (modalità SharePoint) | Documenti Microsoft"
ms.custom: 
ms.date: 09/25/2017
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
ms.openlocfilehash: ea81c248f302e322d981b90147d42cb83a4804cc
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-site-settings-and-site-features-sharepoint-mode"></a>Creazione di report le impostazioni del sito di servizi e le funzionalità del sito (modalità SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Reporting Services in modalità SharePoint dispone di diverse funzionalità personalizzate livello del sito e le funzionalità del sito che possono essere gestite dalla pagina Impostazioni sito di SharePoint. Le impostazioni sono a livello di sito e influiscono su tutte le applicazioni di servizio Reporting Services. Per visualizzare questa pagina, è necessario disporre delle autorizzazioni Gestione contenuto e Amministratore sistema.  

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

|Impostazione del sito|Description|  
|------------------|-----------------|  
|Impostazioni del sito di Reporting Services|Impostazioni a livello di sito descritte in questo argomento.|  
|Gestisci avvisi dati|Funzionalità di gestione dei dati di avviso.|  
|Sincronizzazione file server di report|Funzionalità a livello di sito che è disattivata per impostazione predefinita.<br /><br /> Sincronizza i file del server di report (estensioni .rdl, .rsds, .smdl, .rsd, .rsc, .rdlx) da una raccolta documenti di SharePoint al server di report quando i file vengono aggiunti o aggiornati direttamente nella raccolta documenti.<br /><br /> Per altre informazioni, vedere [Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)|  
  
## <a name="open-the-reporting-services-site-settings-page"></a>Aprire la pagina Impostazioni sito di Reporting Services
  
1.  Dal sito di SharePoint **Azioni sito** dal menu **Impostazioni sito**.  
  
2.  Nel **Reporting Services** selezionare **Impostazioni sito per Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Opzioni per le impostazioni del sito di Reporting Services
  
|Opzione|Description|  
|------------|-----------------|  
|**Consenti download del controllo ActiveX RSClientPrint**|Il controllo visualizza una finestra di dialogo di stampa personalizzata che supporta funzionalità comuni ad altre finestre di dialogo di stampa, inclusi l'anteprima di stampa, la selezione delle pagine per specificare pagine e intervalli, i margini delle pagine e l'orientamento. Per altre informazioni sul controllo, vedere [Utilizzo del controllo RSClientPrint in applicazioni personalizzate](../../reporting-services/report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Abilita i messaggi di errore in modalità locale**|Mostra o nasconde i messaggi di errore dettagliati nei computer remoti quando in esecuzione in modalità locale. Se viene visualizzato un messaggio di errore simile al seguente è possibile che l'abilitazione di errori remoti sia utile:<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Abilita i metadati di accessibilità per i report**|Abilita i metadati di accessibilità nell'output HTML per i report|  
|**Abilita ridimensionamento visualizzazioni di dati esatto per i report**|Configurare il comportamento di adattamento per la visualizzazione dei dati in una tablix, in modo che si adattino esattamente. Sono inclusi grafici, misuratori e mappe. Se l'opzione è disabilitata, il comportamento per la visualizzazione dei dati consiste nell'adattamento approssimativo che potrebbe lasciare spazi vuoti. Questa impostazione si applica solo al rendering nella web part Visualizzatore Report. Per gestire questo comportamento per il rendering lato server, è necessario modificare il **RSReportServer. config** file. Per altre informazioni, vedere quanto segue:<br /><br /> [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Personalizzare i parametri di estensione per il rendering in RSReportServer.config](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [Impostazioni relative alle informazioni sul dispositivo HTML](../../reporting-services/html-device-information-settings.md).<br /><br /> L'abilitazione del ridimensionamento esatto può avere impatto sulle prestazioni perché l'elaborazione per determinare la dimensione esatta potrebbe impiegare più molto tempo di un adattamento approssimativo.|  
  
## <a name="see-also"></a>Vedere anche

 [Gestire un'applicazione di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
