---
title: Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code) | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: quick-start
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c962285d10ca05434deafc9cf1d071a09f8cca65
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Eseguire un pacchetto SSIS da Visual Studio Code con Transact-SQL
Questa guida introduttiva illustra come usare Visual Studio Code per connettersi al database del catalogo SSIS e quindi usare istruzioni Transact-SQL per eseguire un pacchetto SSIS archiviato nel catalogo SSIS.

Visual Studio Code è un editor di codice per Windows, macOS e Linux che supporta le estensioni, incluse le estensioni `mssql` per la connessione a Microsoft SQL Server, al database SQL di Azure o ad Azure SQL Data Warehouse. Per altre informazioni su Visual Studio Code, vedere [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Prerequisites

Prima di iniziare, assicurarsi di aver installato la versione più recente di Visual Studio Code e caricato l'estensione `mssql`. Per scaricare questi strumenti, vedere le pagine seguenti:
-   [Scaricare il codice per Visual Studio](https://code.visualstudio.com/Download)
-   [Estensione mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Impostare la modalità di linguaggio su SQL in Visual Studio Code

Per abilitare i comandi `mssql` e Transact-SQL IntelliSense, la modalità di linguaggio è impostata su **SQL** in Visual Studio Code.

1. Aprire Visual Studio Code e quindi aprire una nuova finestra. 

2. Fare clic su **Testo normale** nell'angolo inferiore destro della barra di stato.

3. Nel menu a discesa **Seleziona modalità linguaggio** visualizzato selezionare o immettere **SQL** e quindi premere **INVIO** per impostare la modalità del linguaggio su SQL. 

## <a name="connect-to-the-ssis-catalog-database"></a>Connettersi al database del catalogo SSIS

Usare SQL Visual Studio Code per stabilire una connessione al catalogo SSIS.

> [!IMPORTANT]
> Prima di continuare, verificare che siano disponibili le informazioni relative a server, database e accesso. Se si sposta lo stato attivo da Visual Studio Code quando si inizia a immettere le informazioni sul profilo di connessione, è necessario riavviare la creazione del profilo di connessione.

1. In Visual Studio Code premere **CTRL+MAIUSC+P** (o **F1**) per aprire il riquadro comandi.

2. Digitare **sqlcon** e premere **INVIO**.

3. Premere **INVIO** per iniziare la procedura di **creazione del profilo di connessione**. Questo passaggio consente di creare un profilo di connessione per l'istanza di SQL Server.

4. Seguire le istruzioni per specificare le proprietà di connessione per il nuovo profilo di connessione. Dopo aver specificato ogni valore, premere **INVIO** per continuare. 

   | Impostazione       | Valore suggerito | Altre informazioni |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nome server** | Nome completo del server | Se si sta eseguendo la connessione a un server di database SQL di Azure, il nome è nel formato `<server_name>.database.windows.net`. |
   | **Nome database** | **SSISDB** | Il nome del database a cui si effettua la connessione. |
   | **Autenticazione** | Account di accesso SQL| In questa guida rapida viene usata l'autenticazione SQL. |
   | **User name** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password (account di accesso SQL)** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |
   | **Salvare la password?** | Sì o No | Se non si vuole immettere la password ogni volta, selezionare Sì. |
   | **Immettere un nome per questo profilo** | Un nome di profilo, ad esempio **mySSISServer** | Se si salva un nome di profilo, gli accessi successivi saranno più rapidi. | 

5. Premere il tasto **ESC** per chiudere il messaggio che informa che il profilo è stato creato e connesso.

6. Verificare la connessione nella barra di stato.

## <a name="run-the-t-sql-code"></a>Eseguire il codice T-SQL
Eseguire il codice Transact-SQL seguente per eseguire un pacchetto SSIS.

1. Nella finestra **Editor** immettere la query seguente nella finestra di query vuota. Questo è il codice generato dall'opzione **Script** nella finestra di dialogo **Esegui pacchetto** di SSMS.

2. Aggiornare i valori dei parametri nella stored procedure `catalog.create_execution` in base al sistema in uso.

3. Premere **CTRL+MAIUSC+E** per eseguire il codice ed eseguire il pacchetto.

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx',
    @execution_id=@execution_id OUTPUT,
    @folder_name=N'Deployed Projects',
      @project_name=N'Integration Services Project1',
    @use32bitruntime=False,
      @reference_id=Null
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,
    @object_type=50,
      @parameter_name=N'LOGGING_LEVEL',
      @parameter_value=@var0
EXEC [SSISDB].[catalog].[start_execution] @execution_id
GO
```

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con SSMS](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
