---
title: Distribuire un progetto SSIS dal prompt dei comandi| Microsoft Docs
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
ms.openlocfilehash: 6c3e7f7e3fa870c7aa5b30a5a4a324f0cef7f6ba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Distribuire un progetto SSIS dal prompt dei comandi con ISDeploymentWizard.exe
Questa esercitazione introduttiva illustra come distribuire un progetto SSIS dal prompt dei comandi eseguendo la Distribuzione guidata Integration Services, `ISDeploymentWizard.exe`.

Per altre informazioni sulla procedura, vedere [Distribuzione guidata Integration Services](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Avviare la Distribuzione guidata Integration Services
1. Aprire la finestra del prompt dei comandi.

2. Eseguire `ISDeploymentWizard.exe`. Si apre la Distribuzione guidata Integration Services.

    Se la cartella che contiene `ISDeploymentWizard.exe` non si trova nella variabile di ambiente `path`, può essere necessario usare il comando `cd` per passare alla directory corrispondente. Per SQL Server 2017, questa cartella è in genere `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

## <a name="deploy-a-project-with-the-wizard"></a>Distribuire un progetto con la procedura guidata
1. Nella pagina **Introduzione** della procedura guidata leggere l'introduzione. Fare clic su **Avanti** per aprire la pagina **Seleziona origine**.

2. Nella pagina **Seleziona origine** selezionare il progetto SSIS esistente da distribuire.
    -   Per distribuire un file di distribuzione del progetto creato, selezionare **File distribuzione progetto** e immettere il percorso al file con estensione ispac.
    -   Per distribuire un progetto che si trova in un catalogo SSIS, selezionare **Catalogo di Integration Services**, quindi immettere il nome del server e il percorso del progetto nel catalogo.
    Fare clic su **Avanti** per visualizzare la pagina **Seleziona destinazione** .
  
3.  Nella pagina **Seleziona destinazione** selezionare la destinazione per il progetto.
    -   Immettere il nome completo del server. Se il server di destinazione è un server del database SQL di Azure, il nome è nel formato: `<server_name>.database.windows.net`.
    -   Fare clic su **Sfoglia** per selezionare la cartella di destinazione in SSISDB.
    Fare clic su **Avanti** per aprire la pagina **Verifica**.  
  
4.  Nella pagina **Verifica** rivedere le impostazioni selezionate.
    -   È possibile modificare le selezioni facendo clic su **Indietro**o selezionando un qualsiasi passaggio nel riquadro sinistro.
    -   Fare clic su **Distribuisci** per avviare il processo di distribuzione.
  
5.  Al termine del processo di distribuzione, si apre la pagina **Risultati**. Questa pagina consente di visualizzare l'esito positivo o negativo di ogni azione.
    -   Se l'azione non è stata completata correttamente, fare clic su **Non riuscito** nella colonna **Risultato** per visualizzare una spiegazione dell'errore.
    -   In alternativa, fare clic su **Salva report...** per salvare i risultati in un file XML.
    -   Per uscire dalla procedura guidata, fare clic su **Chiudi**.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per distribuire un pacchetto.
    - [Distribuire un pacchetto SSIS con SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Distribuire un pacchetto SSIS con PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Distribuire un pacchetto SSIS con C#](./ssis-quickstart-deploy-dotnet.md) 
- Eseguire un pacchetto distribuito. Per eseguire un pacchetto, è possibile scegliere tra diversi strumenti e linguaggi. Per altre informazioni, vedere gli articoli seguenti:
    - [Eseguire un pacchetto SSIS con SSMS](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
