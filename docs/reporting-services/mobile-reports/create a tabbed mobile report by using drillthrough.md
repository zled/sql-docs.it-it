---
title: "Creare un report per dispositivi mobili a schede usando il drill-through | Report per dispositivi mobili di Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Creare un report per dispositivi mobili a schede usando il drill-through | Report per dispositivi mobili di Reporting Services
Informazioni su come creare un report per dispositivi mobili di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] analogo a un report a schede in termini di aspetto e funzionamento usando il drill-through e parametri.

In questo report, ad esempio, i misuratori nella parte superiore si comportano come le schede. Quando si sceglie il misuratore relativo ai trasporti, i dati nella parte restante del grafico vengono filtrati in base ai dati dei trasporti.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

In realtà si tratta di un set di cinque report separati, ognuno con un parametro diverso che filtra il report in modo che corrisponda al misuratore selezionato nella parte superiore del report. 

Nell'esempio vengono prima creati i cinque report, quindi per ciascuno dei cinque report vengono creati gli altri quattro misuratori nei drill-through agli altri quattro report. 

Di seguito è riportata la struttura generale dei passaggi.

1. Creare un report denominato Sales con cinque misuratori:
     - Sales
     - Trasporti
     - Carburante
     - Archiviazione
     - Spese varie
2. Creare quattro copie del report denominate: 
     - Trasporti
     - Carburante
     - Archiviazione
     - Spese varie
3.  Nel report Vendite impostare ciascuno dei quattro misuratori diversi dal misuratore Vendite come drill-through ai rispettivi report.

4. Sempre nel report Vendite impostare la proprietà Evidenziatore del misuratore Vendite in modo da differenziarla dalla parte rimanente del report.

5.  Nel report Trasporti impostare il misuratore Vendite come un drill-through al report Vendite e gli altri tre misuratori come drill-through ai rispettivi report.

6. Di nuovo, nel report Trasporti impostare la proprietà Evidenziatore del misuratore Trasporti in modo da differenziarla dalla parte rimanente del report.

5. Ripetere l'operazione per i report Carburante, Archiviazione e Spese varie. 







  
