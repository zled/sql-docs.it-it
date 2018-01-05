---
title: 'Guida introduttiva: Connettersi ed eseguire query di SQL Server tramite Studio operazioni SQL (anteprima) | Documenti Microsoft'
description: Questa Guida introduttiva viene illustrato come utilizzare Studio operazioni SQL (anteprima) per connettersi a SQL Server ed eseguire una query
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7588368dcd64316551a9eaa72aeb8ce1d2ea67a6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Guida introduttiva: Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos](../includes/name-sos-short.md)]
Questa Guida introduttiva viene illustrato come utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per connettersi a SQL Server e quindi utilizzare istruzioni Transact-SQL (T-SQL) per creare il *TutorialDB* utilizzato [!INCLUDE[name-sos](../includes/name-sos-short.md)] esercitazioni.

## <a name="prerequisites"></a>Prerequisites

Per completare questa Guida rapida, è necessario [!INCLUDE[name-sos](../includes/name-sos-short.md)]e l'accesso a SQL Server.

- [Installare [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Se non si ha accesso a SQL Server, selezionare la piattaforma dai collegamenti seguenti (assicurarsi l'account di accesso SQL e la Password!):
- [Windows - Download SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - scaricare SQL Server 2017 in Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)
- [Linux - Download SQL Server 2017 Developer Edition](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-overview#install) -è necessario seguire i passaggi fino a *Create e eseguire query sui dati*.


## <a name="connect-to-a-sql-server"></a>Connettersi a SQL Server

   
1. Avviare  **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .
1. Alla prima esecuzione  *[!INCLUDE[name-sos](../includes/name-sos-short.md)]*  il **connessione** verrà visualizzata la finestra di dialogo. Se il **connessione** finestra di dialogo non viene aperto, fare clic su di **nuova connessione** icona nel **server** pagina:
   
   ![Nuova icona di connessione](media/quickstart-sql-server/new-connection-icon.png)

1. Questo articolo usa *account di accesso SQL*, ma *l'autenticazione di Windows* è supportato. Compilare i campi come indicato di seguito:
 
    - **Nome del server:** localhost
    - **Tipo di autenticazione:** account di accesso SQL  
    - **Nome utente:** nome utente per SQL Server  
    - **Password:** Password per il Server SQL  
    - **Nome del database:** lasciare vuoto questo campo 
    - **Gruppo di server:** \<predefinito\>  

   ![Nuova schermata di connessione](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>Creazione di un database

La seguente procedura crea un database denominato **TutorialDB**:

1. Fare clic con il pulsante destro sul server, **localhost**e selezionare **nuova Query.**
1. Nella finestra query, incollare il frammento di codice seguente: 

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

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```
1. Per eseguire la query, fare clic su **eseguire** .

Dopo il completamento della query, il nuovo **TutorialDB** viene visualizzato nell'elenco dei database. Se non è visualizzata, fare doppio clic su di **database** nodo e selezionare **aggiornamento**.


## <a name="create-a-table"></a>Creare una tabella

L'editor di query è ancora connesso al *master* database, ma si desidera creare una tabella di *TutorialDB* database. 

1. Modificare il contesto di connessione per **TutorialDB**:

   ![Contesto di modifica](media/quickstart-sql-server/change-context.png)



1. Nella finestra query, incollare il frammento di codice seguente:

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

Dopo il completamento della query, il nuovo **clienti** tabella viene visualizzata nell'elenco di tabelle. Potrebbe essere necessario fare il **TutorialDB > tabelle** nodo e selezionare **aggiornamento**.

## <a name="insert-rows"></a>Inserimento di righe

1. Nella finestra query, incollare il frammento di codice seguente:
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

1. Per eseguire la query, fare clic su **eseguire**.


## <a name="view-the-data-returned-by-a-query"></a>Visualizzare i dati restituiti da una query
1. Nella finestra query, incollare il frammento di codice seguente:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Per eseguire la query, fare clic su **eseguire**.

   ![Selezionare risultati](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Passaggi successivi
Ora che si è connessi correttamente SQL Server ed eseguire una query, provare il [esercitazione editor di codice](tutorial-sql-editor.md).


