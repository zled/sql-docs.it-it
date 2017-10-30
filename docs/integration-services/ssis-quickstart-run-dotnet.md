---
title: Eseguire un progetto SSIS con codice di .NET (c#) | Documenti Microsoft
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
ms.openlocfilehash: 65a8db27af80e5cd7001e9a8777dde3c59e9c55e
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-c-code-in-a-net-app"></a>Eseguire un pacchetto SSIS con codice c# in un'app .NET
Questa esercitazione introduttiva illustra come scrivere codice c# per connettersi a un server di database ed eseguire un pacchetto SSIS.

Per creare un'app c#, è possibile utilizzare Visual Studio, Visual Studio Code o un altro strumento di propria scelta.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, verificare che è installato Visual Studio o Visual Studio Code. Scaricare l'edizione gratuita Community di Visual Studio o gratuita di Visual Studio Code, da [download di Visual Studio](https://www.visualstudio.com/downloads/).

> [!NOTE]
> Un server di Database SQL di Azure è in ascolto sulla porta 1433. Se si sta tentando di connettersi a un server di Database SQL di Azure all'interno di un firewall aziendale, questa porta deve essere aperta nel firewall aziendale per poter funzionare correttamente.

## <a name="get-the-connection-info-if-deployed-to-sql-database"></a>Ottenere le informazioni di connessione, se distribuite al Database SQL

Se i pacchetti vengono distribuiti a un Database di SQL Azure, è possibile ottenere le informazioni di connessione che necessarie per connettersi al database del catalogo SSIS (SSISDB). Sono necessarie le informazioni di accesso e del nome completo del server nelle procedure che seguono.

1. Accedere al [portale di Azure](https://portal.azure.com/).
2. Selezionare **database SQL** dal menu a sinistra e fare clic su database SSISDB il **database SQL** pagina. 
3. Nel **Panoramica** pagina per il database, controllare il nome completo del server. Per visualizzare il **fare clic per copiare** opzione, al passaggio del mouse sul nome del server. 
4. Se si dimenticano le informazioni di accesso del server Database SQL di Azure, passare alla pagina Database di SQL server per visualizzare il nome di amministratore del server. Se necessario, è possibile reimpostare la password.
5. Fare clic su **Mostra le stringhe di connessione di database**.
6. Esaminare l'intero **ADO.NET** stringa di connessione. Il codice di esempio utilizza un `SqlConnectionStringBuilder` per ricreare la stringa di connessione con i valori dei singoli parametri forniti.

## <a name="create-a-new-visual-studio-project"></a>Creare un nuovo progetto di Visual Studio

1. In Visual Studio, scegliere **File**, **New**, **progetto**. 
2. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#**.
3. Selezionare **App Console** e immettere *run_ssis_project* per il nome del progetto.
4. Fare clic su **OK** per creare e aprire il nuovo progetto in Visual Studio.

## <a name="add-references"></a>Aggiungere riferimenti
1. In Esplora soluzioni fare doppio clic su di **riferimenti** cartella e selezionare **Aggiungi riferimento**. Il **gestione riferimenti** verrà visualizzata la finestra di dialogo.
2. Nel **gestione riferimenti** finestra di dialogo espandere **assembly** e selezionare **estensioni**.
3. Selezionare i seguenti due riferimenti da aggiungere:
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. Fare clic su di **Sfoglia** pulsante per aggiungere un riferimento a **Microsoft.SqlServer.Management.IntegrationServices**. (Questo assembly è installato solo nella global assembly cache (GAC)). Il **selezionare i file di riferimento** verrà visualizzata la finestra di dialogo.
5. Nel **selezionare i file di riferimento** finestra di dialogo casella, passare alla cartella contenente l'assembly nella GAC. In genere questa cartella è `C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`.
6. Selezionare l'assembly (vale a dire il file con estensione dll) nella cartella e fare clic su **Aggiungi**.
7. Fare clic su **OK** per chiudere la **gestione riferimenti** finestra di dialogo e aggiungere i tre riferimenti. Per assicurarsi che i riferimenti esistono, controllare il **riferimenti** elenco in Esplora soluzioni.

## <a name="add-the-c-code"></a>Aggiungere il codice c# 
1. Aprire **Program.cs**.

2. Sostituire il contenuto di **Program.cs** con il codice seguente. Aggiungere i valori appropriati per il server, database, l'utente e password.

> [!NOTE]
> L'esempio seguente usa l'autenticazione di Windows. Per utilizzare l'autenticazione di SQL Server, sostituire il `Integrated Security=SSPI;` argomento con `User ID=<user name>;Password=<password>;`.


```csharp
using Microsoft.SqlServer.Management.IntegrationServices;
using System.Data.SqlClient;

namespace run_ssis_package
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string folderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string packageName = "Package.dtsx";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Get the folder
            CatalogFolder folder = catalog.Folders[folderName];

            // Get the project
            ProjectInfo project = folder.Projects[projectName];

            // Get the package
            PackageInfo package = project.Packages[packageName];

            // Run the package
            package.Execute(false, null);

        }
    }
}
```

## <a name="run-the-code"></a>Eseguire il codice

1. Per eseguire l'applicazione, premere **F5**.
2. Verificare che il pacchetto eseguito come previsto e quindi chiudere la finestra dell'applicazione.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)

