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
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ce80496cdf82c2bc2df2447ed043216e6c78ad7e
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-database-engine-docs"></a>Documentazione del motore di database nuova e aggiornata di recente



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **18/07/2017** &nbsp; - &nbsp; **11/09/2017**
- *Area di interesse:* &nbsp; **motore di database**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Installazione di SQL Server](install-windows/installation-for-sql-server.md)
2. [Aggiornamenti di versione ed edizione supportati per SQL Server 2017](install-windows/supported-version-and-edition-upgrades-2017.md)
3. [Motore di database di SQL Server](sql-server-database-engine-overview.md)
4. [Novità del motore di database - SQL Server 2016](whats-new-in-sql-server-2016.md)
5. [Novità del motore di database - SQL Server 2017](whats-new-in-sql-server-2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Seeding automatico per le repliche secondarie](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-seeding-for-secondary-replicasavailability-groupswindowsautomatic-seeding-secondary-replicasmd"></a>1. &nbsp; [Seeding automatico per le repliche secondarie](availability-groups/windows/automatic-seeding-secondary-replicas.md)

*Aggiornamento: 21-08-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 55.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0b7b6a23f38bfe5959ccd170527a9bbdb308dc4b dc51fdf69649ed6cae03584cff7bc900d5b72149  (PR=2896  ,  Filename=automatic-seeding-secondary-replicas.md  ,  Dirpath=docs\database-engine\availability-groups\windows\  ,  MergeCommitSha40=80642503480add90fc75573338760ab86139694c) -->



In SQL Server 2016 e versioni precedenti la cartella in cui viene creato il database per il seeding automatico deve già esistere e deve essere uguale a quella del percorso per la replica primaria.

In SQL Server 2017 Microsoft consiglia di usare lo stesso percorso per i dati e per il file di log in tutte le repliche che partecipano a un gruppo di disponibilità, ma è possibile usare percorsi diversi se necessario. Ad esempio, in un gruppo di disponibilità multipiattaforma un'istanza di SQL Server si trova su Windows e un'altra istanza di SQL Server si trova su Linux. Le diverse piattaforme hanno percorsi predefiniti diversi. SQL Server 2017 supporta repliche dei gruppi di disponibilità su istanze di SQL Server con percorsi predefiniti diversi.

La tabella seguente presenta esempi di layout dei dischi di dati supportati che possono supportare il seeding automatico:

|Istanza primaria</br>Percorso dati predefinito|Istanza secondaria</br>Percorso dati predefinito|Istanza primaria</br>Percorso file di origine|Istanza secondaria</br> Percorso file di destinazione
|:------|:------|:------|:------
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\ |/var/opt/mssql/data/|
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\group1\\ |/var/opt/mssql/data/group1/|
|c:\\data\\ |d:\\data\\ |c:\\data\\ |d:\\data\\
|c:\\data\\ |d:\\data\\ |c:\\data\\group1\\ |d:\\data\\group1\

Gli scenari in cui i percorsi dei database di replica primari e secondari non corrispondono ai percorsi predefiniti dell'istanza non sono interessati da questa modifica. I requisiti relativi alla corrispondenza dei percorsi file di replica secondaria e dei percorsi file di replica primaria rimangono invariati.

|Istanza primaria</br>Percorso dati predefinito|Istanza secondaria</br>Percorso dati predefinito|Istanza primaria</br>Percorso del file|Istanza secondaria</br> Percorso del file
|:------|:------|:------|:------
|c:\\data\\ |c:\\data\\ |d:\\group1\\ |d:\\group1\\
|c:\\data\\ |c:\\data\\ |d:\\data\\ |d:\\data\\
|c:\\data\\ |c:\\data\\ |d:\\data\\group1\\ |d:\\data\\group1\\

Se si combinano percorsi predefiniti e non predefiniti nelle repliche primarie e secondarie, SQL Server 2017 si comporta in modo diverso rispetto alle versioni precedenti. La tabella seguente illustra questo comportamento di SQL Server 2017.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+12): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5+1): documentazione di **Motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19+82): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1+8): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12+1): documentazione di **Database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+1): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+2): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1+4): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (4+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0+1): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



