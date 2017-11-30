---
title: Web part Visualizzatore di report in un sito di SharePoint | Microsoft Docs
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
ms.openlocfilehash: dfb4ace4c673bf32bc9ecba6bed58c1d379221e3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>Web part Visualizzatore di report in un sito di SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

La web part Visualizzatore di report è una web part personalizzata. La web part può essere usata per visualizzare, stampare ed esportare report in un server di report all'interno di un sito di SharePoint. La web part Visualizzatore di report è associata ai file di definizione dei report (con estensione rdl) elaborati da un server di report di Microsoft SQL Server Reporting Services. 

La web part Visualizzatore di report più recente può essere usata anche per i report impaginati distribuiti al server di report di Power BI. La web part non funziona con i report di Power BI.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Perché è stata reintrodotta la web part Visualizzatore di report

La web part Visualizzatore di report era disponibile come parte del componente aggiuntivo Reporting Services per prodotti SharePoint. La web part era specifica per i server di report in modalità integrata SharePoint. La modalità integrata SharePoint è stata deprecata dopo il rilascio di SQL Server 2016.

A partire da SQL Server 2017, è disponibile una sola modalità di installazione per Reporting Services: la **modalità nativa**. È possibile incorporare tutti i tipi di report usando una web part Visualizzatore pagine che usa il parametro URL *rs:Embed=true*. Incorporare report nelle pagine di SharePoint è una sequenza di integrazione richiesta dai clienti e la web part Visualizzatore di report aggiornata abilita questo scenario per i report impaginati.

Mentre la web part Visualizzatore pagine è sufficiente per incorporare un report impaginato in una pagina di SharePoint, la web part Visualizzatore di report aggiornata offre funzionalità aggiuntive.

* Visualizzare o nascondere pulsanti della barra degli strumenti specifici
* Sostituire valori di parametri dei report
* Connettere le web part Filtro ai parametri del report

## <a name="download-the-report-viewer-web-part-solution-package"></a>Scaricare il pacchetto della soluzione web part Visualizzatore di report

La web part Visualizzatore di report è disponibile nell'Area download Microsoft.

[Scaricare il pacchetto della soluzione web part Visualizzatore di report](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

Gli elementi elencati sono specifici della web part Visualizzatore di report aggiornata.

* La web part può essere usata solo nelle pagine di SharePoint *classiche*.
* Solo i report (RDL) impaginati sono supportati per l'incorporamento nella web part Visualizzatore di report. Per incorporare report di Power BI o report per dispositivi mobili, è possibile usare il parametro URL *rs:Embed=true*.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare la web part Visualizzatore di report aggiornata, vedere [Distribuire la web part Visualizzatore di report in un sito di SharePoint](deploy-report-viewer-web-part.md).
