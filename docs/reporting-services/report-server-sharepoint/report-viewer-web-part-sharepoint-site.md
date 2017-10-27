---
title: Report web part del visualizzatore in un sito di SharePoint | Documenti Microsoft
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a37ed5efe7c365c601deb95d9fe761d227e7021e
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>Report web part del visualizzatore in un sito di SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

La web part Visualizzatore Report è una parte web personalizzato. È possibile utilizzare la web part per visualizzare, esplorare, stampare ed esportare report in un server di report all'interno di un sito di SharePoint. La web part Visualizzatore Report è associata a file di definizione (con estensione rdl) del report che vengono elaborati da un server di report di Microsoft SQL Server Reporting Services. 

La web part di Visualizzatore Report più recente può anche i report impaginato servizio distribuiti al Server di Report di Power BI. La web part non funziona con i report di Power BI.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Motivo per cui la web part Visualizzatore Report vengono reinserite

La web part Visualizzatore Report è disponibile come parte del componente aggiuntivo di Reporting Services per prodotti SharePoint. La web part è specifica per i server di report in modalità integrata SharePoint. La modalità integrata SharePoint è stata deprecata dopo SQL Server 2016.

A partire da SQL Server 2017, è solo una modalità di installazione per Reporting Services: **modalità nativa**. È possibile incorporare tutti i tipi di report tramite un visualizzatore pagine web part di *rs: incorporare = true* parametro URL. Incorporare report nelle pagine di SharePoint è una sequenza di integrazione richiesta dai clienti e la web part di Visualizzatore Report aggiornata consente questo scenario per i report impaginati.

Mentre la web part di Visualizzatore pagine è sufficiente per incorporare un report impaginato in una pagina di SharePoint, la web part di Visualizzatore di Report aggiornata offre funzionalità aggiuntive.

* Visualizza o nasconde i pulsanti della barra degli strumenti specifici
* Eseguire l'override di valori dei parametri di report
* La connessione web part di filtro per i parametri del report

## <a name="download-the-report-viewer-web-part-solution-package"></a>Scaricare il pacchetto di soluzione web part di Visualizzatore Report

La web part Visualizzatore Report è disponibile nel Microsoft Download Center.

[Scarica pacchetto della soluzione web part Visualizzatore Report](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

Gli elementi elencati sono specifici per la web part di Visualizzatore di Report aggiornata.

* La web part è utilizzabile solo in *classico* pagine di SharePoint.
* Solo i report (RDL) impaginati sono supportati per l'incorporamento nella web part Visualizzatore Report. Se si desidera utilizzare per incorporare i report di Power BI o report per dispositivi mobili, è possibile utilizzare il *rs: incorporare = true* parametro URL.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a utilizzare la web part di Visualizzatore Report aggiornata, vedere [distribuire la web part di Visualizzatore Report in un sito di SharePoint](deploy-report-viewer-web-part.md).

