---
title: Visualizzare report di Reporting Services sui dispositivi di Microsoft Surface e Apple iOS | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
caps.latest.revision: 21
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 2766644db67f3f677060c90a2addd2123276f1e0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167009"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Visualizzare i report Reporting Services su dispositivi Microsoft Surface e Apple iOS
  In questo articolo vengono descritti i flussi di lavoro e le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supportati per i dispositivi di Microsoft Surface e i dispositivi con Apple iOS 6 e Apple Safari come l'iPad.  
  
## <a name="view-and-interact-with-reports"></a>Visualizzare e interagire con i report  
 A partire da [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supporta la visualizzazione e base l'interattività dei report nei dispositivi di Microsoft Surface e i dispositivi con Apple iOS 6 e il browser Apple Safari come l'iPad. Inoltre, è possibile pubblicare i report utilizzando i dispositivi di Microsoft Surface.  
  
 ![Desktop IPad](media/videothumbnail.jpg "Desktop IPad")  
Esaminare una dimostrazione per la visualizzazione dei report in un iPad.  
  
 I report di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] possono essere visualizzati anche in un dispositivo Windows Phone 8.  
  
 Per utilizzare le funzionalità descritte in questo argomento, installare uno degli elementi seguenti:  
  
-   Per un server di report in modalità nativa, installare [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] o versioni successive.  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] è disponibile per il download il [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=35575).  
  
