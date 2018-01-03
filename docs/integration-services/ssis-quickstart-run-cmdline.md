---
title: Eseguire un pacchetto SSIS dal prompt dei comandi | Microsoft Docs
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
ms.openlocfilehash: 8d5c64fa4ba32ebd9e95d728b3a7655b523d9627
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Eseguire un pacchetto SSIS dal prompt dei comandi con DTExec.exe
Questa esercitazione introduttiva illustra come eseguire un pacchetto SSIS dal prompt dei comandi eseguendo `DTExec.exe` con i parametri appropriati.

> [!NOTE]
> Il metodo descritto in questo articolo non è stato testato con i pacchetti distribuiti in un server di database SQL di Azure.

Per altre informazioni su `DTExec.exe`, vedere [Utilità dtexec](https://docs.microsoft.com/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Eseguire un pacchetto con dtexec

Se la cartella che contiene `DTExec.exe` non si trova nella variabile di ambiente `path`, può essere necessario usare il comando `cd` per passare alla directory corrispondente. Per SQL Server 2017 questa cartella è in genere `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

Con i valori dei parametri usati nell'esempio seguente, il programma esegue il pacchetto nel percorso della cartella specificato nel server SSIS, ovvero il server che ospita il database del catalogo SSIS (SSISDB). Il parametro `/Server` specifica il nome del server. Il programma si connette come utente corrente con l'autenticazione integrata di Windows. Per usare l'autenticazione SQL, specificare i parametri `/User` e `Password` con i valori appropriati.

1. Aprire la finestra del prompt dei comandi.

2. Eseguire `DTExec.exe` e specificare i valori almeno per i parametri `ISServer` e `Server`, come illustrato nell'esempio seguente:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con SSMS](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
