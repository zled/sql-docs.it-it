---
title: Distribuire un progetto SSIS con Transact-SQL (SSMS) | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: e97fb20f5b0ee10aa3e5de690676b7e0bb797b4c
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Distribuire un progetto SSIS da SSMS con Transact-SQL

Questa Guida introduttiva viene illustrato come utilizzare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi utilizzare istruzioni Transact-SQL per distribuire un progetto SSIS nel catalogo SSIS. 

> [!NOTE]
> Il metodo descritto in questo articolo non è disponibile quando ci si connette a un server di Database SQL di Azure con SQL Server Management Studio. Il `catalog.deploy_project` stored procedura prevede il percorso di `.ispac` file nel file system locale (locale).

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al Database SQL. Per ulteriori informazioni su SQL Server Management Studio, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di che disporre della versione più recente di SQL Server Management Studio. Per scaricare SQL Server Management Studio, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssis-catalog-database"></a>Connettersi al database del catalogo SSIS

Utilizzare SQL Server Management Studio per stabilire una connessione al catalogo SSIS. 

> [!NOTE]
> Un server di Database SQL di Azure è in ascolto sulla porta 1433. Se si sta tentando di connettersi a un server di Database SQL di Azure all'interno di un firewall aziendale, questa porta deve essere aperta nel firewall aziendale per poter funzionare correttamente.

1. Aprire SQL Server Management Studio.

2. Nel **Connetti al Server** finestra di dialogo immettere le informazioni seguenti:

   | Impostazione       | Valore consigliato | Altre informazioni | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Il nome completo del server |  |
   | **Autenticazione** | autenticazione di SQL Server | Questa Guida rapida Usa autenticazione di SQL Server. |
   | **Account di accesso** | L'account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | La password per l'account di amministratore del server | Questa è la password specificata al momento della creazione del server. |

3. Fare clic su **Connetti**. Viene visualizzata la finestra di Esplora oggetti in SQL Server Management Studio. 

4. In Esplora oggetti espandere **cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="run-the-t-sql-code"></a>Eseguire il codice T-SQL
Eseguire il codice Transact-SQL seguente per distribuire un progetto SSIS.

1.  In SQL Server Management Studio, aprire una nuova finestra query e incollare il codice seguente.

2.  Aggiornare i valori dei parametri di `catalog.deploy_project` stored procedure per il sistema.

3.  Assicurarsi che SSISDB è il database corrente.

4.  Eseguire lo script.

5. In Esplora oggetti, aggiornare il contenuto di **SSISDB** se necessario e controllo per il progetto distribuito.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary =
    (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per distribuire un pacchetto.
    - [Distribuire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-deploy-ssms.md)
    - [Distribuire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Distribuire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-deploy-cmdline.md)
    - [Distribuire un pacchetto SSIS con PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Distribuire un pacchetto SSIS con c#](./ssis-quickstart-deploy-dotnet.md) 
- Eseguire un pacchetto distribuito. Per eseguire un pacchetto, è possibile scegliere da numerosi strumenti e linguaggi. Per altre informazioni, vedere gli articoli seguenti:
    - [Eseguire un pacchetto SSIS con SQL Server Management Studio](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

