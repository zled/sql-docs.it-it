---
title: Scaricare SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: 4bcceaeca15c3fa20cd797bda0182cf48f73a730
ms.contentlocale: it-it
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Scaricare SQL Server Data Tools (SSDT)

**[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)** è un moderno strumento di sviluppo scaricabile gratuitamente per compilare database relazionali SQL Server, database Azure SQL, pacchetti di Integration Services, modelli di dati di Analysis Services e report di Reporting Services. Con SSDT è possibile progettare e distribuire qualsiasi tipo di contenuto SQL Server con la stessa facilità con la quale si sviluppa un'applicazione in Visual Studio. Questa versione supporta da SQL Server 2017 a SQL Server 2005 e include l'ambiente di progettazione per l'aggiunta di funzionalità nuove in SQL Server.  
    
    
![Download](../ssdt/media/download.png) [Scaricare SQL Server Data Tools 17.2 per Visual Studio 2015](https://go.microsoft.com/fwlink/?linkid=852922)

![Download](../ssdt/media/download.png) [Scaricare Data-Tier Application Framework (DacFx) 17.2](https://www.microsoft.com/download/details.aspx?id=55713)

## <a name="sql-server-data-tools"></a>SQL Server Data Tools   
**Informazioni sulla versione**  
  
Numero di versione: 17.2  
Numero di build per questa versione: 14.0.61707.300
  
**Novità**

**Analysis Services**

- Ora è possibile configurare la sicurezza a livello di oggetto nella finestra di dialogo Ruoli per la sicurezza avanzata nei modelli tabulari con livello di compatibilità 1400.
- Nuova selezione di membri del ruolo AAD per gli utenti senza indirizzi di posta elettronica nei modelli di Azure Analysis Services nei progetti SSDT Analysis Services per Visual Studio 2017.
- Nuova proprietà del progetto "Chiedi sempre conferma" di Azure Analysis Services nei progetti tabulari di SSDT Analysis Services per personalizzare il comportamento di memorizzazione nella cache delle credenziali ADAL.


**Problemi noti**

- Per un elenco completo delle modifiche, vedere il [log delle modifiche](changelog-for-sql-server-data-tools-ssdt.md).
- Per segnalare eventuali problemi, è possibile usare il [Centro commenti e suggerimenti per SSDT Connect](https://connect.microsoft.com/SQLServer/Feedback).

> [!NOTE]
> Per usare SQL Server Data Tools in Visual Studio 2017 vedere [questa](#use-ssdt-in-visual-studio-2017) sezione di seguito

  **Lingue disponibili**  
  
 Questa versione di SSDT può essere installata nelle lingue seguenti:  
[Cinese (Repubblica popolare cinese)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x804) | 
[Cinese (Taiwan)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x404) | 
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x409) | 
[Francese]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x407) | 
[Italiano]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x410) | 
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x411) | 
[Coreano]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x412) | 
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x416) | 
[Russo]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x419) | 
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40a)  

**Immagini ISO**

Un'immagine ISO di SSDT può essere utilizzata come metodo alternativo per installare SSDT o configurare un punto di installazione amministrativa. L'immagine ISO è un file autonomo che contiene tutti i componenti richiesti da SSDT e può essere scaricata mediante un gestore download riavviabile, utile nei casi di larghezza di banda della rete limitata o meno affidabile. Una volta scaricata, l'immagine ISO può essere montata come unità o masterizzata su un DVD.

[Cinese (Repubblica popolare cinese)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x804) |
[Cinese (Taiwan)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x404) |
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x409) |
[Francese]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x407) |
[Italiano]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x410) |
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x411) |
[Coreano]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x412) |
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x416) |
[Russo]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x419) |
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40a)

## <a name="download-visual-studio"></a>Scaricare Visual Studio

* [**Scaricare Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Installazione di SSDT senza Visual Studio preinstallato

Se Visual Studio non è installato nel computer, l'installazione di SSDT per Visual Studio 2015 includerà anche l'installazione di una versione minima "shell integrata" di Visual Studio 2015. Questa versione di Visual Studio può essere installata e usata liberamente in qualsiasi numero di computer. Include tutti i tipi di progetto di SQL Server, oltre a Esplora oggetti di SQL Server e altre esperienze di strumenti SQL.

Se nel computer in uso è installato [Visual Studio 2015 Community Edition (o versioni successive)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx), l'installazione di SSDT consentirà di aggiungere il set completo di strumenti di SQL Server nell'installazione di Visual Studio esistente. Visual Studio include molte funzionalità utili, come l'integrazione del controllo del codice sorgente e il supporto di linguaggi diversi da SQL. Per un'esperienza di sviluppo ottimale con T-SQL, è consigliabile usare Visual Studio Community 2015 o versione successiva.

## <a name="supported-sql-versions"></a>Versioni di SQL supportate
  
|Modelli di progetto|Piattaforme SQL supportate|  
|-------------------|--------------------|  
Database relazionali|  SQL Server 2005* - SQL Server 2017 <br /><br />Database SQL di Azure<br /><br />Azure SQL Data Warehouse (supporta solo query, i progetti di database non sono ancora supportati)<br /><br />  * Il supporto per SQL Server 2005 è deprecato<br /><br /> e si consiglia di passare a una versione di SQL supportata ufficialmente|
  |Modelli di Analysis Services<br /><br />Report di Reporting Services | SQL Server 2008 - SQL Server 2017|
  |pacchetti di Integration Services| SQL Server 2012 - SQL Server 2017    |
  
## <a name="next-steps"></a>Passaggi successivi  
Dopo l'installazione di SSDT, consultare queste esercitazioni per imparare a creare database, pacchetti, modelli di dati e report mediante SSDT:  
  
-   [Sviluppo di database offline orientato ai progetti](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Esercitazione SSIS: Creare un pacchetto ETL semplice](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Esercitazioni su Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Creare un report tabella semplice (esercitazione su SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="use-ssdt-in-visual-studio-2017"></a>Usare SSDT in Visual Studio 2017 

* [**Scaricare Visual Studio 2017**](https://www.visualstudio.com/) ([confrontare le funzionalità di Visual Studio 2017 nelle varie edizioni](https://www.visualstudio.com/vs/compare/))

Per usare progetti di database relazionali, è consigliabile controllare il carico di lavoro **Elaborazione ed archiviazione dati** durante l'installazione. Il supporto per progetti di database SSDT è incluso anche in altri carichi di lavoro, tra cui *Azure*, *Sviluppo Web e ASP.NET* e *Sviluppo multipiattaforma .NET Core*.

> [!NOTE]
> I progetti di database SSDT in Visual Studio 2017 supportano attualmente fino a SQL Server 2016.  Il supporto per SQL Server 2017 sarà presto disponibile in un aggiornamento di Visual Studio 2017.

Se si usa SSDT con Visual Studio 2017, installare i componenti AS e RS:
* [Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)
* [Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


## <a name="see-also"></a>Vedere anche  
[SQL Server Data Tools in Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog del Team di SSDT](http://blogs.msdn.com/b/ssdt/)  
[Commenti SSDT Connect](https://connect.microsoft.com/SQLServer/Feedback)  
[Documentazione di SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

