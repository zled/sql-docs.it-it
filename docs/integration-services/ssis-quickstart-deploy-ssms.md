---
title: Distribuire un progetto SSIS con SQL Server Management Studio | Documenti Microsoft
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
ms.openlocfilehash: b9729343ab14563ee6264795d6f098f3c22e91bf
ms.contentlocale: it-it
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-with-sql-server-management-studio-ssms"></a>Distribuire un progetto SSIS con SQL Server Management Studio (SSMS)
Questa Guida introduttiva viene illustrato come utilizzare SQL Server Management Studio (SSMS) per connettersi al database del catalogo SSIS e quindi eseguire la distribuzione guidata di Integration Services per distribuire un progetto SSIS nel catalogo SSIS. 

SQL Server Management Studio è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al Database SQL. Per ulteriori informazioni su SQL Server Management Studio, vedere [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di che disporre della versione più recente di SQL Server Management Studio. Per scaricare SQL Server Management Studio, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

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

## <a name="start-the-integration-services-deployment-wizard"></a>Avviare la distribuzione guidata di Integration Services
1. In Esplora oggetti, con la **cataloghi di Integration Services** nodo e **SSISDB** espansa, espandere una cartella di progetto.

2.  Selezionare il **progetti** nodo.

3.  Fare clic su di **progetti** nodo e selezionare **Distribuisci progetto**. Verrà visualizzata la distribuzione guidata di Integration Services. È possibile distribuire un progetto dal catalogo corrente o dal file system.

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
    -   Facoltativamente, fare clic su **Salva Report... ** per salvare i risultati in un file XML.
    -   Fare clic su **Chiudi** chiudere la procedura guidata.

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per distribuire un pacchetto.
    - [Distribuire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
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

