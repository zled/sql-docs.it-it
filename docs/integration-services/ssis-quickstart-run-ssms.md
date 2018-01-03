---
title: Eseguire un pacchetto SSIS con SSMS | Microsoft Docs
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
ms.openlocfilehash: 53ad81ce3021f14e6d0638e7e60a050f892bb8bf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>Eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)
Questa guida introduttiva illustra come usare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi eseguire un pacchetto SSIS archiviato nel catalogo SSIS da Esplora oggetti in SSMS.

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al database SQL. Per altre informazioni su SSMS, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisites

Prima di iniziare, verificare di avere l'ultima versione di SQL Server Management Studio (SSMS). Per scaricare SSMS, vedere [Scaricare SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Usare SQL Server Management Studio per stabilire una connessione al catalogo SSIS. 

> [!NOTE]
> Un server di database SQL di Azure è in ascolto sulla porta 1433. Se si sta provando a connettersi a un server di database SQL di Azure dall'interno di un firewall aziendale, per stabilire correttamente la connessione questa porta deve essere aperta nel firewall aziendale.

1. Aprire SQL Server Management Studio.

2. Immettere le informazioni seguenti nella finestra di dialogo **Connetti al server**:

   | Impostazione       | Valore suggerito | Altre informazioni | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Nome completo del server | Se si sta eseguendo la connessione a un server di database SQL di Azure, il nome è nel formato `<server_name>.database.windows.net`. |
   | **Autenticazione** | autenticazione di SQL Server | In questa guida rapida viene usata l'autenticazione SQL. |
   | **Account di accesso** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |

3. Fare clic su **Connetti**. In SSMS si apre la finestra Esplora oggetti. 

4. In Esplora oggetti espandere **Cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="run-a-package"></a>Eseguire un pacchetto

1. In Esplora oggetti selezionare il pacchetto da eseguire.

2. Fare clic con il pulsante destro del mouse e selezionare **Esegui**. Viene visualizzata la finestra di dialogo **Esegui pacchetto**.

3.  Configurare l'esecuzione del pacchetto usando le impostazioni delle schede **Parametri**, **Gestioni connessioni** e **Avanzate** della finestra di dialogo Esegui pacchetto.

4.  Fare clic su OK per eseguire il pacchetto.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
