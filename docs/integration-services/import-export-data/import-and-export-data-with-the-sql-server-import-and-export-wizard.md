---
title: Importare ed esportare i dati con il Server importazione / esportazione guidata SQL | Documenti Microsoft
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 6cd388215de02072522011b149a9cecc3239b64c
ms.contentlocale: it-it
ms.lasthandoff: 10/18/2017

---
# <a name="import-and-export-data-with-the-sql-server-import-and-export-wizard"></a>Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server

 > Per contenuti relativi a versioni precedenti di SQL Server, vedere [eseguire SQL Server di importazione / esportazione guidata](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx).

 L'Importazione/Esportazione guidata[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di copiare facilmente i dati da un'origine a una destinazione. Questa panoramica descrive le origini dati che la procedura guidata è possibile utilizzare come origini e destinazioni, nonché le autorizzazioni che necessarie per eseguire la procedura guidata.

## <a name="get-the-wizard"></a>Ottenere la procedura guidata
Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="what-happens-when-i-run-the-wizard"></a>Cosa accade quando si esegue la procedura guidata?
-    **Vedere l'elenco dei passaggi.** Per una descrizione dei passaggi della procedura guidata, vedere [i passaggi in SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). È inoltre disponibile una pagina separata della documentazione per ogni pagina della procedura guidata.  
    \- o \-
-   **Visualizzare un esempio.** Per un rapido controllo le schermate visualizzate diverse in una sessione tipica, esaminiamo questo semplice esempio in una singola pagina - [iniziare con questo semplice esempio di importazione / esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).  

##  <a name="wizardSources"></a>Informazioni sulle origini e destinazioni è possibile utilizzare?  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata possibile copiare i dati da e verso le origini dati elencate nella tabella seguente. Per connettersi ad alcune di queste origini dati, è necessario scaricare e installare i file aggiuntivi.
 
| Origine dati | È necessario scaricare file aggiuntivi? |
|-------------|-----------------------------------------|
|**Database aziendali**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, DB2 e altri.|SQL Server o SQL Server Data Tools (SSDT) vengono installati i file che si devono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ma SSDT non installa tutti i file necessari per connettersi ad altri database aziendali, ad esempio Oracle o IBM DB2.<br/><br/>Per connettersi a un database dell'organizzazione, in genere è necessario disporre di due operazioni:<br/><br/>1. **Il software client**. Se il software client relativo al proprio database aziendale è già installato, non sono generalmente necessari altri componenti per eseguire la connessione. Se invece il software client non è installato, chiedere all'amministratore del database come poterne installare una copia con licenza.<br/><br/>2. **I driver o provider**. Microsoft consente di installare i driver e provider per la connessione a Oracle. Per connettersi a IBM DB2, ottenere il Provider di Microsoft® OLE DB per DB2 v 5.0 per Microsoft SQL Server dal [Feature Pack di Microsoft SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=52676).<br/><br/>Per altre informazioni, vedere [connettersi a un'origine dati di SQL Server](connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md) o [connettersi a un'origine dati Oracle](connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md).|
|**File di testo** (file flat)|Non sono necessari file aggiuntivi.<br/><br/>Per altre informazioni, vedere [connettersi a un'origine dati File Flat](connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md).|
|**File di Microsoft Excel e Microsoft Access**|Microsoft Office non installa tutti i file necessari per eseguire la connessione a file Excel e Access come origini dati. Scarica il programma seguente - [Microsoft Access Database Engine 2016 Redistributable](https://www.microsoft.com/download/details.aspx?id=54920).<br/><br/>Per altre informazioni, vedere [Connetti a un'origine dati di Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md) o [connessione a un'origine dati accesso](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md).|
|**Origini dati di Azure**<br/>Attualmente solo Archiviazione BLOB di Azure.|SQL Server Data Tools non installare i file che si devono connettersi all'archiviazione Blob di Azure come origine dati. È necessario scaricare [Microsoft SQL Server 2016 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=49492).<br/><br/>Per altre informazioni, vedere [Connect per l'archiviazione BLOB di Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md).|
|**Database open source**<br/>PostgreSQL, MySql e altri.|Per connettersi a queste origini dati, è necessario scaricare file aggiuntivi.<br/><br/>-Per **PostgreSQL**, vedere [connessione a un'origine dati PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md).<br/>-Per **MySql**, vedere [connessione a un'origine dati MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md).|
|**Qualsiasi altra origine dati per cui è disponibile un driver o un provider**|In genere è necessario scaricare file aggiuntivi per eseguire la connessione ai tipi di origine dati seguenti.<br/><br/>- Qualsiasi origine per la quale è disponibile un **driver ODBC** . Per altre informazioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).<br/>- Qualsiasi origine per la quale è disponibile un **provider di dati .NET Framework** .<br/>- Qualsiasi origine per la quale è disponibile un **provider OLE DB** .<br/><br/>Componenti di terze parti che forniscono funzionalità di origine e di destinazione per le altre origini dati sono a volte commercializzati come prodotti aggiuntivi per SQL Server Integration Services (SSIS).|

