---
title: Aggiungere elementi di Reporting Services ai dashboard di Power BI | Microsoft Docs
ms.date: 09/16/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- pbi
- dashboard
- pin
- powerbi
- power bi integration
ms.assetid: 1d96c3f7-2fd4-40f7-8d1c-14a7f54cdb15
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5d8b28b0799ec5ffac1f00e54cf2305a1027bc35
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50031410"
---
# <a name="pin-reporting-services-items-to-power-bi-dashboards"></a>Aggiungere elementi di Reporting Services ai dashboard di Power BI
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] consente agli utenti di aggiungere elementi del report di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dalla barra degli strumenti di Visualizzatore report a un dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] come nuovo riquadro.   Per aggiungere elementi, l'amministratore deve innanzitutto integrare il server di report con Azure Active Directory e [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
 ![rs_powerbi_icon](../reporting-services/media/ssrs-powerbi-icon.png "rs_powerbi_icon")  
  
 [!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Modalità nativa
  
##  <a name="bkmk_requirements_to_pin"></a> Requisiti per l'aggiunta  
  
-   Il server di report è configurato per l'integrazione di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] . Per altre informazioni, vedere [Power BI Report Server Integration &#40;Configuration Manager&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md). Se il server di report non è stato configurato, il pulsante **Aggiungi al dashboard di Power BI** non verrà visualizzato nella barra degli strumenti.  
  
     ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
-   Aggiungere il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Visualizzatore di report in [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], ad esempio `http://myserver/Reports`.  Non è possibile aggiungere elementi da [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], da Progettazione report in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]o da un URL del server di report.  Ad esempio, `http://myserver/ReportServer`.  
  
-   Il browser deve essere configurato per consentire i popup dal sito del server di report.  
  
-   Se si desidera aggiornare l'elemento aggiunto, i report devono essere configurati per le credenziali archiviate.  Quando si aggiunge un elemento, viene creata automaticamente una sottoscrizione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per gestire l'aggiornamento dei dati dell'elemento nel dashboard.  Se il report non usa le credenziali archiviate, quando viene eseguita la sottoscrizione, verrà visualizzato un messaggio di errore simile al seguente nella pagina **Sottoscrizioni personali** .  
  
        PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credential.
 
    Vedere la sezione "Configurare le credenziali archiviate per un'origine dati specifica del report (modalità nativa)" di [Archiviare le credenziali in un'origine dati di Reporting Services](../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md).  
  
##  <a name="bkmk_supported_items"></a> Elementi che è possibile aggiungere  
 I seguenti elementi del report possono essere aggiunti a un dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  Non è possibile aggiungere elementi annidati all'interno di un'area dati. Ad esempio, non è possibile aggiungere un elemento annidato all'interno di una tabella o un elenco di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Grafici  
  
-   Pannelli dei misuratori  
  
-   Mappe  
  
-   Immagini  
  
-   Gli elementi devono far parte del corpo del report.  Non è possibile aggiungere elementi presenti nell'intestazione o nel piè di pagina.  
  
-   È possibile aggiungere singoli elementi presenti all'interno di un rettangolo di livello superiore, ma non come unico gruppo.  
  
##  <a name="bkmk_to_pin"></a> Per aggiungere un elemento del report  
  
1. Verificare di aver eseguito l'accesso a [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], select the menu item **My Settings** and sign in. Per altre informazioni, vedere  [Impostazioni personali per Integrazione di Power BI &#40;portale Web&#41;](https://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5).

    ![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
2. Passare alla cartella [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] che contiene il report e quindi visualizzare il report.  
  
3. Durante la visualizzazione del report, fare clic sul pulsante **Aggiungi a Power BI** nella barra degli strumenti.  Se non è già stato eseguito l'accesso, verrà richiesto di farlo.  Se il pulsante di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] non è visibile, il server di report non è stato integrato con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Per altre informazioni, vedere [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
    ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
4. Selezionare l'elemento del report che si vuole aggiungere a [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. È possibile aggiungere un solo elemento per volta.  Visualizzatore di report presenta una visualizzazione ombreggiata del report. Gli elementi del report che è possibile aggiungere sono evidenziati, mentre quelli che non è possibile aggiungere sono ombreggiati con un colore scuro.  
  
    **(1)** selezionare il gruppo contenente il dashboard in cui si vuole aggiungere l'elemento, **(2)** selezionare il dashboard a cui si vuole aggiungere l'elemento e **(3)** selezionare la frequenza di aggiornamento del riquadro nel dashboard.   ![nota](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "nota") L'aggiornamento è gestito dalle sottoscrizioni di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e, dopo l'aggiunta dell'elemento, è possibile modificare la sottoscrizione e configurare un'altra pianificazione dell'aggiornamento.  
  
    ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png)  
  
5. Selezionare **Aggiungi**.  
  
    Nella finestra **Elemento aggiunto correttamente** è possibile selezionare il collegamento **Visualizzalo in Power BI** per passare al dashboard e visualizzare l'elemento appena aggiunto.  
  
6. Fare clic su **Chiudi** per tornare alla visualizzazione normale del report.  
  
##  <a name="bkmk_in_the_dashboard"></a> Nel dashboard

Dopo l'aggiunta dell'elemento del report nel dashboard, l'aspetto del riquadro è simile a quello di altri riquadri del dashboard e non è presente alcuna indicazione visibile riguardo la sua provenienza da [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. L'elenco seguente riepiloga in che modo le proprietà del riquadro vengono popolate dall'elemento del report.  
  
Nel dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] l'elemento del report aggiunto si comporta come gli altri riquadri:

