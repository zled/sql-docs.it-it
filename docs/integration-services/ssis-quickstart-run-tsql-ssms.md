---
title: Eseguire un pacchetto SSIS con Transact-SQL (SSMS) | Documenti Microsoft
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
ms.openlocfilehash: 1c656661f645ac9f5d1659800893290819525f39
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Eseguire un pacchetto SSIS da SSMS con Transact-SQL
Questa Guida introduttiva viene illustrato come utilizzare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi utilizzare istruzioni Transact-SQL per eseguire un pacchetto SSIS archiviato nel catalogo SSIS.

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al Database SQL. Per ulteriori informazioni su SQL Server Management Studio, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di che disporre della versione più recente di SQL Server Management Studio (SSMS). Per scaricare SQL Server Management Studio, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Utilizzare SQL Server Management Studio per stabilire una connessione al catalogo SSIS nel server di Database SQL di Azure. 

> [!NOTE]
> Un server di Database SQL di Azure è in ascolto sulla porta 1433. Se si sta tentando di connettersi a un server di Database SQL di Azure all'interno di un firewall aziendale, questa porta deve essere aperta nel firewall aziendale per poter funzionare correttamente.

1. Aprire SQL Server Management Studio.

2. Nel **Connetti al Server** finestra di dialogo immettere le informazioni seguenti:

   | Impostazione       | Valore consigliato | Altre informazioni | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Il nome completo del server | Se ci si connette a un server di Database SQL di Azure, il nome è nel formato: `<server_name>.database.windows.net`. |
   | **Autenticazione** | autenticazione di SQL Server | Questa Guida rapida Usa autenticazione di SQL Server. |
   | **Account di accesso** | L'account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | La password per l'account di amministratore del server | Questa è la password specificata al momento della creazione del server. |

3.  Fare clic su **Connetti**. Viene visualizzata la finestra di Esplora oggetti in SQL Server Management Studio.

4. In Esplora oggetti espandere **cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="run-a-package"></a>Eseguire un pacchetto
Eseguire il seguente codice Transact-SQL per eseguire un pacchetto SSIS.

1.  In SQL Server Management Studio, aprire una nuova finestra query e incollare il codice seguente. (Questo codice è il codice generato dal **Script** opzione il **Esegui pacchetto** nella finestra di dialogo di SQL Server Management Studio.)

2.  Aggiornare i valori dei parametri di `catalog.create_execution` stored procedure per il sistema.

3.  Assicurarsi che SSISDB è il database corrente.

4.  Eseguire lo script.

5. In Esplora oggetti, aggiornare il contenuto di **SSISDB** se necessario e controllo per il progetto distribuito.

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
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

