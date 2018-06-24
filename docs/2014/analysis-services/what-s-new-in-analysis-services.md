---
title: Novità&#39;s New in Analysis Services e Business Intelligence | Documenti Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 81dc5c82b8b034556ab4eb69c9f9ca377f641c43
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062695"
---
# <a name="what39s-new-in-analysis-services-and-business-intelligence"></a>Novità&#39;s New in Analysis Services e Business Intelligence
  Fatta eccezione per funzionalità aggiunta che supporta i report Power View nei modelli multidimensionali, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] rimane invariata dalla versione precedente.  
  
 Per informazioni su altri [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] prodotti e tecnologie che sono diverse in questa versione, vedere [novità in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
## <a name="updates-to-design-tool-installation"></a>Aggiornamenti all'installazione dello strumento di progettazione  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per Business Intelligence (SSDT-BI), precedentemente noto come Business Intelligence Development Studio (BIDS), viene utilizzato per creare i modelli di Analysis Services, i report di Reporting Services e i pacchetti di Integration Services. È possibile scaricare SSDT-BI dai percorsi seguenti:  
  
-   [Scaricare SSDT-BI per Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Scaricare SSDT-BI per Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Se si dispone di una versione precedente di SSDT-BI o BIDS installata nel computer, la versione più recente viene installata side-by-side alla versione precedente. La versione più recente e quella precedente degli strumenti di progettazione vengono in genere eseguite su una sola workstation in modo da poter modificare progetti e soluzioni legati a versioni specifiche del server.  
  
> [!NOTE]  
>  Sono disponibili vari siti di download per le versioni di SSDT di Visual Studio 2012 e Visual Studio 2013. La maggior parte non include i modelli di progetto BI. Tramite i collegamenti sopra indicati è possibile scaricare la versione corretta. Se la versione di SSDT-BI è quella corretta, viene visualizzata la cartella dei modelli di progetto Business Intelligence. Questa cartella contiene i modelli di progetto per Analysis Services, Reporting Services e Integration Services. A seconda della modalità di installazione di SSDT-BI, potrebbe essere visualizzato anche un modello di progetto aggiuntivo per i database di SQL Server.  
  
 ![Nuovi modelli di progetto in SSDT](media/ssdt-biprojects.png "Nuovi modelli di progetto in SSDT")  
  
## <a name="features-recently-added-power-view-for-multidimensional-models"></a>Funzionalità recentemente aggiunte: Power View per i modelli multidimensionali  
 La possibilità di creare report Power View nei modelli multidimensionali è stata introdotta per la prima volta nell'aggiornamento cumulativo 4 di [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1. La funzionalità Power View per i modelli multidimensionali è ora incluso in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
 **Report Power View per un modello multidimensionale**  
  
 ![Report Power View](media/powerviewreport-wn.gif "Report Power View")  
  
 Questa funzionalità consente alle organizzazioni di ottimizzare gli investimenti esistenti di business intelligence permettendo di utilizzare i modelli multidimensionali (anche noti come cubi OLAP) con i più recenti strumenti client per la creazione di report. A seconda dei tipi di dati contenuti in un modello multidimensionale, gli utenti possono creare facilmente varie visualizzazioni dinamiche dalle tabelle e dalle matrici, ai grafici a bolle, alle mappe geografiche. I modelli multidimensionali ora supportano anche le query che utilizzano Data Analysis Expressions (DAX).  
  
 Power View per modelli multidimensionali richiede la funzionalità di creazione di report Power View incorporata in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (in modalità SharePoint). Altre versioni di Power View, in particolare il componente aggiuntivo di Power View in Excel 2013, non supportano i modelli multidimensionali.  
  
 Per altre informazioni, vedere [Power View per modelli multidimensionali](http://msdn.microsoft.com/library/dn140246.aspx).  
  
  