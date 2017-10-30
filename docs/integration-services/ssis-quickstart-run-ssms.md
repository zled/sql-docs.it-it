---
title: Eseguire un pacchetto SSIS con SQL Server Management Studio | Documenti Microsoft
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
ms.openlocfilehash: bbc17907311785ef98560493cb453b7b9b6d1556
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>Eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)
Questa Guida introduttiva viene illustrato come utilizzare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi eseguire un pacchetto SSIS archiviato nel catalogo SSIS da Esplora oggetti in SQL Server Management Studio.

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al Database SQL. Per ulteriori informazioni su SQL Server Management Studio, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di che disporre della versione più recente di SQL Server Management Studio (SSMS). Per scaricare SQL Server Management Studio, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Utilizzare SQL Server Management Studio per stabilire una connessione al catalogo SSIS. 

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

3. Fare clic su **Connetti**. Viene visualizzata la finestra di Esplora oggetti in SQL Server Management Studio. 

4. In Esplora oggetti espandere **cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="run-a-package"></a>Eseguire un pacchetto

1. In Esplora oggetti, selezionare il pacchetto che si desidera eseguire.

2. Mouse e scegliere **Execute**. Il **Esegui pacchetto** verrà visualizzata la finestra di dialogo.

3.  Configurare l'esecuzione del pacchetto tramite le impostazioni di **parametri**, **gestioni connessioni**, e **avanzate** schede nella finestra di dialogo Esegui pacchetto.

4.  Fare clic su OK per eseguire il pacchetto.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (codice di Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con PowerShell](ssis-quickstart-run-powershell.md)
    - [Eseguire un pacchetto SSIS con c#](./ssis-quickstart-run-dotnet.md) 

