---
title: Documentazione aggiornata del motore di database | Microsoft Docs
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione per il motore di database.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.openlocfilehash: dc4a5516662b200b4224facbb4c9cf4588c1b42e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="new-and-recently-updated-database-engine-docs"></a>Documentazione del motore di database nuova e aggiornata di recente



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **11/09/2017** &nbsp; - &nbsp; **27/09/2017**
- *Area di interesse:* &nbsp; **motore di database**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Aggiungere funzionalità a un'istanza di SQL Server (programma di installazione)](install-windows/add-features-to-an-instance-of-sql-server-setup.md)
2. [Installare SQL Server dal prompt dei comandi](install-windows/install-sql-server-from-the-command-prompt.md)
3. [Installare SQL Server tramite un file di configurazione](install-windows/install-sql-server-using-a-configuration-file.md)
4. [Continuità aziendale e recupero del database - SQL Server](sql-server-business-continuity-dr.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Installazione degli aggiornamenti dal prompt dei comandi](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-installing-updates-from-the-command-promptinstall-windowsinstalling-updates-from-the-command-promptmd"></a>1. &nbsp; [Installazione degli aggiornamenti dal prompt dei comandi](install-windows/installing-updates-from-the-command-prompt.md)

*Aggiornamento: 12/09/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 48.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 04abb23d0682c23654a55e7926d2140f0b6ae408 a4bb1e27ae99460a66da72848ace1417b148f85c  (PR=3122  ,  Filename=installing-updates-from-the-command-prompt.md  ,  Dirpath=docs\database-engine\install-windows\  ,  MergeCommitSha40=1df54edd5857ac2816fa4b164d268835d9713638) -->



- Aggiornare tutte le istanze di ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] nel computer e tutti i componenti condivisi, come ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] e Strumenti di gestione:

```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.
```

- Rimuovere un aggiornamento da una singola istanza di ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] e tutti i componenti condivisi, come ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] e Strumenti di gestione:

```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.
```

- Rimuovere un aggiornamento solo dai componenti condivisi di ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)], come ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] e Strumenti di gestione:

```
    <package_name>.exe /qs /Action=RemovePatch
```







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+1): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (4+1): documentazione del **motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (17+0): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+0): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1+1): documentazione dei **database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2+0): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+0): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


