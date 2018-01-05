---
title: 'Guida introduttiva: Connettersi ed eseguire query di un database SQL di Azure mediante Studio operazioni SQL (anteprima) | Documenti Microsoft'
description: Questa Guida introduttiva viene illustrato come utilizzare Studio operazioni SQL (anteprima) per connettersi a un database SQL ed eseguire una query
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
ms.openlocfilehash: d0e2d48ed411f883a904decce5d836dde7aaa41b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Guida introduttiva: Utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per connettersi ed eseguire query di database SQL di Azure

Questa Guida introduttiva viene illustrato come utilizzare  *[!INCLUDE[name-sos](../includes/name-sos-short.md)]*  per connettersi a un database SQL di Azure e quindi utilizzare istruzioni Transact-SQL (T-SQL) per creare il *TutorialDB* utilizzato [!INCLUDE[name-sos](../includes/name-sos-short.md)] esercitazioni.

## <a name="prerequisites"></a>Prerequisites

Per completare questa Guida rapida, è necessario [!INCLUDE[name-sos](../includes/name-sos-short.md)]e un server SQL Azure.

- [Installare [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Se si dispone già di un server SQL Azure, completare una delle seguenti Guide rapide a Database SQL di Azure (occorre ricordare che il nome del server e le credenziali di accesso!):

- [Creare DB - portale](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Creare DB - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Creare DB - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Connettersi al server di Database SQL di Azure

Utilizzare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per stabilire una connessione al server di Database SQL di Azure.

1. Alla prima esecuzione [!INCLUDE[name-sos](../includes/name-sos-short.md)] il **connessione** pagina. Se il **connessione** pagina non viene visualizzata, fare clic sul **nuova connessione** sull'icona di **server** barra laterale:
   
   ![Nuova icona di connessione](media/quickstart-sql-database/new-connection-icon.png)

2. Questo articolo usa *account di accesso SQL*, ma *l'autenticazione di Windows* è anche supportato. Compilare i campi come indicato di seguito:

   | Impostazione       | Valore suggerito | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nome server** | Nome completo del server | Il nome deve essere simile al seguente: **servername.database.windows.net** |
   | **Autenticazione** | Account di accesso SQL| In questa esercitazione viene utilizzata l'autenticazione di SQL. |
   | **User name** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password (account di accesso SQL)** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |
   | **Salvare la password?** | Sì o No | Selezionare Sì se non si desidera immettere la password ogni volta. |
   | **Nome database** | *lasciare vuoto* | Il nome del database a cui si desidera connettersi. |
   | **Gruppo di server** | Selezionare<Default> | Se è stato creato un gruppo di server, è possibile impostare per un gruppo di server specifico. | 

   ![Nuova icona di connessione](media/quickstart-sql-database/new-connection-screen.png)  

3. Se si verifica un errore su firewall, è necessario creare una regola del firewall. Per creare una regola del firewall, vedere [regole del Firewall](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

4. Dopo avere stabilito la connessione del server verrà visualizzato nel *server* barra laterale.

## <a name="create-the-tutorial-database"></a>Creare il database dell'esercitazione

Il *TutorialDB* database viene utilizzato in diversi [!INCLUDE[name-sos](../includes/name-sos-short.md)] esercitazioni.

1. Fare clic con il pulsante destro sul server SQL Azure nella barra laterale di server e selezionare **nuova Query.**

1. Incollare il frammento seguente nell'editor di query.

   ```sql
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

1. Per eseguire la query, fare clic su **eseguire**.


## <a name="create-a-table"></a>Creare una tabella

L'editor di query è ancora connesso al *master* database, ma si desidera creare una tabella di *TutorialDB* database. 

1. Modificare il contesto di connessione per **TutorialDB**:

   ![Contesto di modifica](media/quickstart-sql-database/change-context.png)



1. Incollare il frammento seguente nell'editor di query.

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
1. Per eseguire la query, fare clic su **eseguire**.

## <a name="insert-rows"></a>Inserimento di righe

1. Incollare il seguente frammento di codice nell'editor di query:
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

## <a name="view-the-result"></a>Visualizzare il risultato
1. Incollare il frammento seguente nell'editor di query.

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Per eseguire la query, fare clic su **eseguire**.

   ![Selezionare risultati](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>Pulire le risorse

Altri articoli in questa raccolta si basano su questa Guida rapida. Se si prevede di continuare a lavorare con guide rapide successive, non pulire le risorse create in questa Guida rapida. Se non si prevede di continuare, utilizzare la procedura seguente per eliminare le risorse create da questa Guida rapida nel portale di Azure.
Pulire le risorse eliminando i gruppi di risorse che non è più necessario. Per informazioni dettagliate, vedere [pulire le risorse](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Passaggi successivi

Ora che si è connessi correttamente a un database SQL di Azure ed è stata eseguita una query, provare il [esercitazione editor di codice](tutorial-sql-editor.md).
