---
title: 'Articolo aggiornato: documentazione di SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: sql-server
ms.date: 02/03/2018
ms.openlocfilehash: 9d16ef6e59a911b8963bfda46cad9ed6d8e8109c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Articoli nuovi e aggiornati di recente: documentazione di SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Aggiornare istanze di SQL Server in esecuzione in cluster di Windows Server 2008/2008 R2/2012](failover-clusters/windows/upgrade-sql-server-failover-cluster-instance-2008-2012.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Guida offline di SQL Server e Help Viewer](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-offline-help-and-help-viewersql-server-help-installationmd"></a>1. &nbsp; [Guida offline di SQL Server e Help Viewer](sql-server-help-installation.md)

*Aggiornamento: 19/12/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 67.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ea491fdc173a54fb4cdb3dfa2e26bd206d1cc45d 22444427a48064b76088d19d1ffae0a885bfe2a7  (PR=4338  ,  Filename=sql-server-help-installation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=f2fde1c324466530f92006561a9a29decb711e1b) -->



   Help Viewer si apre con la scheda Gestisci contenuto visualizzata.

2. Per installare il pacchetto di contenuto della Guida più recente, scegliere **Online** come origine dell'installazione.

   ![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-onlinesource.png)

   >[!NOTE]
   > Per eseguire l'installazione dal disco (Guida di SQL Server 2014), scegliere **Disco** come origine dell'installazione e specificare il percorso del disco.

   Il percorso dell'archivio locale nella scheda Gestisci contenuto indica dove verrà installato il contenuto nel computer locale. Per modificare il percorso, fare clic su **Sposta**, immettere un altro percorso di cartella nel campo **A** e quindi fare clic su **OK**.
   Se l'installazione della Guida non riesce dopo aver modificato il percorso dell'archivio locale, chiudere e riaprire Help Viewer, verificare che la nuova posizione appaia nel percorso dell'archivio locale e quindi tentare nuovamente l'installazione.

3. Fare clic su **Aggiungi** accanto a ogni pacchetto di contenuto (libro) da installare.
   Per installare tutto il contenuto della Guida di SQL Server, aggiungere tutti i 13 libri in SQL Server.

4. Fare clic su **Aggiorna** in basso a destra.
   Il sommario della Guida a sinistra si aggiorna automaticamente con i libri aggiunti.

   ![HelpViewer2_ManageContent_AddContent](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-addcontent.png)

> [!NOTE]
> Non tutti i titoli del nodo superiore nel sommario di SQL Server corrispondono esattamente ai nomi dei libri della Guida scaricabili corrispondenti. I titoli del sommario sono associati ai nomi dei libri come indicato di seguito:

| Riquadro del contenuto | Libro di SQL Server |
|-----|-----|
|Guida di riferimento al linguaggio di Analysis Services | Guida di riferimento al linguaggio di Analysis Services (MDX)|
|Guida di riferimento a Data Analysis Expressions (DAX) | Guida di riferimento a Data Analysis Expressions (DAX)|
|Guida di riferimento a DMX (Data Mining Extensions) | Guida di riferimento a DMX (Data Mining Extensions)|
|Guide per sviluppatori per SQL Server | Guida di riferimento per sviluppatori per SQL Server|
|Scaricare SQL Server Management Studio | SQL Server Management Studio|







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (1+3):&nbsp; documentazione di **Advanced Analytics per SQL** ](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **piattaforma di strumenti analitici per SQL** ](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **connessione a SQL Server** ](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione del **motore di database di SQL Server** ](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12+1): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6+2):&nbsp; documentazione di **Linux per SQL Server** ](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15+0):**documentazione di**PowerShell per SQL Server](../powershell/new-updated-powershell.md)
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
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


