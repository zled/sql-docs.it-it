---
title: 'Aggiornamento: documentazione di SSMS per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione di SQL Server Management Studio (SSMS) per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 02/03/2018
ms.openlocfilehash: d69c32f2159c133d7c8042359b7d65885aac39d3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Articoli nuovi e aggiornati di recente: SQL Server Management Studio (SSMS) per SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Installare versioni in lingua non inglese di SQL Server Management Studio (SSMS)](install-other-languages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Scaricare SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [SQL Server Management Studio: log delle modifiche (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Scaricare SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Aggiornamento: 18/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0e123e7bdf04f02fcd26ac31fa30ed5f31b19c7d 924246b55d3cad6a5d068da8a41f4be23dcfeb2b  (PR=4652  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



SSMS 17.4 è la versione più recente di SQL Server Management Studio. La generazione 17.x offre il supporto per quasi tutte le aree di funzionalità da SQL Server 2008 fino a SQL Server 2017. La versione 17.x supporta anche SQL Analysis Services PaaS.

La versione 17.4 include:

Valutazione della vulnerabilità:
- Aggiunta di un nuovo servizio di valutazione della vulnerabilità SQL per l'analisi dei database per rilevare eventuali vulnerabilità e deviazioni dalle procedure consigliate, ad esempio configurazioni errate, autorizzazioni eccessive ed esposizione di dati sensibili.
- I risultati della valutazione includono le azioni applicabili per risolvere ogni problema, oltre a script di correzione personalizzati, ove applicabile. I report di valutazione possono essere personalizzati per ogni ambiente e adattati a specifici requisiti. Per altre informazioni, vedere [Valutazione della vulnerabilità SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Risoluzione del problema per cui *HasMemoryOptimizedObjects* genera un'eccezione in Azure.
- Aggiunta del supporto per la funzionalità CATALOG_COLLATION.

Dashboard Always On:
- Miglioramenti dell'analisi della latenza nei gruppi di disponibilità.
- Aggiunta di due nuovi report: *AlwaysOn\_Latency\_Primary* e *AlwaysOn\_Latency\_Secondary*.

Showplan:
- Aggiornamento dei collegamenti che ora puntano alla documentazione corretta.
- Possibilità di eseguire l'analisi di un singolo piano direttamente dal piano effettivo generato.
- Nuovo set di icone.
- Aggiunta del supporto per riconoscere l'applicazione di operatori logici, ad esempio GbApply e InnerApply.

Profiler XE:
- Rinominato in Profiler XEvent.
- I comandi di menu Arresta/Avvia ora arrestano/avviano la sessione per impostazione predefinita.
- Abilitazione dei tasti di scelta rapida (ad esempio, CTRL+F per la ricerca).
- Aggiunta delle azioni database\_name e client\_hostname agli eventi appropriati nelle sessioni di Profiler XEvent. Per applicare la modifica, potrebbe essere necessario eliminare le istanze della sessione QuickSessionStandard o QuickSessionTSQL sui server - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>2. &nbsp; [SQL Server Management Studio: log delle modifiche (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Aggiornamento: 29/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5096fa8f1ae3f2e4bc040f43cb8810d96f2c69c eb641ac39386a26a76dc303f5bd55eb3f9f4c78d  (PR=0  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=ba4b1c2e5200f2f78786b710da18fd38fedde6c9) -->



**[SSMS 17.4](download-sql-server-management-studio-ssms.md)**

Disponibile a livello generale | Numero di build: 14.0.17213.0

**Novità**


**SQL Server Management Studio (SSMS) - Generale**

Valutazione della vulnerabilità:
- Aggiunta di un nuovo servizio di valutazione della vulnerabilità SQL per l'analisi dei database per rilevare eventuali vulnerabilità e deviazioni dalle procedure consigliate, ad esempio configurazioni errate, autorizzazioni eccessive ed esposizione di dati sensibili.
- I risultati della valutazione includono le azioni applicabili per risolvere ogni problema, oltre a script di correzione personalizzati, ove applicabile. I report di valutazione possono essere personalizzati per ogni ambiente e adattati a specifici requisiti. Per altre informazioni, vedere [Valutazione della vulnerabilità SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Risoluzione del problema per cui *HasMemoryOptimizedObjects* genera un'eccezione in Azure.
- Aggiunta del supporto per la funzionalità CATALOG_COLLATION.

Dashboard Always On:
- Miglioramenti dell'analisi della latenza nei gruppi di disponibilità.
- Aggiunta di due nuovi report: *AlwaysOn\_Latency\_Primary* e *AlwaysOn\_Latency\_Secondary*.

Showplan:
- Aggiornamento dei collegamenti che ora puntano alla documentazione corretta.
- Possibilità di eseguire l'analisi di un singolo piano direttamente dal piano effettivo generato.
- Nuovo set di icone.
- Aggiunta del supporto per riconoscere l'applicazione di operatori logici, ad esempio GbApply e InnerApply.

Profiler XE:
- Rinominato in Profiler XEvent.
- I comandi di menu Arresta/Avvia ora arrestano/avviano la sessione per impostazione predefinita.
- Abilitazione dei tasti di scelta rapida (ad esempio, CTRL+F per la ricerca).
- Aggiunta delle azioni database\_name e client\_hostname agli eventi appropriati nelle sessioni di Profiler XEvent. Per applicare la modifica, potrebbe essere necessario eliminare le istanze della sessione QuickSessionStandard o QuickSessionTSQL sui server - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

Riga di comando:
- Aggiunta di una nuova opzione della riga di comando ("-G") che può essere usata per la connessione automatica di SSMS a un server/database usando l'autenticazione di Active Directory (integrata o della password). Per altre informazioni, vedere [Utilità Ssms](ssms-utility.md).







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (1+3):&nbsp; documentazione di **Advanced Analytics per SQL** ](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **piattaforma di strumenti analitici per SQL** ](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **connessione a SQL Server** ](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione del **motore di database di SQL Server** ](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12+1): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6+2):&nbsp; documentazione di **Linux per SQL Server** ](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15+0): **documentazione di** PowerShell per SQL Server](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (2+9):&nbsp; documentazione dei **database relazionali per SQL Server** ](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (1+0):&nbsp; documentazione di **SQL Server Reporting Services** ](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **SQL Operations Studio** ](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **Microsoft SQL Server** ](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione di **SQL Server Data Tools (SSDT)** ](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+2):&nbsp; documentazione di **SQL Server Management Studio (SSMS)** ](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di **Transact-SQL** ](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