**(1)** È possibile aggiungere il riquadro ad altri dashboard.

**(2)** In **Dettagli riquadro** si noterà che il titolo del report di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] viene usato come titolo predefinito del riquadro.

**(3)** Il sottotitolo del riquadro è basato sulla data e sull'ora di aggiunta del riquadro o dell'ultimo aggiornamento dei dati da [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. La pianificazione dell'aggiornamento è gestita dalla sottoscrizione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] creata automaticamente quando l'elemento del report è stato aggiunto.

**(4)** Se si fa clic sul riquadro stesso, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] usare il **(3) collegamento personalizzato** per passare alla pagina di [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] del server di report registrato. Il link è stato impostato quando l'elemento è stato aggiunto da [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Se non si dispone di connettività a Internet per il server di report, verrà visualizzato un errore nel browser.  

![ssrs_pinned_tile_details](../reporting-services/media/ssrs-pinned-tile-details.png "ssrs_pinned_tile_details")  
  
##  <a name="bkmk-troubleshoot"></a> Risolvere eventuali problemi  
  
-   **Nessun pulsante di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] nella barra degli strumenti di Visualizzatore report**: questo indica che il server di report non è stato integrato con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Per altre informazioni, vedere [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
- **Impossibile eseguire l'aggiunta**: quando si tenta di aggiungere un elemento, viene visualizzato il messaggio di errore seguente. Vedere la sezione [Elementi che è possibile aggiungere](#bkmk_supported_items).  
  
      Cannot Pin: There are no report items on this page that you can pin to [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
-   **Gli elementi aggiunti mostrano dati non aggiornati** in un dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] , che non è stato aggiornato per un periodo di tempo.  Il token delle credenziali utente è scaduto ed è necessario eseguire nuovamente l'accesso.  La registrazione delle credenziali utente con Azure e [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] è valida per 90 giorni. In[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]fare clic su **Impostazioni personali**. Per altre informazioni, vedere [Impostazioni personali per Integrazione di Power BI &#40;portale Web&#41;](https://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5).  
  
-   **Gli elementi aggiunti mostrano dati non aggiornati** in un dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] , che non è stato mai aggiornato.  Il problema è che il report non è configurato per usare le credenziali archiviate. Un report deve usare le credenziali archiviate perché l'azione di aggiunta di un elemento del report crea una sottoscrizione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per gestire la pianificazione dell'aggiornamento dei riquadri. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] richiedono credenziali archiviate. Se si esamina la pagina **Sottoscrizioni personali** , viene visualizzato un messaggio di errore simile al seguente:  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified. (rsInvalidDataSourceCredentialSetting)
  
-   **Credenziali di Power BI scadute:**  se si tenta di aggiungere un elemento, viene visualizzato il messaggio di errore seguente. In [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]fare clic su **Impostazioni personali** e, nella pagina Impostazioni personali, fare clic su **Accedi**. Per altre informazioni, vedere  [Impostazioni personali per Integrazione di Power BI &#40;portale Web&#41;](https://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5) .  
  
        Cannot Pin : Unexpected Server Error: Missing, invalid or expired Power BI credentials.  
  
-   **Impossibile eseguire l'aggiunta**: se si tenta di aggiungere un elemento a un dashboard in uno stato di sola lettura, verrà visualizzato un messaggio di errore simile al seguente:  
  
        Server Error : The item 'Dashboard deleted 015cf022-8e2f-462e-88e5-75ab0a04c4d0' cannot be found. (rsItemNotFound)  
  
##  <a name="bkmk_subscription_management"></a> Gestione delle sottoscrizioni  
 Oltre ai problemi relativi alle sottoscrizioni descritti nella sezione sulla risoluzione dei problemi, le informazioni seguenti aiuteranno a mantenere le sottoscrizioni relative a [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .
  
-   **Nome dell'elemento modificato:** se un elemento del report aggiunto viene rinominato o eliminato, il riquadro di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] non verrà più aggiornato e verrà visualizzato un messaggio di errore simile al seguente.  Se si ripristina il nome originale dell'elemento, la sottoscrizione inizierà a funzionare di nuovo e il riquadro verrà aggiornato nella pianificazione delle sottoscrizioni.  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image1, error: Error: Report item 'Image1' cannot be found.  
  
     È inoltre possibile modificare le proprietà della sottoscrizione e cambiare il **nome dell'elemento visivo del report** con il nome dell'elemento del report appropriato. ![modificare la visualizzazione usata per l'aggiornamento di Power BI](../reporting-services/media/ssrs-powerbi-subscription-visual.png "modificare la visualizzazione usata per l'aggiornamento di Power BI")  
  
-   **Eliminare un riquadro**. Se si elimina un riquadro in [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)], la sottoscrizione associata non viene eliminata in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e nella pagina **Sottoscrizioni personali**viene visualizzato un errore simile al seguente. È possibile eliminare la sottoscrizione.  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The item 'Tile deleted af7131d9-5eaf-480f-ba45-943a07d19c9f' cannot be found.  

## <a name="video"></a>Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="see-also"></a>Vedere anche  
 [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Impostazioni personali per Integrazione di Power BI &#40;portale Web&#41;](https://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5)  
 [Dashboard in Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

