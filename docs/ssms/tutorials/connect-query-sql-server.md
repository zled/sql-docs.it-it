---
Title: 'Tutorial: Connect and Query SQL Server using SQL Server Management Studio'
description: Esercitazione per la connessione a SQL Server tramite SQL Server Management Studio ed esecuzione di query T-SQL di base.
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 7b389c5b58dc0afde077f70e2fd8bec7c6cac4d0
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-connect-and-query-sql-server-using-sql-server-management-studio"></a>Esercitazione: Connettersi ed eseguire query in SQL Server con SQL Server Management Studio
In questa esercitazione viene illustrato come usare SQL Server Management Studio (SSMS) per connettersi all'istanza di SQL Server ed eseguire alcuni comandi Transact-SQL (T-SQL) di base. Questo articolo illustra come eseguire le operazioni seguenti:
    - [Connettersi a SQL Server ](#connect-to-a-sql-server)
    - [Creare un nuovo database (**TutorialDB**)](#create-a-database)
    - [Creare una tabella (**Customers**) nel nuovo database](#create-a-table)
    - [Inserire righe nella nuova tabella **Customers**](#insert-rows)
    - [Eseguire query sulla tabella **Customers** e visualizzare i risultati](#view-query-results)
    - [Usare la tabella della finestra di query per verificare le proprietà di connessione](#verify-your-query-window-connection-properties)
    - [Modificare il server al quale è connessa la finestra di query](#change-server-connection-within-query-window)


## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, sono necessari SQL Server Management Studio e l'accesso a SQL Server. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

Se non si ha accesso a SQL Server, selezionare la piattaforma dai collegamenti seguenti. Assicurarsi di conoscere l'account di accesso e la password SQL se si decide di accedere tramite l'autenticazione SQL:
- [Windows - Scaricare SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - Scaricare SQL Server 2017 in Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)


## <a name="connect-to-a-sql-server"></a>Connettersi a SQL Server

1. Avviare SQL Server Management Studio (SSMS).
1. La prima volta che si esegue SSSM viene visualizzata la finestra di dialogo **Connetti al server**. 
      - Se la finestra di dialogo **Connetti al server** non si apre, è possibile aprirla manualmente in **Esplora oggetti** > **Connetti** (o l'icona a fianco) > **Motore di database**.

        ![Eseguire la connessione in Esplora oggetti](media/connect-query-sql-server/connectobjexp.png)

1. Nella finestra di dialogo **Connetti al server** compilare le opzioni di connessione: 

    - **Tipo server**: motore di database (in genere opzione selezionata per impostazione predefinita)
    - **Autenticazione**: autenticazione di Windows. In questo articolo viene usata l'autenticazione di Windows. È comunque supportata anche l'opzione Account di accesso SQL. Se selezionata, è necessario immettere nome utente e password.

      ![Connessione](media/connect-query-sql-server/connection.png)

        È possibile modificare anche le opzioni di connessione aggiuntive, ad esempio il database della connessione, il valore di timeout della connessione e il protocollo di rete, facendo clic sul pulsante **Opzioni**. Ai fini di questo articolo, sono stati lasciati i valori predefiniti. 

1. Dopo aver compilato i campi, fare clic su **Connetti**. 

1. Esplorare gli oggetti in **Esplora oggetti** per verificare se è stato possibile connettersi a SQL Server: 

   ![Connessione riuscita](media/connect-query-sql-server/successfulconnection.png)


## <a name="create-a-database"></a>Creare un database
La procedura seguente consente di creare un database denominato TutorialDB. 

1. Fare clic con il pulsante destro del mouse in  **Esplora oggetti** e scegliere **Nuova query**:

   ![Nuova query](media/connect-query-sql-server/newquery.png)
   
1. Incollare il frammento di codice T-SQL seguente nella finestra di query: 
   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
2. Per eseguire la query, fare clic su **Esegui** o premere F5 sulla tastiera. 

   ![Eseguire la query](media/connect-query-sql-server/execute.png)
  
 
Al termine della query, il nuovo database **TutorialDB** sarà visualizzato nell'elenco dei database in **Esplora oggetti**. Se il database non è visualizzato, fare clic con il pulsante destro del mouse sul nodo Database e selezionare **Aggiorna**.  


## <a name="create-a-table"></a>Creare una tabella
La procedura seguente consente di creare ora una tabella nel database **TutorialDB** appena creato. Si vuole creare una tabella nel database *TutorialDB*, ma l'editor di query è ancora nel contesto del database *master*. 

1. Modificare il contesto della connessione della query dal database master al database **TutorialDB** selezionando il database necessario dall'elenco a discesa dei database. 

   ![Modificare il database](media/connect-query-sql-server/changedb.png)

1. Incollare il frammento di codice T-SQL seguente nella finestra di query, evidenziarlo, fare clic su **Esegui** o premere F5 sulla tastiera: 
    - È possibile sostituire il testo esistente nella finestra di query o aggiungerlo alla fine. Se si vuole eseguire l'intero testo nella finestra di query, fare clic su **Esegui**. Se si vuole eseguire una parte del testo, evidenziare tale parte e fare clic su **Esegui**.  
  
   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
Al termine della query, la nuova tabella **Customers** sarà visualizzata nell'elenco delle tabelle in **Esplora oggetti**. Se la tabella non è visualizzata, fare clic con il pulsante destro del mouse sul nodo **TutorialDB > Tabelle** in **Esplora oggetti** e selezionare **Aggiorna**.

## <a name="insert-rows"></a>Inserire righe
Il passaggio seguente consente di inserire alcune righe nella tabella **Customers** creata in precedenza. 

Incollare il frammento di codice T-SQL seguente nella finestra di query e fare clic su **Esegui**: 


   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```

## <a name="view-query-results"></a>Visualizzare i risultati delle query
I risultati di una query vengono visualizzati sotto la finestra di testo della query. La procedura seguente consente di eseguire una query sulla tabella **Customers** e visualizzare le righe che sono state precedentemente inserite.  

1. Incollare il frammento di codice T-SQL seguente nella finestra di query e fare clic su **Esegui**: 

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```
1. I risultati della query vengono visualizzati al di sotto dell'area in cui il testo è stato immesso: 

   ![Risultati delle query](media/connect-query-sql-server/queryresults.png)


1.  È possibile modificare il formato di visualizzazione dei risultati selezionando una delle opzioni seguenti:

     ![risultati](media/connect-query-sql-server/results.png)

    - Per impostazione predefinita, i risultati sono disponibili in **Visualizzazione griglia**, ovvero il pulsante centrale e i risultati vengono visualizzati sotto forma di tabella. 
    - Il primo pulsante visualizza i risultati in **Visualizzazione testo**, come illustrato nell'immagine della sezione successiva.
    - Il terzo pulsante consente di salvare i risultati in un file, un file che termina con * ed estensione rpt per impostazione predefinita.

## <a name="verify-your-query-window-connection-properties"></a>Verificare le proprietà di connessione della finestra di query
È possibile trovare informazioni sulle proprietà di connessione tra i risultati della query. 
- Dopo aver eseguito la query specificata nel passaggio precedente, esaminare le proprietà di connessione nella parte inferiore della finestra di query.
    - È possibile determinare il server e il database ai quali ci si è connessi e l'utente che ha eseguito la connessione.
    - È anche possibile visualizzare la durata della query e il numero di righe restituite dalla query eseguita in precedenza.
    
    ![Proprietà di connessione](media/connect-query-sql-server/connectionproperties.png)  
    In questa immagine i risultati sono visualizzati in **Visualizzazione testo**.  

## <a name="change-server-connection-within-query-window"></a>Modificare la connessione al server nella finestra di query
È possibile modificare il server al quale la finestra di query corrente è connessa attenendosi alla procedura seguente.
1. Fare clic con il pulsante destro all'interno della finestra di query > Connessione > Cambia connessione.
2. Si aprirà nuovamente la finestra di dialogo **Connetti al server** in cui è possibile modificare il server al quale la query si connette. 
 
   ![Cambia connessione](media/connect-query-sql-server/changeconnection.png)
   - Si noti che in questo modo non si modifica il server al quale **Esplora oggetti** è connesso, ma solo la finestra di query corrente. 



