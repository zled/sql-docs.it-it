---
title: "Importare ed esportare dati con l&#39;Importazione/Esportazione guidata SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "esportazione di dati"
  - "mapping di file [Integration Services]"
  - "Importazione/Esportazione guidata SQL Server"
  - "pacchetti SSIS, creazione"
  - "pacchetti [Integration Services], copia"
  - "pacchetti di Integration Services, creazione"
  - "pacchetti [Integration Services], creazione"
  - "pacchetti di SQL Server Integration Services, creazione"
  - "importazione ed esportazione guidate"
  - "copia di dati [Integration Services]"
  - "importazione di dati, pacchetti SSIS"
  - "origini [Integration Services], copia di dati"
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 134
---
# Importare ed esportare dati con l&#39;Importazione/Esportazione guidata SQL Server
 L'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di copiare facilmente i dati da un'origine a una destinazione. Per eseguire la procedura guidata non è necessario che SQL Server sia installato. Questa panoramica descrive le origini dati dalle o nelle quali è possibile importare i dati tramite la procedura guidata e le autorizzazioni necessarie per eseguire tale procedura.

Questo argomento fornisce solo una **panoramica** della procedura guidata.
-   Se si è pronti per eseguire la procedura guidata e servono solo le istruzioni per iniziare, vedere [Avviare l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).
-   Per informazioni sui passaggi della procedura guidata, selezionare la pagina desiderata nel menu di navigazione del contenuto. Per ogni pagina della procedura guidata è disponibile una pagina di documentazione separata. In alternativa, premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.

**Ottenere la procedura guidata.** Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!TIP] Se è necessario copiare più di un database oppure oggetti di database diversi da tabelle e viste, usare Copia guidata database anziché l'Importazione/Esportazione guidata. Per altre informazioni, vedere [Utilizzo di Copia guidata database](../../relational-databases/databases/use-the-copy-database-wizard.md).

## <a name="example-of-a-common-use-case---exporting-data-to-excel-video"></a>Esempio di un caso d'uso comune: esportazione di dati in Excel (video)  
La procedura guidata viene spesso usata per esportare i dati in Excel. Questo video di YouTube della durata di quattro minuti illustra la procedura guidata e descrive come eseguire l'operazione con istruzioni chiare e semplici: [Using the SQL Server Import and Export Wizard to Export to Excel](https://go.microsoft.com/fwlink/?linkid=829049) (Uso dell'Importazione/Esportazione guidata SQL Server per l'esportazione in Excel).

##  <a name="a-namewizardsourcesa-what-data-sources-and-destinations-can-i-use"></a><a name="wizardSources"></a> Quali origini e destinazioni di dati è possibile usare?  
 L'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di copiare dati dalle/nelle origini dati seguenti. Per poter usare alcune di queste origini dati è possibile che sia necessario scaricare e installare file aggiuntivi.

