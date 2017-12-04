---
title: Validate SSIS packages deployed to Azure (Convalidare pacchetti SSIS distribuiti in Azure) | Microsoft Docs
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 15f838e93a5473a2d2345ae8c297f9b92eb2a23e
ms.sourcegitcommit: 19e1c4067142d33e8485cb903a7a9beb7d894015
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2017
---
# <a name="validate-ssis-packages-deployed-to-azure"></a>Convalidare pacchetti SSIS distribuiti in Azure
Quando si distribuisce un progetto di SQL Server Integration Services (SSIS) al database di catalogo SSIS (SSISDB) in un server di Azure, la distribuzione guidata del pacchetto prevede un passaggio di convalida aggiuntivo dopo la pagina relativa alla **revisione**. Questo passaggio di convalida controlla che i pacchetti del progetto non contengano problemi noti che potrebbero impedire la corretta esecuzione Runtime di integrazione di Azure SSIS. Quindi la procedura guidata consente di visualizzare gli avvisi applicabili nella pagina relativa alla **convalida**.

> [!IMPORTANT]
> La convalida descritta in questo articolo si verifica quando si distribuisce un progetto con una versione di SQL Server Data Tools (SSDT) 17.4 o successiva. Per scaricare la versione più recente di SSDT, vedere [Scaricare la versione più recente di SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).

Per altre informazioni sulla distribuzione guidata dei pacchetti, vedere [Distribuire progetti e pacchetti di Integration Services (SSIS)](../packages/deploy-integration-services-ssis-projects-and-packages.md).

## <a name="validate-connection-managers"></a>Convalidare le gestioni connessioni

La procedura guidata controlla che in alcune gestioni connessioni non siano presenti i problemi seguenti che potrebbero causare un errore di connessione:
- **Autenticazione di Windows**. Se una stringa di connessione usa l'autenticazione di Windows, la convalida genera un avviso. L'autenticazione di Windows richiede ulteriori passaggi di configurazione. Per altre informazioni, vedere [Connettersi a origini dati locali con Autenticazione Windows](ssis-azure-connect-with-windows-auth.md).
- **Percorso file**. Se una stringa di connessione contiene un percorso file locale hard-coded come `C:\\...`, la convalida genera un avviso. L'esecuzione di pacchetti che contengono un percorso assoluto potrebbe non riuscire.
- **Percorso UNC**. Se una stringa di connessione contiene un percorso UNC, la convalida genera un avviso. L'esecuzione di pacchetti che contengono un percorso UNC potrebbe non riuscire, in genere ciò si verifica perché i pacchetti UNC richiedono l'autenticazione di Windows per effettuare l'accesso.
- **Nome host**. Se una proprietà del server contiene il nome host anziché l'indirizzo IP, la convalida genera un avviso. L'esecuzione di pacchetti che contengono il nome host potrebbe non riuscire, in genere ciò si verifica perché la rete virtuale di Azure richiede la corretta configurazione di DNS per supportare la risoluzione dei nomi DNS.
- **Provider o driver**. Se un provider o il driver non è supportato, la convalida genera un avviso. In questo momento è supportato solamente un numero ridotto di driver e provider predefiniti.

La procedura guidata esegue i controlli di convalida seguenti per le gestioni connessioni nell'elenco.

| Gestione connessione | Autenticazione Windows | Percorso file | Percorso UNC | Nome host | Provider o driver |
|--------------------|----------|-----------|-----|-----------|-------------------|
| Ado                | ✓        |           |     | ✓         | ✓                 |
| AdoNet             | ✓        |           |     | ✓         | ✓                 |
| Cache              |          | ✓         | ✓   |           |                   |
| Excel              |          | ✓         | ✓   |           |                   |
| File               |          | ✓         | ✓   |           |                   |
| FlatFile           |          | ✓         | ✓   |           |                   |
| FTP                |          |           |     | ✓         |                   |
| MsOLAP100          |          |           |     | ✓         | ✓                 |
| MultiFile          |          | ✓         | ✓   |           |                   |
| MultiFlatFile      |          | ✓         | ✓   |           |                   |
| OData              | ✓        |           |     | ✓         |                   |
| Odbc               | ✓        |           |     | ✓         | ✓                 |
| OleDb              | ✓        |           |     | ✓         | ✓                 |
| SmoServer          | ✓        |           |     | ✓         |                   |
| SMTP               | ✓        |           |     | ✓         |                   |
| SQLMOBILE          |          | ✓         | ✓   |           |                   |
| WMI                | ✓        |           |     |           |                   |
|||||||

## <a name="validate-sources-and-destinations"></a>Convalidare origini e destinazioni
Le origini di terze parti e le destinazioni seguenti non sono supportate:

-   Origine e destinazione Oracle di Attunity
-   Origine e destinazione Teradata di Attunity
-   Origine e destinazione SAP BI

## <a name="validate-tasks-and-components"></a>Convalidare attività e componenti

### <a name="execute-process-task"></a>Attività Esegui processo

La convalida genera un avviso se un comando punta a un file locale con un percorso assoluto o a un file con un percorso UNC. Questi percorsi potrebbero causare un esito negativo dell'esecuzione in Azure.

### <a name="script-task-and-script-component"></a>Attività e componente Script

La convalida genera un avviso se un pacchetto contiene un'attività script o un componente script, che può fare riferimento o chiamare assembly non supportati. Questi riferimenti o chiamate possono causare un errore di esecuzione.

### <a name="other-components"></a>Altri componenti

Il formato Orc non è supportato nella destinazione HDFS e nella destinazione di Azure Data Lake Store.

## <a name="next-steps"></a>Passaggi successivi
Per informazioni su come pianificare l'esecuzione del pacchetto in Azure, vedere [Pianificare l'esecuzione di un pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).