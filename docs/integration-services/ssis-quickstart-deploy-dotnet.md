---
title: Distribuire un progetto SSIS con codice .NET (C#) | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7891a781a5874653eb7d4864529630d4d2a03442
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-an-ssis-project-with-c-code-in-a-net-app"></a>Distribuire un progetto SSIS con codice C# in un'app .NET
Questa esercitazione introduttiva illustra come scrivere codice C# per connettersi a un server di database e distribuire un progetto SSIS.

Per creare un'app C#, è possibile usare Visual Studio, Visual Studio Code o un altro strumento di propria scelta.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, verificare che Visual Studio o Visual Studio Code sia installato. Scaricare l'edizione Community gratuita di Visual Studio o lo strumento gratuito Visual Studio Code dalla pagina dei [download di Visual Studio](https://www.visualstudio.com/downloads/).

> [!NOTE]
> Un server di database SQL di Azure è in ascolto sulla porta 1433. Se si sta provando a connettersi a un server di database SQL di Azure dall'interno di un firewall aziendale, per stabilire correttamente la connessione questa porta deve essere aperta nel firewall aziendale.

## <a name="get-the-connection-info-if-deployed-to-sql-database"></a>Ottenere le informazioni di connessione se la distribuzione viene eseguita al database SQL 

Se i pacchetti vengono distribuiti a un database SQL di Azure, ottenere le informazioni di connessione necessarie per connettersi al database del catalogo SSIS (SSISDB). Nelle procedure che seguono sono necessari il nome completo del server e le informazioni di accesso.

1. Accedere al [portale di Azure](https://portal.azure.com/).
2. Selezionare **Database SQL** dal menu a sinistra e fare clic sul database SSIDB nella pagina dei **database SQL**. 
3. Nella pagina **Panoramica** del database controllare il nome completo del server. Passare il mouse sul nome del server per visualizzare l'opzione **Fare clic per copiare**. 
4. Se si dimenticano le informazioni di accesso del server di database SQL di Azure, passare alla pagina del server di database SQL per visualizzare il nome amministratore del server. Se necessario, è possibile reimpostare la password.
5. Fare clic su **Mostra stringhe di connessione del database**.
6. Esaminare l'intera stringa di connessione **ADO.NET**. L'esempio di codice usa `SqlConnectionStringBuilder` per ricreare questa stringa di connessione con i valori dei singoli parametri specificati.

## <a name="create-a-new-visual-studio-project"></a>Creare un nuovo progetto Visual Studio

1. In Visual Studio scegliere **File**, **Nuovo**, **Progetto**. 
2. Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#**.
3. Selezionare **Applicazione console** e immettere *deploy_ssis_project* come nome del progetto.
4. Fare clic su **OK** per creare e aprire il nuovo progetto in Visual Studio.

## <a name="add-references"></a>Aggiungere riferimenti
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Riferimenti** e selezionare **Aggiungi riferimento**. Viene visualizzata la finestra di dialogo **Gestione riferimenti**.
2. Nella finestra di dialogo **Gestione riferimenti** espandere **Assembly** e selezionare **Estensioni**.
3. Selezionare i seguenti due riferimenti da aggiungere:
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. Fare clic sul pulsante **Sfoglia** per aggiungere un riferimento a **Microsoft.SqlServer.Management.IntegrationServices**. Questo assembly viene installato nella Global Assembly Cache (GAC). Viene visualizzata la finestra di dialogo **Selezionare i file a cui fare riferimento**.
5. Nella finestra di dialogo **Selezionare i file a cui fare riferimento** passare alla cartella che contiene l'assembly nella GAC. In genere questa cartella è `C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`.
6. Selezionare l'assembly, ovvero il file DLL, nella cartella e fare clic su **Aggiungi**.
7. Fare clic su **OK** per chiudere la finestra di dialogo **Gestione riferimenti** e aggiungere i tre riferimenti. Per verificare se i riferimenti sono presenti, controllare l'elenco **Riferimenti** in Esplora soluzioni.

## <a name="add-the-c-code"></a>Aggiungere il codice C# 
1. Aprire **Program.cs**.

2. Sostituire il contenuto di **Program.cs** con il codice seguente. Aggiungere i valori appropriati per server, database, utente e password.

> [!NOTE]
> L'esempio seguente usa l'autenticazione di Windows. Per usare l'autenticazione di SQL Server, sostituire l'argomento `Integrated Security=SSPI;` con `User ID=<user name>;Password=<password>;`.

```csharp
using Microsoft.SqlServer.Management.IntegrationServices;
using System;
using System.Data.SqlClient;
using System.IO;

namespace deploy_ssis_project
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string targetFolderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string projectFilePath = @"C:\Projects\Integration Services Project1\Integration Services Project1\bin\Development\Integration Services Project1.ispac";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Create the target folder
            CatalogFolder folder = new CatalogFolder(catalog,
                targetFolderName, "Folder description");
            folder.Create();

            Console.WriteLine("Deploying " + projectName + " project.");

            byte[] projectFile = File.ReadAllBytes(projectFilePath);
            folder.DeployProject(projectName, projectFile);

            Console.WriteLine("Done.");
        }
    }
}
```

## <a name="run-the-code"></a>Eseguire il codice

1. Premere **F5** per eseguire l'applicazione.
2. In SQL Server Management Studio verificare che il progetto sia stato distribuito.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per distribuire un pacchetto.
    - [Distribuire un pacchetto SSIS con SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Distribuire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-deploy-cmdline.md)
    - [Distribuire un pacchetto SSIS con PowerShell](ssis-quickstart-deploy-powershell.md)
- Eseguire un pacchetto distribuito. Per eseguire un pacchetto, è possibile scegliere tra diversi strumenti e linguaggi. Per altre informazioni, vedere gli articoli seguenti:
    - [Eseguire un pacchetto SSIS con SSMS](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