| Origine dati | È necessario scaricare file aggiuntivi? |
|-------------|-----------------------------------------|
|**Database aziendali**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle e altri.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installa i file che devono essere connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e Oracle, ma non i file che devono essere connessi ad altri database aziendali come IBM DB2 o Informix.<br/>- Se il software client relativo al proprio database aziendale è già installato, non sono generalmente necessari altri componenti per eseguire la connessione.<br/>- Se invece il software client non è installato, chiedere all'amministratore del database come poterne installare una copia con licenza.|
|**Database open source**<br/>MySql, PostgreSQL, SQLite e altri.|È necessario scaricare file aggiuntivi per eseguire la connessione a queste origini dati.<br/><br/>- Per **MySql**, vedere [MySQL Connectors](http://dev.mysql.com/downloads/connector/) (Connettori MySQL).<br/>- Per **PostgreSQL**, vedere [psqlODBC - PostgreSQL ODBC driver](https://odbc.postgresql.org/) (psqlODBC - Driver ODBC per PostgreSQL) e prodotti di terze parti come [Npgsql - .NET Data Provider for PostgreSQL](http://www.npgsql.org/) (Npgsql - Provider di dati .NET per PostgreSQL).<br/>- Per **SQLite**, selezionare uno dei vari provider e driver open source disponibili online.|
|**File di testo** (file flat).|Non sono necessari file aggiuntivi.|
|**File di Microsoft Excel e Microsoft Access**|Microsoft Office non installa tutti i file necessari per eseguire la connessione a file Excel e Access come origini dati. È necessario scaricare [Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040).|
|**Origini dati di Azure**<br/>Attualmente solo Archiviazione BLOB di Azure.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non installa i file necessari per eseguire la connessione ad Archiviazione BLOB di Azure come origine dati. È necessario scaricare [Microsoft SQL Server 2016 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=49492).|
|**Qualsiasi altra origine dati per cui è disponibile un connettore**.|In genere è necessario scaricare file aggiuntivi per eseguire la connessione ai tipi di origine dati seguenti.<br/><br/>- Qualsiasi origine per la quale è disponibile un **driver ODBC**. Stabilire una connessione di tipo ODBC (Open Database Connectivity) selezionando il provider .NET Framework per ODBC nella pagina **Scegliere un'origine dati** o **Scegliere una destinazione** della procedura guidata e quindi specificando una stringa di connessione o un DSN (Data Source Name) esistente che faccia riferimento al driver ODBC.<br/>- Qualsiasi origine per la quale è disponibile un **provider OLE DB**.<br/>- Qualsiasi origine per la quale è disponibile un **provider di dati .NET Framework**.<br/>- Altre origini dati per cui **componenti di terze parti** offrono funzionalità di origine e destinazione. Questi prodotti di terze parti vengono generalmente commercializzati come prodotti aggiuntivi per SQL Server Integration Services (SSIS).|
  
> [!TIP] Se l'origine dati richiede una stringa di connessione, è possibile trovare esempi su questo sito di terze parti relativo al [riferimento sulle stringhe di connessione](https://www.connectionstrings.com/).  
  
## <a name="what-permissions-do-i-need-to-run-the-wizard"></a>Quali autorizzazioni sono richieste per eseguire la procedura guidata?  
 Per eseguire l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario avere almeno le autorizzazioni seguenti. Se si usano già un'origine dati e una destinazione, è probabile che si abbiano già le autorizzazioni necessarie.
  
|Azioni per le quali sono necessarie autorizzazioni|Autorizzazioni necessarie se si è connessi a SQL Server |  
|-------------------------|----------------------------------------------------|  
|Eseguire la connessione a database di origine e di destinazione o a condivisioni file.|Diritti di accesso al server e al database.|  
|Esportare o leggere dati dal file o dal database di origine.|Autorizzazioni SELECT nelle viste e nelle tabelle di origine.|  
|Importare o scrivere dati nel file o nel database di destinazione.|Autorizzazioni INSERT nelle tabelle di destinazione.|  
|Creare il file o il database di destinazione, se applicabile.|Autorizzazioni CREATE DATABASE o CREATE TABLE.|  
|Salvare il pacchetto SSIS creato dalla procedura guidata, se applicabile.|Se si vuole salvare il pacchetto in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sono sufficienti le autorizzazioni necessarie per salvare il pacchetto nel database **msdb**.|  
  
##  <a name="a-namewizardssisa-the-wizard-uses-sql-server-integration-services-ssis"></a><a name="wizardSSIS"></a> La procedura guidata usa SQL Server Integration Services (SSIS)  
 La procedura guidata usa SQL Server Integration Services (SSIS) per copiare i dati. SSIS è uno strumento per l'estrazione, la trasformazione e il caricamento di dati. Le pagine della procedura guidata usano alcuni dei termini specifici di SSIS.
  
 In SSIS il **pacchetto** rappresenta l'unità di base. La procedura guidata crea un pacchetto SSIS in memoria mentre ci si sposta tra le pagine della procedura guidata e si specificano le opzioni.    
  
Al termine della procedura guidata, se si usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition o versioni successive, è possibile salvare il pacchetto SSIS. In un momento successivo sarà quindi possibile riusare il pacchetto o estenderlo aggiungendo attività, trasformazioni e logica guidata dagli eventi tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. L'utilizzo di Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] costituisce il metodo più semplice per creare un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] di base che consenta di copiare dati da un'origine a una destinazione.

Per altre informazioni su SSIS, vedere [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).

## <a name="get-help-while-the-wizard-is-running"></a>Visualizzare la Guida durante l'esecuzione della procedura guidata
> [!TIP] Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.   
  
## <a name="whats-next"></a>Operazioni successive  
 Avviare la procedura guidata. Per altre informazioni, vedere [Avviare SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="see-also"></a>Vedere anche
[Data Type Mapping in the SQL Server Import and Export Wizard](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md) (Mapping dei tipi di dati nell'Importazione/Esportazione guidata SQL Server)
