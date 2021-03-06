---
title: Modificare l'estensione per il recapito predefinita di Reporting Services | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b5de95f97dc6ba0b8adb1cc0ad37f3ad08e59c1e
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813094"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a>Modificare l'estensione per il recapito predefinita di Reporting Services
  È possibile modificare le impostazioni di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per modificare l'estensione per il recapito predefinita visualizzata nell'elenco **Recapito** di una pagina di definizione della sottoscrizione. Ad esempio, è possibile modificare la configurazione in modo che, quando viene creata una nuova sottoscrizione, il recapito della condivisione file venga selezionato per impostazione predefinita al posto del recapito tramite posta elettronica. È inoltre possibile modificare l'ordine con cui sono elencate le estensioni per il recapito nell'interfaccia utente.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] | Modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]   
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include le estensioni per il recapito tramite posta elettronica e condivisione file di Windows. Nel server di report potrebbero essere disponibili ulteriori estensioni per il recapito, se sono state distribuite estensioni personalizzate o di terze parti per supportare funzionalità di recapito particolari. Un'estensione per il recapito è disponibile se è distribuita in un server di report.  
  
## <a name="default-native-mode-report-server-configuration"></a>Configurazione dei server di report con modalità nativa predefinita  
 L'ordine con cui un'estensione per il recapito viene visualizzata nell'elenco **Recapito** di Gestione report dipende dall'ordine delle voci dell'estensione presenti nel file **RSReportServer.config** . Ad esempio, nell'immagine seguente Posta elettronica è visualizzato per primo ed è selezionato per impostazione predefinita.  
  
 ![Elenco predefinito di estensioni per il recapito](../../reporting-services/subscriptions/media/ssrs-default-delivery.png "Elenco predefinito di estensioni per il recapito")  
  
 Di seguito è riportata la sezione predefinita **RSReportServer.config** che controlla l'estensione per il recapito predefinita e l'ordine di visualizzazione in Gestione Report. Si noti che Posta elettronica viene visualizzato per primo nel file ed è impostato come predefinito.  
  
```  
<DeliveryUI>  
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
               <Configuration>  
               <RSEmailDPConfiguration>  
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
               </RSEmailDPConfiguration>  
               </Configuration>  
     </Extension>  
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>  
</DeliveryUI>  
```  
  
#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a>Configurare il recapito della condivisione file come estensione per il recapito predefinita in Gestione report  
  
1.  I passaggi descritti in questa procedura consentono di modificare la configurazione in modo che il recapito tramite condivisione file venga elencato come prima opzione nell'interfaccia utente e sia la selezione predefinita.  
  
     Aprire il file RSReportServer.config in un editor di testo. Per altre informazioni sul file di configurazione, vedere [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md). Dopo la modifica della configurazione, l'interfaccia utente sarà simile all'immagine seguente:  
  
     ![Elenco modificato di estensioni per il recapito](../../reporting-services/subscriptions/media/ssrs-modified-delivery.png "Elenco modificato di estensioni per il recapito")  
  
2.  Modificare la sezione DeliveryUI in modo che somigli all'esempio seguente e prendere nota delle principali modifiche:  
  
    1.  L'estensione FileShare precede l'estensione per la posta elettronica. Verrà modificato l'ordine di visualizzazione delle estensioni in Gestione Report.  
  
    2.  L'estensione per la condivisione file contiene il tag DefaultExtension `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` ed è stato aggiunto il tag di fine estensione `</Extension>`.  
  
    3.  L'estensione per la posta elettronica non è più l'impostazione predefinita. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`  
  
    ```  
    <DeliveryUI>  
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">  
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
         </Extension>  
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>  
         <Configuration>  
              <RSEmailDPConfiguration>  
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
              </RSEmailDPConfiguration>  
         </Configuration>  
         </Extension>  
    </DeliveryUI>  
    ```  
  
3.  Salvare il file di configurazione.  
  
4.  Entro pochi minuti il server di report ricarica il file di configurazione e le nuove impostazioni diventano effettive. È possibile riavviare il servizio del server di report per forzare il caricamento del file di configurazione.  
  
     Il seguente evento viene scritto nel registro eventi di Windows durante la lettura della configurazione.  
  
     **Event ID:** 109  
  
     **Origine:** servizio del server di report di Windows (nome istanza)  
  
     Il file RSReportServer.config è stato modificato  
  
## <a name="sharepoint-mode-report-servers"></a>Server di report in modalità SharePoint  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] La modalità SharePoint archivia le informazioni delle estensioni nei database dell'applicazione del servizio SharePoint e non nel file RsrReportServer.config. In modalità SharePoint, la configurazione delle estensioni per il recapito viene modificata con PowerShell.  
  
#### <a name="configure-the-default-delivery-extension"></a>Configurare l'estensione per il recapito predefinita  
  
1.  Aprire la **shell di gestione di SharePoint**.  
  
2.  È possibile ignorare questo passaggio se si conosce già il nome dell'applicazione del servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Usare le seguenti funzioni PowerShell per elencare le applicazioni del servizio di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nella farm di SharePoint.  
  
    ```  
    get-sprsserviceapplication | format-list *  
    ```  
  
3.  Eseguire la funzione PowerShell seguente per verificare l'estensione per il recapito predefinita corrente per l'applicazione di servizio "ssrsapp" di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    ```  
    $app=get-sprsserviceapplication | where {$_.name -like "ssrsapp*"};Get-SPRSExtension -identity $app | where{$_.ServerDirectivesXML -like "<DefaultDelivery*"} | format-list *  
  
    ```
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Recapito tramite condivisione file in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)   
 [Recapito tramite posta elettronica in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)   
 [Configurare un server di report per il recapito tramite posta elettronica (Gestione configurazione SSRS)](https://msdn.microsoft.com/b838f970-d11a-4239-b164-8d11f4581d83)  
  
<!-- TODO:
The above See Also link to the old MSDN at...
https://msdn.microsoft.com/b838f970-d11a-4239-b164-8d11f4581d83

...is redirected to the following Docs link, for SQL Server 2014...

https://docs.microsoft.com/sql/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager?view=sql-server-2014

...So if I was not presently resolving conflicts with public repo PR, related to private repo PR 7827,
the better fix would be to replace the whole MSDN link with the newer Docs link (to which the older MSDN link is redirected).
Maybe later someone can perform this replacement, and under docs/reporting-services/ there are multiple similar replacement opportunities.
GeneMi , 2018/10/25
-->
