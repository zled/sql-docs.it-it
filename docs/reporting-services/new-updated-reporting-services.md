---
title: 'Articoli nuovi e aggiornati di recente: Reporting Services per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione, per Reporting Services per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: reporting-services
ms.suite: pro-bi
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: 
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.author: genemi
ms.workload: reporting-services
ms.openlocfilehash: fc35b1dc39ded10eaf20f503fb561562ce55da98
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-reporting-services-for-sql-server"></a>Articoli nuovi e aggiornati di recente: Reporting Services per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **Reporting Services per SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Log delle modifiche per SQL Server Reporting Services](change-log-sql-server-reporting-services.md)
2. [Sviluppare con le API REST per Reporting Services](developer/rest-api.md)
3. [Web part di Visualizzatore di report in un sito di SharePoint](report-server-sharepoint/report-viewer-web-part-sharepoint-site.md)
4. [Impostazioni del sito di SharePoint per la web part Visualizzatore di report](report-server-sharepoint/report-viewer-web-part-sharepoint-site-settings.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Installare SQL Server Reporting Services](#TitleNum_1)
2. [Distribuire la web part Visualizzatore di report di SQL Server Reporting Services in un sito di SharePoint](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-install-sql-server-reporting-servicesinstall-windowsinstall-reporting-servicesmd"></a>1. &nbsp; [Installare SQL Server Reporting Services](install-windows/install-reporting-services.md)

*Aggiornamento: 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 66.  ms.author= "asaxton".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c959622d4d10a71ed598256e8e284130eb49af5b 77dc1b4f6696e911ed036fc27724ff8a96b79f57  (PR=4150  ,  Filename=install-reporting-services.md  ,  Dirpath=docs\reporting-services\install-windows\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    > The default path is C:\Program Files\Microsoft SQL Server Reporting Services.

7. Una volta completata l'installazione, selezionare **Configura server di report** per avviare Gestione configurazione Reporting Services.

    ![Configurare il server di report--media/install-reporting-services/report-server-install-configure.png)

**Configurazione del server di report**


Dopo aver selezionato **Configura server di report** nel programma di installazione, verrà visualizzata la **Gestione configurazione del server di report**. Per altre informazioni, vedere [Gestione configurazione server di report--reporting-services-configuration-manager-native-mode.md).

È necessario [creare un database del server di report--ssrs-report-server-create-a-report-server-database.md) per completare la configurazione iniziale di Reporting Services. Per completare questo passaggio è necessario un server di database di SQL Server.

**Creazione di un database in un server diverso**


Se si sta creando il database del server di report in un server di database in un computer diverso, è necessario modificare l'account del servizio del server di report con credenziali riconosciute nel server di database.

Per impostazione predefinita, il server di report usa l'account del servizio virtuale. Se si tenta di creare un database in un server diverso, si potrebbe ricevere l'errore seguente durante il passaggio di applicazione dei diritti di connessione.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Per risolvere l'errore, è possibile modificare l'account del servizio impostandolo su un servizio di rete o un account di dominio. Se si modifica l'account del servizio impostandolo su un servizio di rete, i diritti verranno applicati nel contesto dell'account computer del server di report.

Per altre informazioni, vedere [Configurare l'account del servizio del server di report--configure-the-report-server-service-account-ssrs-configuration-manager.md).

**Servizio Windows**


Come parte dell'installazione viene creato un servizio di Windows che viene visualizzato come **SQL Server Reporting Services**. Il nome del servizio è **SQLServerReportingServices**.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-sitereport-server-sharepointdeploy-report-viewer-web-partmd"></a>2. &nbsp; [Distribuire la web part Visualizzatore di report di SQL Server Reporting Services in un sito di SharePoint](report-server-sharepoint/deploy-report-viewer-web-part.md)

*Aggiornamento: 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 129.  ms.author= "asaxton".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 99275aa597f491bb09688060b3f713406e2f0624 a282486da6df55154212c98fa06c7e62e66c8350  (PR=4150  ,  Filename=deploy-report-viewer-web-part.md  ,  Dirpath=docs\reporting-services\report-server-sharepoint\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



È possibile provare a eliminare la web part tramite PowerShell, ma per questa operazione non è disponibile un comando diretto. Per un esempio di script, vedere [How to delete web parts from the web part Gallery](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f) (Come eliminare web part dalla Raccolta web part).

**Lingue supportate**


La web part supporta le lingue seguenti:

* Inglese (en)
* Tedesco (de)
* Spagnolo (sp)
* Francese (fr)
* Italiano (it)
* Giapponese (ja)
* Coreano (ko)
* Portoghese (pt)
* Russo (ru)
* Cinese (semplificato - zh-HANS e zh-CHS)







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


