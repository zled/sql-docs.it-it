---
title: 'Aggiornato: documentazione di Integration Services per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione, per Integration Services per Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.date: 04/28/2018
ms.openlocfilehash: 865a5c79c3726b36faed32d24c07c37ea4837ba2
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406183"
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Articoli nuovi e aggiornati di recente: Integration Services per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **Integration Services per SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Caricare i dati da o in Excel con SQL Server Integration Services (SSIS)](load-data-to-from-excel-with-ssis.md)
2. [Caricare i dati da SQL Server in Azure SQL Data Warehouse con SQL Server Integration Services (SSIS)](load-data-to-sql-data-warehouse.md)
3. [Supporto di Scale Out per disponibilità elevata tramite istanza del cluster di failover di SQL Server](scale-out/scale-out-failover-cluster-instance.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Installazione di Integration Services](#TitleNum_1)
2. [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-install-integration-servicesinstall-windowsinstall-integration-servicesmd"></a>1. &nbsp; [Installazione di Integration Services](install-windows/install-integration-services.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 75.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 49551f3b1138f805e6d5e0f6099a100e2f3b3e7a 97caaafc1587b2326f4c357dd5eb21f2de7d358f  (PR=5676  ,  Filename=install-integration-services.md  ,  Dirpath=docs\integration-services\install-windows\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**Installazione completa di Integration Services**


Per un'installazione completa di *{Included-Content-Goes-Here}*, selezionare i componenti necessari dall'elenco seguente:

-   **Integration Services (SSIS)**. Installare SSIS con l'Installazione guidata di SQL Server. Se si seleziona SSIS viene installato quanto segue:
    -   Supporto per il catalogo SSIS nel motore di database di SQL Server.
    -   Facoltativamente, funzionalità SSIS Scale Out, costituita da un master e da diversi ruoli di lavoro.
    -   Componenti SSIS a 32 e a 64 bit.
    -   L'installazione di SSIS **non** installa gli strumenti necessari per progettare e sviluppare pacchetti SSIS.
-   **Motore di database di SQL Server**. Installare il motore di database con l'Installazione guidata di SQL Server. La selezione del motore di database consente di creare e ospitare il database del catalogo SSIS, `SSISDB`, per archiviare, gestire, eseguire e monitorare i pacchetti SSIS.
-   **SQL Server Data Tools (SSDT)**. Per scaricare e installare SSDT, vedere [Scaricare SQL Server Data Tools (SSDT)]. L'installazione di SSDT consente di progettare e distribuire pacchetti SSIS. Con SSDT vengono installati i componenti seguenti:
    -   Strumenti di progettazione e sviluppo di pacchetti SSIS, incluso Progettazione SSIS.
    -   Solo componenti di SSIS a 32 bit.
    -   Una versione limitata di Visual Studio, se non è installata alcuna edizione di Visual Studio.
    -   Visual Studio Tools for Applications (VSTA), l'editor di script usato dall'attività Script SSIS e dal componente script.
    -   Procedure guidate SSIS tra cui la Distribuzione guidata e l'Aggiornamento guidato pacchetti.
    -   Importazione ed esportazione guidate di SQL Server.
-   **Integration Services Feature Pack per Azure**. Per scaricare e installare il Feature Pack, vedere [Microsoft SQL Server 2017 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=54798). L'installazione del Feature Pack consente la connessione dei pacchetti ai servizi di archiviazione e analisi nel cloud di Azure, inclusi i servizi seguenti:



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-deploy-run-and-monitor-an-ssis-package-on-azurelift-shiftssis-azure-deploy-run-monitor-tutorialmd"></a>2. &nbsp; [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](lift-shift/ssis-azure-deploy-run-monitor-tutorial.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 99.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07f2b752818f2e786c4380fb822099190c59f302 54de9497353bac2d6a8a87e546fc6ab9e444a734  (PR=5676  ,  Filename=ssis-azure-deploy-run-monitor-tutorial.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**Distribuire un progetto con PowerShell**


Per distribuire un progetto con PowerShell in SSISDB nel database SQL di Azure, adattare lo script seguente secondo i propri requisiti. Lo script enumera le cartelle figlio in `$ProjectFilePath` e i progetti in ogni cartella figlio, quindi crea le stesse cartelle in SSISDB e distribuisce i progetti in tali cartelle.

Questo script richiede SQL Server Data Tools versione 17.x o SQL Server Management Studio installato nel computer in cui viene eseguito lo script.

```
**Variables**

$ProjectFilePath = "C:\<folder>"
$SSISDBServerEndpoint = "<servername>.database.windows.net"
$SSISDBServerAdminUserName = "<username>"
$SSISDBServerAdminPassword = "<password>"

**Load the IntegrationServices Assembly**

[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices") | Out-Null;

**Store the IntegrationServices Assembly namespace to avoid typing it every time**

$ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"

Write-Host "Connecting to server ..."

**Create a connection to the server**

$sqlConnectionString = "Data Source=" + $SSISDBServerEndpoint + ";User ID="+ $SSISDBServerAdminUserName +";Password="+ $SSISDBServerAdminPassword + ";Initial Catalog=SSISDB"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

**Create the Integration Services object**

$integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection

**Get the catalog**

$catalog = $integrationServices.Catalogs['SSISDB']

write-host "Enumerating all folders..."

$folders = ls -Path $ProjectFilePath -Directory

if ($folders.Count -gt 0)
{
    foreach ($filefolder in $folders)
    {
        Write-Host "Creating Folder " $filefolder.Name " ..."

        # Create a new folder
        $folder = New-Object $ISNamespace".CatalogFolder" ($catalog, $filefolder.Name, "Folder description")
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11+6):&nbsp; documentazione di &nbsp;**Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18+0): &nbsp; documentazione di &nbsp;**Analysis Services per SQL Server**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218+14):**documentazione della**connessione a SQL Server](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14+0):&nbsp; documentazione del &nbsp;**motore di database per SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3+2): documentazione di &nbsp;&nbsp;**SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+3):&nbsp; documentazione di &nbsp;**Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7+10):&nbsp; documentazione dei &nbsp;**database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+3):&nbsp; documentazione di &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2+3):&nbsp; documentazione di &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5+2):&nbsp; documentazione di &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+1): documentazione di &nbsp;&nbsp;**Tools per SQL Server**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0):**documentazione della**piattaforma di strumenti analitici per SQL Server](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)