## <a name="how-do-i-connect-to-my-data"></a>Come connettersi a dati?
Per informazioni su come connettersi a un'origine dati di uso comune, vedere una delle seguenti pagine:
-   [Connettersi a SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi ai file flat (file di testo)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a accesso](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi all'archiviazione Blob di Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Connettersi con ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [La connessione a MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)


Per informazioni su come connettersi a un'origine dati che non è elencata, vedere [al riferimento di stringhe di connessione](https://www.connectionstrings.com/). In questo sito di terze parti sono stringhe di connessione di esempio e altre informazioni sui provider di dati e le informazioni di connessione che richiedono.

## <a name="what-permissions-do-i-need"></a>Quali autorizzazioni sono necessarie?  
 Per eseguire l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario avere almeno le autorizzazioni seguenti. Se si usano già un'origine dati e una destinazione, è probabile che si abbiano già le autorizzazioni necessarie.
  
|Azioni per le quali sono necessarie autorizzazioni|Se ci si connette a SQL Server, è necessario che queste autorizzazioni |  
|-------------------------|----------------------------------------------------|  
|Eseguire la connessione a database di origine e di destinazione o a condivisioni file.|Diritti di accesso al server e al database.|  
|Esportare o leggere dati dal file o dal database di origine.|Autorizzazioni SELECT nelle viste e nelle tabelle di origine.|  
|Importare o scrivere dati nel file o nel database di destinazione.|Autorizzazioni INSERT nelle tabelle di destinazione.|  
|Creare il file o il database di destinazione, se applicabile.|Autorizzazioni CREATE DATABASE o CREATE TABLE.|  
|Salvare il pacchetto SSIS creato dalla procedura guidata, se applicabile.|Se si vuole salvare il pacchetto in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sono sufficienti le autorizzazioni necessarie per salvare il pacchetto nel database **msdb** .|  
  
## <a name="get-help-while-the-wizard-is-running"></a>Visualizzare la Guida durante l'esecuzione della procedura guidata
> [!TIP]
> Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.   
  
##  <a name="wizardSSIS"></a> La procedura guidata usa SQL Server Integration Services (SSIS)  
 La procedura guidata usa SQL Server Integration Services (SSIS) per copiare i dati. SSIS è uno strumento per l'estrazione, la trasformazione e il caricamento di dati. Le pagine della procedura guidata usano alcuni dei termini specifici di SSIS.
  
 In SSIS il **pacchetto**rappresenta l'unità di base. La procedura guidata crea un pacchetto SSIS in memoria mentre ci si sposta tra le pagine della procedura guidata e si specificano le opzioni.    
  
Al termine della procedura guidata, se si usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition o versioni successive, è possibile salvare il pacchetto SSIS. In un momento successivo sarà quindi possibile riusare il pacchetto o estenderlo aggiungendo attività, trasformazioni e logica guidata dagli eventi tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . L'utilizzo di Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] costituisce il metodo più semplice per creare un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] di base che consenta di copiare dati da un'origine a una destinazione.

Per altre informazioni su SSIS, vedere [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).

## <a name="whats-next"></a>Operazioni successive  
 Avviare la procedura guidata. Per altre informazioni, vedere [Avviare SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)  
[Mapping dei tipi di dati nell'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)



