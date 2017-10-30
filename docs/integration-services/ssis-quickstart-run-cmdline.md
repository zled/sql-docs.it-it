---
title: Eseguire un pacchetto SSIS dal prompt dei comandi | Documenti Microsoft
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
ms.openlocfilehash: a33b8518ec3284f5de73d38c87209057dc1c7487
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Eseguire un pacchetto SSIS dal prompt dei comandi con DTExec.exe
In questa esercitazione introduttiva di seguito viene illustrato come eseguire un pacchetto SSIS dal prompt dei comandi eseguendo `DTExec.exe` con i parametri appropriati.

> [!NOTE]
> Il metodo descritto in questo articolo non è stato testato con i pacchetti distribuiti in un server di Database SQL di Azure.

Per ulteriori informazioni su `DTExec.exe`, vedere [utilità dtexec](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Eseguire un pacchetto con dtexec

Se la cartella che contiene `DTExec.exe` non si trova nel `path` variabile di ambiente, potrebbe essere necessario utilizzare il `cd` comando per passare alla directory. Per SQL Server 2017, questa cartella è in genere `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

Con i valori dei parametri utilizzati nell'esempio seguente, il programma viene eseguito il pacchetto nel percorso della cartella specificato nel server SSIS, vale a dire, il server che ospita il database di catalogo SSIS (SSISDB). Il `/Server` parametro fornisce il nome del server. Il programma si connette come l'utente corrente con l'autenticazione integrata di Windows. Per utilizzare l'autenticazione di SQL, specificare il `/User` e `Password` parametri con valori appropriati.

1. Aprire la finestra del prompt dei comandi.

2. Eseguire `DTExec.exe` e fornire i valori per almeno il `ISServer` e `Server` parametri, come illustrato nell'esempio seguente:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

