---
title: 'Aggiornamento: documentazione di SSDT per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione di SQL Server Data Tools (SSDT) per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: ssdt
ms.date: 02/03/2018
ms.openlocfilehash: c591ddddd60af31fe2d338fdee25ea2c17ab0ea5
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Articoli nuovi e aggiornati di recente: SQL Server Data Tools (SSDT)



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


***Nessun nuovo articolo da visualizzare.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Log delle modifiche per SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp;[Log delle modifiche per SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Aggiornamento: 18/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6416949beaee91da2f77dfebb9eb5ed363db4cb7 de18314845cffa197b3fd2ed868f2c330760bedb  (PR=4652  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**SSDT per Visual Studio 2017 (15.5.1)**

Numero di build: 14.0.16148.0

**Novità**


Visual Studio 2017 (15.5.1) è uguale alla versione 15.5.0 tranne che per le correzioni di bug seguenti apportate al programma di installazione:

1.  Risolvere il problema per cui il programma di installazione si blocca dopo l'installazione di SQL Server Integration Services.
2.  Risolvere il problema per cui l'installazione non riesce e viene visualizzato il messaggio di errore seguente: "L'operazione metafile richiesta non è supportata (0x800707D3)".

A parte queste due correzioni di bug, i dettagli seguenti per la versione 15.5.0 si applicano anche alla versione 15.5.1

**SSDT per Visual Studio 2017 (15.5.0)**

Numero di build: 14.0.16146.0

**Novità**


SSDT per Visual Studio 2017 (15.5.0) passa dalla versione di anteprima alla disponibilità generale.

**Programma di installazione**
1. L'interfaccia utente del programma di installazione è localizzata.
1. L'icona è stata sostituita con una versione di qualità superiore.

**Integration Services (IS)**
1. È stato aggiunto un passaggio di convalida del pacchetto nella distribuzione guidata durante la distribuzione nel runtime di integrazione di Azure SSIS nel file di definizione dell'applicazione (ADF), che consente di individuare potenziali problemi di compatibilità nei pacchetti SSIS per l'esecuzione nel runtime di integrazione di Azure SSIS. Per altre informazioni, vedere [Convalidare pacchetti SSIS distribuiti in Azure](..\integration-services\lift-shift\ssis-azure-validate-packages.md).
1. L'estensione SSIS è localizzata.

**Correzioni di bug**


**Integration Services (IS)**
1. È stato risolto un problema per cui il layout della gestione connessione OLEDB e ADO.NET risultava danneggiata.
2. È stato risolto un problema per cui veniva generato un errore di assembly non trovato durante il tentativo di modifica di un'attività di elaborazione della dimensione.

**Problemi noti**


**Integration Services (SSIS)** L'attività di esecuzione dei pacchetti SSIS non supporta il debug quando l'elemento ExecuteOutOfProcess è impostato su True. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.



**SSDT 17.4 per Visual Studio 2015**

Numero di build: 14.0.61712.050

**Novità**


**Progetti Analysis Services (SSAS)**
- Sono state aggiunte tre nuove opzioni per progetti tabulari in Opzioni > Analysis Services Tabular > Importazione dati:







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


