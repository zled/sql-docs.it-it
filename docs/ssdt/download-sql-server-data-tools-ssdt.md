---
title: Scaricare SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installare ssdt, scaricare ssdt, versione più recente di ssdt"
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 681ad2f6d7aeb88db45dde3f2e695db672b97dbd
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Scaricare SQL Server Data Tools (SSDT)

**[SQL Server Data Tools](https://msdn.microsoft.com/mt186501)** è un moderno strumento di sviluppo scaricabile gratuitamente per compilare database relazionali SQL Server, database Azure SQL, pacchetti di Integration Services, modelli di dati di Analysis Services e report di Reporting Services. Con SSDT è possibile progettare e distribuire qualsiasi tipo di contenuto SQL Server con la stessa facilità con la quale si sviluppa un'applicazione in Visual Studio. Questa versione supporta SQL Server 2016 tramite SQL Server 2005 e fornisce l'ambiente di progettazione per l'aggiunta delle funzionalità introdotte in SQL Server 2016.  
    
    
| ![download](../ssdt/media/download.png) Scaricare SQL Server Data Tools per Visual Studio 2015  | Download del framework applicazione livello dati (DacFx) ||
|:---|:---|:---|
|**[Scaricare SQL Server Data Tools (16.5)](https://msdn.microsoft.com/mt186501)**|[**Scaricare DacFx e SqlPackage.exe (16.5)**](https://www.microsoft.com/download/details.aspx?id=54106) |Versione di disponibilità generale corrente per l'uso in un ambiente di produzione.|
|[**Scaricare SQL Server Data Tools (versione finale candidata)**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md)| [**Scaricare DacFx e SqlPackage.exe (versione finale candidata)**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md) |Include il supporto per SQL Server vNext.|



## <a name="download-visual-studio"></a>Scaricare Visual Studio

* [**Scaricare Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

### <a name="use-ssdt-in-visual-studio-2017"></a>Usare SSDT in Visual Studio 2017

* [**Scaricare Visual Studio 2017**](https://www.visualstudio.com/) ([confrontare le funzionalità di Visual Studio 2017 nelle varie edizioni](https://www.visualstudio.com/vs/compare/))

Per usare progetti di database relazionali, è consigliabile controllare il carico di lavoro **Elaborazione ed archiviazione dati** durante l'installazione. Il supporto per progetti di database SSDT è incluso anche in altri carichi di lavoro, tra cui *Azure*, *Sviluppo Web e ASP.NET* e *Sviluppo multipiattaforma .NET Core*.

Se si usa SSDT con Visual Studio 2017, installare i componenti AS e RS:
* [Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)
* [Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Installazione di SSDT senza Visual Studio preinstallato

Se Visual Studio non è installato nel computer, l'installazione di SSDT per Visual Studio 2015 includerà anche l'installazione di una versione minima "shell integrata" di Visual Studio 2015. Questa versione di Visual Studio può essere installata e usata liberamente in qualsiasi numero di computer. Include tutti i tipi di progetto di SQL Server, oltre a Esplora oggetti di SQL Server e altre esperienze di strumenti SQL.

Se nel computer in uso è installato [Visual Studio 2015 Community Edition (o versioni successive)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx), l'installazione di SSDT consentirà di aggiungere il set completo di strumenti di SQL Server nell'installazione di Visual Studio esistente. Visual Studio include molte funzionalità utili, come l'integrazione del controllo del codice sorgente e il supporto di linguaggi diversi da SQL. Per un'esperienza di sviluppo ottimale con T-SQL, è consigliabile usare Visual Studio Community 2015 o versione successiva.

## <a name="supported-sql-versions"></a>Versioni di SQL supportate
  
|Modelli di progetto|Piattaforme SQL supportate|  
|-------------------|--------------------|  
Database relazionali|  SQL Server 2005* - SQL Server 2016 <br /><br />Database SQL di Azure<br /><br />Azure SQL Data Warehouse (supporta solo query, i progetti di database non sono ancora supportati)<br /><br />  * Il supporto per SQL Server 2005 è deprecato<br /><br /> e si consiglia di passare a una versione di SQL supportata ufficialmente|
  |Modelli di Analysis Services<br /><br />Report di Reporting Services | SQL Server 2008 - SQL Server 2016|
  |pacchetti di Integration Services| SQL Server 2012 - SQL Server 2016    |
  
## <a name="next-steps"></a>Passaggi successivi  
Dopo l'installazione di SSDT, consultare queste esercitazioni per imparare a creare database, pacchetti, modelli di dati e report mediante SSDT:  
  
-   [Sviluppo di database offline orientato ai progetti](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Esercitazione SSIS: Creare un pacchetto ETL semplice](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Esercitazioni su Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Creare un report tabella semplice (esercitazione su SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="see-also"></a>Vedere anche  
[SQL Server Data Tools in Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog del Team di SSDT](http://blogs.msdn.com/b/ssdt/)  
[Commenti SSDT Connect](https://connect.microsoft.com/SQLServer/Feedback)  
[Documentazione di SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

