---
title: 'Guida introduttiva: Connettersi ed eseguire query di un database SQL di Azure mediante Data Studio di Azure | Microsoft Docs'
description: Questa Guida introduttiva illustra come usare Azure Data Studio per connettersi a un database SQL ed eseguire una query
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 00ed5c02e423e5d51fd6f0ee3aabfc73a752e403
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038457"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Guida introduttiva: Usare [!INCLUDE[name-sos](../includes/name-sos-short.md)] connettersi ed eseguire query di database SQL di Azure

In questa guida introduttiva viene illustrato come utilizzare *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* per connettersi a un database SQL di Azure e quindi utilizzare istruzioni Transact-SQL (T-SQL) per creare il *TutorialDB* utilizzato [!INCLUDE[name-sos](../includes/name-sos-short.md)] esercitazioni.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa guida rapida, è necessario [!INCLUDE[name-sos](../includes/name-sos-short.md)] e un server SQL Azure.

- [Installare [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Se non si dispone già di un server SQL Azure, completare una delle seguenti guide rapide al database SQL di Azure (ricordare che il nome del server e le credenziali di accesso):

- [Creare un database - portale](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Creare un database - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Creare un database: PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Connettersi al server di Database SQL di Azure

Usare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per stabilire una connessione al server di Database SQL di Azure.

1. Alla prima esecuzione di [!INCLUDE[name-sos](../includes/name-sos-short.md)] viene mostrata la pagina **connessione**. Se essa non appare, fare clic sull'icona **Nuova connessione** nella barra laterale **SERVER**: 
   
   ![Nuova connessione](media/quickstart-sql-database/new-connection-icon.png)

2. Questo articolo usa *Account di accesso SQL*, ma l'accesso tramite *Autenticazione di Windows* è comunque supportato. Compilare i campi come indicato di seguito, specificando il nome del server, il nome utente e la password per il server Azure SQL usato: 

   | Impostazione       | Valore suggerito | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nome server** | Nome completo del server | Il nome deve essere simile al seguente: **nomeserver.database.Windows.NET** |
   | **Autenticazione** | Account di accesso SQL| In questa esercitazione viene utilizzata l'autenticazione di SQL. |
   | **Nome utente** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password (account di accesso SQL)** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |
   | **Salvare la password?** | Sì o No | Selezionare Sì se non si vuole immettere la password ogni volta. |
   | **Nome database** | *Lasciare vuoto* | Il nome del database a cui si desidera connettersi. |
   | **Gruppo di server** | Selezionare <Default> | Se è stato creato un gruppo di server, è possibile impostare per un gruppo di server specifico. | 

   ![Nuova connessione](media/quickstart-sql-database/new-connection-screen.png)  

3. Se il server non dispone di una regola firewall che consenta di Studio dei dati di Azure per la connessione, il **Crea nuova regola del firewall** viene aperto. Completare il modulo per creare una nuova regola firewall. Per informazioni dettagliate, vedere [Regole del firewall](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Nuova regola del firewall](media/quickstart-sql-database/firewall.png)  

4. Dopo avere stabilito la connessione al server, quest'ultimo appare nella barra laterale *server* .

## <a name="create-the-tutorial-database"></a>Creare il database dell'esercitazione

Nelle sezioni seguenti viene creato il database *TutorialDB* utilizzato in diverse esercitazioni su [!INCLUDE[name-sos](../includes/name-sos-short.md)].

1. Fare clic con il pulsante destro sul server SQL Azure nella barra laterale Server e selezionare **Nuova query.**

1. Incollare il seguente frammento di codice nell'editor di query, quindi fare clic su **Esegui**:

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



## <a name="create-a-table"></a>Creare una tabella

L'editor di query è ancora connesso al *master* database, ma si vuole creare una tabella sul database *TutorialDB*. 

1. Impostare il contesto di connessione su **TutorialDB**:

   ![Modifica del contesto](media/quickstart-sql-database/change-context.png)



1. Incollare il seguente frammento di codice nell'editor di query, quindi fare clic su **Esegui**:

   > [!NOTE]
   > È possibile aggiungere lo script o sovrascrivere la query precedente nell'editor. Si noti che il clic su **Esegui** esegue solo la query selezionata. Se nulla è selezionato, tutte le query presenti nel foglio vengono eseguite. Se nulla è selezionato, tutte le query presenti nel foglio vengono eseguite.

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


## <a name="insert-rows"></a>Inserire righe

- Incollare il seguente frammento di codice nell'editor di query, quindi fare clic su **Esegui**:

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


## <a name="view-the-result"></a>Visualizzare il risultato
1. Incollare il seguente frammento di codice nell'editor di query, quindi fare clic su **Esegui**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Vengono visualizzati i risultati della query:

   ![Selezionare i risultati](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>Pulire le risorse

Altri articoli in questa raccolta si basano su questa guida rapida. Se si prevede di continuare con le esercitazioni successive, non pulire le risorse create in questa guida rapida. Se non si prevede di continuare, utilizzare la procedura seguente per eliminare le risorse create nel portale di Azure.
Pulire le risorse eliminando i gruppi di risorse che non sono più necessari. Per informazioni dettagliate, vedere [Pulire le risorse](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Passaggi successivi

Ora che si è connessi correttamente a un database SQL di Azure e si sono eseguite query, provare l'[Esercitazione editor di codice](tutorial-sql-editor.md).
