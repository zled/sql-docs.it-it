---
title: Eseguire un pacchetto SSIS con Transact-SQL (SSMS) | Microsoft Docs
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
ms.openlocfilehash: c4710f13f257f98326f0fa6c7f4550551bff3fd5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Eseguire un pacchetto SSIS da SSMS con Transact-SQL
Questa guida introduttiva illustra come usare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi usare istruzioni Transact-SQL per eseguire un pacchetto SSIS archiviato nel catalogo SSIS.

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al database SQL. Per altre informazioni su SSMS, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, verificare di avere l'ultima versione di SQL Server Management Studio (SSMS). Per scaricare SSMS, vedere [Scaricare SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Usare SQL Server Management Studio per stabilire una connessione al catalogo SSIS nel server di database SQL di Azure. 

> [!NOTE]
> Un server di database SQL di Azure è in ascolto sulla porta 1433. Se si sta provando a connettersi a un server di database SQL di Azure dall'interno di un firewall aziendale, per stabilire correttamente la connessione questa porta deve essere aperta nel firewall aziendale.

1. Aprire SQL Server Management Studio.

2. Immettere le informazioni seguenti nella finestra di dialogo **Connetti al server**:

   | Impostazione       | Valore suggerito | Altre informazioni | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Nome completo del server | Se si sta eseguendo la connessione a un server di database SQL di Azure, il nome è nel formato: `<server_name>.database.windows.net`. |
   | **Autenticazione** | autenticazione di SQL Server | In questa guida rapida viene usata l'autenticazione SQL. |
   | **Account di accesso** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |

3.  Fare clic su **Connetti**. In SSMS si apre la finestra Esplora oggetti.

4. In Esplora oggetti espandere **Cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="run-a-package"></a>Eseguire un pacchetto
Eseguire il codice Transact-SQL seguente per eseguire un pacchetto SSIS.

1.  In SSMS aprire una nuova finestra di query e incollare il codice seguente. Questo è il codice generato dall'opzione **Script** nella finestra di dialogo **Esegui pacchetto** di SSMS.

2.  Aggiornare i valori dei parametri nella stored procedure `catalog.create_execution` in base al sistema in uso.

3.  Verificare che SSISDB sia il database corrente.

4.  Eseguire lo script.

5. In Esplora oggetti aggiornare il contenuto di **SSISDB** se necessario e verificare la presenza del progetto distribuito.

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
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