-   Per un server di report in modalità SharePoint, installare [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] o versione successiva del [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aggiuntivo per prodotti SharePoint.  
  
 **Per visualizzare e interagire con un report in un dispositivo iPad o Microsoft Surface**  
  
1.  Verificare che sia possibile connettersi al server di report oppure al sito di SharePoint in cui si trova il report.  
  
2.  Aprire il report effettuando una delle operazioni seguenti.  
  
    -   **Avvio dalla posta elettronica:** un messaggio di posta elettronica creato da un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sottoscrizione, toccare l'URL del report. Il report verrà aperto nel browser.  
  
    -   **Avviare dal Server di Report:** passare alla directory nel [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] server di report e quindi toccare il nome del report per aprire il report.  
  
    -   **Avvio da una raccolta documenti di SharePoint:** passare a una raccolta documenti di SharePoint contenente [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report e quindi toccare il nome del report. È possibile visualizzare e interagire con il report.  
  
        > [!IMPORTANT]  
        >  Per l'iPad, verificare che la proprietà relativa all'esplorazione privata per Safari sia disabilitata **.**  
  
    -   **Web part di SharePoint:** se la web part è stata aggiunta a una pagina di SharePoint, è possibile visualizzare [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report.  
  
3.  Sul dispositivo Microsoft Surface è inoltre possibile aprire il report utilizzando Gestione report. Passare alla directory in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] gestione Report e quindi toccare il nome del report per aprire il report.  
  
    > [!IMPORTANT]  
    >  La visualizzazione dei report in Gestione report non è supportata su un iPad.  
  
4.  Scorrere e fare zoom avanti effettuando le operazioni seguenti  
  
    -   Per scorrere il report, trascinare il dito sullo schermo (verso l'alto, verso il basso, a sinistra o a destra). Si tratta del gesto di spostamento rapido con un dito.  
  
    -   Per fare zoom avanti, posizionare due dita sullo schermo e allontanarle. Per fare zoom indietro, posizionare due dita sullo schermo e spostarle insieme. Si tratta del movimento zoom indietro.  
  
5.  Esplorare e interagire con il report effettuando le operazioni seguenti.  
  
    -   Comprimere ed espandere gli elementi del report, nonché le righe e le colonne associate ai gruppi, toccando il segno più (+) per comprimere e il segno meno (-) per espandere.  
  
    -   Toccare il pulsante di ordinamento per passare dall'ordine crescente a quello decrescente e viceversa per le righe di una tabella o per le righe e le colonne di una matrice. Il pulsante di ordinamento in genere si trova nell'intestazione della colonna.  
  
    -   Espandere e comprimere il riquadro dei parametri, toccando il pulsante freccia nella parte superiore del report.  
  
    -   Selezionare un valore di parametro toccando la casella o il controllo accanto al parametro. Toccare **Visualizza report** per applicare il valore del parametro al report.  
  
    -   Per eseguire ricerche nel contenuto del report toccare la casella accanto a **Trova**, digitando un termine di ricerca e toccando **Trova**.  
  
    -   Esplorare le pagine del report toccando i pulsanti di navigazione o la casella di testo accanto ai pulsanti e digitando il numero di pagina.  
  
    -   Passare agli URL toccando i collegamenti ipertestuali aggiunti agli elementi del report, ad esempio caselle di testo, immagini, grafici e misuratori.  
  
    -   Esportare il report toccando l'icona di **Menu a discesa Esporta** e, successivamente, un formato di file.  
  
        -   Se il report viene visualizzato su un dispositivo di Microsoft Surface, è possibile esportarlo in uno dei formati riportati di seguito.  
  
            -   File XML con dati del report  
  
            -   CSV (delimitato da virgole)  
  
            -   PDF  
  
            -   MHTML (archivio Web)  
  
            -   Excel  
  
            -   TIFF  
  
            -   Word  
  
        -   Se il report viene visualizzato su un iPad, è possibile esportarlo come file TIFF o PDF.  
  
## <a name="authentication"></a>Autenticazione  
 Autenticazione RSWindowsNTLM e RSWindowsBasic operare [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità nativa e iPad.  
  
 In genere, è consigliabile non utilizzare RSWindowsBasic in ambienti non https, poiché questo tipo di autenticazione non offre riservatezza per le credenziali trasmesse.  
  
 Per ulteriori informazioni sull'autenticazione RSWindowsNTLM e RSWindowsBasic, vedere [l'autenticazione con il Server di Report](security/authentication-with-the-report-server.md).  
  
## <a name="uploading-reports"></a>Caricamento di report  
 È possibile pubblicare i report da un dispositivo di Microsoft Surface utilizzando uno dei metodi seguenti, se si dispone delle autorizzazioni appropriate.  
  
> [!IMPORTANT]  
>  Questi metodi non sono supportati sull'iPad.  
  
-   Caricare un file di definizione del report (con estensione rdl) in una raccolta documenti di SharePoint aprendo e toccando **Carica documento**.  
  
-   Caricare un file di definizione del report nel database del server di report aprendo Gestione report e toccando **Carica file**.  
  
## <a name="additional-information"></a>Informazioni aggiuntive  
 Per ulteriori informazioni su [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e sui browser supportati, vedere:  
  
-   [Pianificazione per Reporting Services e supporto Browser per Power View &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Per ulteriori informazioni su Microsoft Business Intelligence e sui dispositivi mobili, vedere gli argomenti seguenti:  
  
-   [Panoramica dei dispositivi mobili e SharePoint 2013](http://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (http://technet.microsoft.com/library/fp161351(v=office.15).aspx).  
  
-   [Browser per dispositivi mobili supportati in SharePoint 2013](http://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (http://technet.microsoft.com/library/fp161353(v=office.15).aspx).  
  
-   [Visualizzazione di report e scorecard in dispositivi Apple iPad (SharePoint Server 2010)](http://technet.microsoft.com/library/hh697482.aspx) (http://technet.microsoft.com/library/hh697482.aspx).  
  
-   [Visualizzazione di report di Reporting Services in un iPad (video)](http://technet.microsoft.com/sqlserver/jj873792.aspx) (http://technet.microsoft.com/sqlserver/jj873792.aspx).  
  
-   [Visualizzazione dei report di Reporting Services in un dispositivo RT Microsoft Surface (video)](http://technet.microsoft.com/sqlserver/dn146017)  
  
  