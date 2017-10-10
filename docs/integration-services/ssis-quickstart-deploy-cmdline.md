---
title: Distribuire un progetto SSIS dal prompt dei comandi | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 0f1c7733f0ce6b132c209961a1fd12da80cbd282
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Distribuire un progetto SSIS dal prompt dei comandi con ISDeploymentWizard.exe
In questa esercitazione introduttiva viene illustrato come distribuire un progetto SSIS dal prompt dei comandi eseguendo la distribuzione guidata Integration Services, `ISDeploymentWizard.exe`.

Per ulteriori informazioni sulla distribuzione guidata di Integration Services, vedere [distribuzione guidata Integration Services](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Avviare la distribuzione guidata di Integration Services
1. Aprire la finestra del prompt dei comandi.

2. Eseguire `ISDeploymentWizard.exe`. Verrà visualizzata la distribuzione guidata di Integration Services.

    Se la cartella che contiene `ISDeploymentWizard.exe` non si trova nel `path` variabile di ambiente, potrebbe essere necessario utilizzare il `cd` comando per passare alla directory. Per SQL Server 2017, questa cartella è in genere `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

## <a name="deploy-a-project-with-the-wizard"></a>Distribuire un progetto con la procedura guidata
1. Nel **Introduzione** pagina della procedura guidata, rivedere l'introduzione. Fare clic su **Avanti** per aprire la **Seleziona origine** pagina.

2. Nel **Seleziona origine** pagina, selezionare il progetto SSIS esistente per la distribuzione.
    -   Per distribuire un file di distribuzione del progetto creato, selezionare **File distribuzione progetto** e immettere il percorso al file con estensione ispac.
    -   Per distribuire un progetto che si trova in un catalogo SSIS, selezionare **catalogo di Integration Services**, quindi immettere il nome del server e il percorso al progetto nel catalogo.
    Fare clic su **Avanti** per visualizzare la pagina **Seleziona destinazione** .
  
3.  Nel **Seleziona destinazione** pagina, selezionare la destinazione per il progetto.
    -   Immettere il nome completo del server. Se il server di destinazione è un server di Database SQL di Azure, il nome è nel formato: `<server_name>.database.windows.net`.
    -   Quindi fare clic su **Sfoglia** per selezionare la cartella di destinazione in SSISDB.
    Fare clic su **Avanti** per aprire la **revisione** pagina.  
  
4.  Nel **esaminare** pagina, rivedere le impostazioni selezionate.
    -   È possibile modificare le selezioni facendo clic su **Indietro**o selezionando un qualsiasi passaggio nel riquadro sinistro.
    -   Fare clic su **Distribuisci** per avviare il processo di distribuzione.
  
5.  Al termine del processo di distribuzione, il **risultati** verrà visualizzata la pagina. Questa pagina consente di visualizzare l'esito positivo o negativo di ogni azione.
    -   Se l'azione non riuscita, fare clic su **Failed** nel **risultato** colonna per visualizzare una spiegazione dell'errore.
    -   Facoltativamente, fare clic su **Salva Report...**  per salvare i risultati in un file XML.
    -   Fare clic su **Chiudi** chiudere la procedura guidata.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per distribuire un pacchetto.
    - [Distribuire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-deploy-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Distribuire un pacchetto SSIS con PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Distribuire un pacchetto SSIS con c#](./ssis-quickstart-deploy-dotnet.md) 
- Eseguire un pacchetto distribuito. Per eseguire un pacchetto, è possibile scegliere da numerosi strumenti e linguaggi. Per altre informazioni, vedere gli articoli seguenti:
    - [Eseguire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

