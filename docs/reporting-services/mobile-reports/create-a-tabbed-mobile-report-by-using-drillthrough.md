---
title: Creare un report per dispositivi mobili a schede tramite il drill-through | Report di Reporting Services per dispositivi mobili | Documenti Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6554f808c19540d2a3b7cbe3fdf4e86c5fe7a357
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-tabbed-mobile-report-by-using-drillthrough"></a>Creare un report per dispositivi mobili a schede tramite il drill-through
Informazioni su come creare un report per dispositivi mobili di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] analogo a un report a schede in termini di aspetto e funzionamento usando il drill-through e parametri.

In questo report, ad esempio, i misuratori nella parte superiore si comportano come le schede. Quando si sceglie il misuratore relativo ai trasporti, i dati nella parte restante del grafico vengono filtrati in base ai dati dei trasporti.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/tabbed-mobile-report-web-viewer-transportation-complete.png)

In realtà si tratta di un set di cinque report separati, ognuno con un parametro diverso che filtra il report in modo che corrisponda al misuratore selezionato nella parte superiore del report. Si crea innanzitutto tutti i cinque report, quindi per ognuno dei cinque report, rendere le altri quattro misuratori drillthroughs quattro report.

Ecco i passaggi per questo esempio.

## <a name="create-the-basic-report"></a>Creare report di base

1. Creare un report denominato Sales con cinque misuratori:

    * Sales
    * Trasporti
    * Carburante
    * Archiviazione
    * Spese varie

   ![01-vendite-Mobile-Report-server di pubblicazione](../../reporting-services/mobile-reports/media/01-sales-mobile-report-publisher.png)
    
2. Impostare **accento** a **su** per il misuratore di vendite, pertanto confronteranno con l'il resto del report, ma in questo caso, bianco su sfondo nero.

    ![01a-Sales-Accent-mobile-report-Publisher](../../reporting-services/mobile-reports/media/01a-sales-accent-mobile-report-publisher.png)
    
3. Salvare in un [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] server di report.

## <a name="make-copies-of-the-report"></a>Creare copie del report

1. Quattro copie del report di vendite e assegnare loro un nome: 

    * Trasporti
    * Carburante
    * Archiviazione
    * Spese varie

3. Per salvare il [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] server di report.

## <a name="set-the-gauge-as-a-drillthrough"></a>Impostare il misuratore come un drill-through

In questa sezione, impostare ogni misuratore (ad eccezione del misuratore Sales) come un drill-through per il report corrispondente.

1. Nel report delle vendite, selezionare il misuratore di trasporto.

    ![02-Sales-create-Drillthrough-mobile-report-Publisher](../../reporting-services/mobile-reports/media/02-sales-create-drillthrough-mobile-report-publisher.png)

2. Con il **Layout** selezionata, nella scheda il **proprietà visive** riquadro selezionare **destinazione drill-through**.

3. Selezionare **report per dispositivi mobili**.

4. Individuare e selezionare il report che sarà la destinazione per il drill-through, in questo caso, "Financials - trasporto".

    ![03-Sales-Select-dashboard-mobile-report-Publisher](../../reporting-services/mobile-reports/media/03-sales-select-dashboard-mobile-report-publisher.png)

5. In **configurare i report di destinazione**, selezionare il parametro per filtrare il report e selezionare **applica**.

   ![04-Sales-Apply-Parameters-mobile-report-Publisher](../../reporting-services/mobile-reports/media/04-sales-apply-parameters-mobile-report-publisher.png)
   
6. Ripetere questi passaggi per ognuna delle altri misuratori del report di vendite. 

## <a name="set-the-gauges-for-the-other-reports"></a>Impostare i misuratori per gli altri report

1.  Aprire il report di trasporto, impostare il misuratore Sales come un drill-through per il report di vendite e gli altri tre misuratori come drillthroughs ai rispettivi report.

2. Ancora nel rapporto di trasporto, impostare **accento** del misuratore di trasporto per **su**, si differenzia il resto del report.

3. Ripetere questi passaggi per i report di carburante, archiviazione e le spese varie. 

## <a name="view-the-report-in-the-web-portal"></a>Visualizzare il report nel portale web

1. Passare al [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] server di report e aprire uno dei report. 

2. Si noti che ogni i misuratori è associata un'icona di drill-through nell'angolo superiore destro.

    ![Web-Viewer-drillthrough-icon-mobile-report-builder](../../reporting-services/mobile-reports/media/web-viewer-drillthrough-icon-mobile-report-builder.png)

3. Selezionare uno dei misuratori per passare al report filtrato in base ai dati che del misuratore.

   ![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

### <a name="see-also"></a>Vedere anche
    
* [Aggiungere parametri a un report per dispositivi mobili](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)
* [Aggiungere il drill-through da un report per dispositivi mobili ad altri report per dispositivi mobili o URL](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)




  


