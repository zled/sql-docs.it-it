---
title: Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code) | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a912bf7f7944d4af3d41c5596e67aa77f3214112
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Eseguire un pacchetto SSIS da codice di Visual Studio con Transact-SQL
Questa Guida introduttiva viene illustrato come utilizzare codice di Visual Studio per connettersi al database del catalogo SSIS e quindi utilizzare istruzioni Transact-SQL per eseguire un pacchetto SSIS archiviato nel catalogo SSIS.

Codice di Visual Studio è un editor di codice per Windows, macOS e Linux che supporta le estensioni, incluse le `mssql` estensione per la connessione a Microsoft SQL Server, Database SQL di Azure o Azure SQL Data Warehouse. Per ulteriori informazioni su Visual Studio Code, vedere [Visual Studio Cod](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi che hanno installato la versione più recente del codice di Visual Studio e caricato il `mssql` estensione. Per scaricare questi strumenti, vedere le pagine seguenti:
-   [Scaricare il codice per Visual Studio](https://code.visualstudio.com/Download)
-   [estensione MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Impostare la modalità di lingua su SQL nel codice di Visual Studio

Per abilitare `mssql` comandi e T-SQL IntelliSense, la modalità di linguaggio impostato **SQL** nel codice di Visual Studio.

1. Aprire Visual Studio Code e quindi aprire una nuova finestra. 

2. Fare clic su **testo normale** nell'angolo inferiore destro della barra di stato.

3. Nel **la modalità di selezione lingua** menu di scelta rapida che viene visualizzata, selezionare o immettere **SQL**e quindi premere **invio** su cui impostare la modalità di linguaggio SQL. 

## <a name="connect-to-the-ssis-catalog-database"></a>Connettersi al database del catalogo SSIS

Utilizzare Visual Studio Code per stabilire una connessione al catalogo SSIS.

> [!IMPORTANT]
> Prima di continuare, assicurarsi di disporre di server, database e le informazioni di accesso pronte. Se si modifica lo stato attivo dal codice di Visual Studio non appena si inizia a immettere le informazioni sul profilo di connessione, è necessario riavviare la creazione del profilo di connessione.

1. Nel codice di Visual Studio, premere **CTRL + MAIUSC + P** (o **F1**) per aprire il riquadro comandi.

2. Tipo **sqlcon** e premere **invio**.

3. Premere **invio** selezionare **Crea profilo di connessione**. Questo passaggio consente di creare un profilo di connessione per l'istanza di SQL Server.

4. Seguire le istruzioni per specificare le proprietà di connessione per il nuovo profilo di connessione. Dopo aver specificato ogni valore, premere **invio** per continuare. 

   | Impostazione       | Valore consigliato | Altre informazioni |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nome server** | Il nome completo del server | Se ci si connette a un server di Database SQL di Azure, il nome è nel formato: `<server_name>.database.windows.net`. |
   | **Nome database** | **SSISDB** | Il nome del database a cui connettersi. |
   | **Autenticazione** | Account di accesso SQL| Questa Guida rapida Usa autenticazione di SQL Server. |
   | **User name** | L'account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password (account di accesso SQL)** | La password per l'account di amministratore del server | Questa è la password specificata al momento della creazione del server. |
   | **Salva Password?** | Sì o No | Se non si desidera immettere la password ogni volta, selezionare Sì. |
   | **Immettere un nome per questo profilo** | Nome di un profilo, ad esempio **mySSISServer** | Nome di un profilo salvato velocità di connessione agli accessi successivi. | 

5. Premere il **ESC** tasto per chiudere il messaggio informativo che informa che il profilo viene creato e collegato.

6. Verificare la connessione nella barra di stato.

## <a name="run-the-t-sql-code"></a>Eseguire il codice T-SQL
Eseguire il seguente codice Transact-SQL per eseguire un pacchetto SSIS.

1. Nel **Editor** finestra, immettere la query seguente nella finestra query vuota. (Questo codice è il codice generato dal **Script** opzione il **Esegui pacchetto** nella finestra di dialogo di SQL Server Management Studio.)

2. Aggiornare i valori dei parametri di `catalog.create_execution` stored procedure per il sistema.

3. Premere **CTRL + MAIUSC + E** per eseguire il codice ed eseguire il pacchetto.

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
    - [Eseguire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

