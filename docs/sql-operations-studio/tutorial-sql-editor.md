---
title: 'Esercitazione: Usare l''editor Transact-SQL Studio operazioni SQL (anteprima) per creare oggetti di database | Documenti Microsoft'
description: "Questa esercitazione illustra le funzionalità principali in Studio operazioni SQL (anteprima) che semplificano l'uso di T-SQL."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2754a998963be5a25d00aa58dcb9b4105bb8f37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Esercitazione: Usare l'editor Transact-SQL per creare oggetti di database-[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Creazione ed esecuzione di query, stored procedure, script, e così via sono le attività principali dei professionisti di database. Questa esercitazione illustra le funzionalità chiave nell'editor T-SQL per creare oggetti di database.

In questa esercitazione imparare a usare [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] per:
> [!div class="checklist"]
> * Oggetti di database di ricerca
> * Modificare i dati di tabella 
> * Usare i frammenti di codice per scrivere rapidamente T-SQL
> * Visualizzare i dettagli dell'oggetto database con *Visualizza definizione* e *Vai a definizione*


## <a name="prerequisites"></a>Prerequisites

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Un oggetto di database di individuare rapidamente e di eseguire un'attività comune

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]fornisce un widget di ricerca per trovare rapidamente gli oggetti di database. L'elenco dei risultati fornisce un menu di scelta rapida per le attività comuni relative all'oggetto selezionato, ad esempio *modifica dati* per una tabella.

1. Aprire il riquadro Server (**Ctrl + G**), espandere **database**e selezionare **TutorialDB**. 

1. Aprire il *TutorialDB Dashboard* selezionando **Gestisci** dal menu di scelta rapida.

   ![menu di scelta rapida - gestire](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Individuare il *clienti* tabella digitando *cus* nel widget di ricerca.
1. Fare doppio clic su **dbo. I clienti** e selezionare **modificare dati**.

   ![widget di ricerca rapida](./media/tutorial-sql-editor/quick-search-widget.png)

1. Modificare il **posta elettronica** colonna nella prima riga, di tipo  *orlando0@adventure-works.com* e premere **invio** per salvare le modifiche.

   ![modificare i dati](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-a-stored-procedure"></a>Usare i frammenti di codice T-SQL per creare una stored procedure

### <a name="use-snippets-in-includename-sos-shortincludesname-sos-shortmd"></a>Usare i frammenti di codice in[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]

1. Aprire un nuovo editor di query premendo **Ctrl + N**.

2. Tipo **sql** nell'editor, sulla freccia verso il basso per **sqlCreateStoredProcedure**, premere il *scheda* tasto per caricare il nuovo frammento di codice di stored procedure.

   ![elenco dei frammenti](./media/tutorial-sql-editor/snippet-list.png)

3. Tipo *getCustomer* e tutte le *StoredProcedureName* le voci delle modifiche per *getCustomer*. 

   ![Frammento di codice](./media/tutorial-sql-editor/snippet.png)

4. Sostituire il resto della stored procedure con T-SQL riportata di seguito:

    ```sql
    -- Create a new stored procedure called 'getCustomer' in schema 'dbo'
    -- Drop the stored procedure if it already exists
    IF EXISTS (
    SELECT *
    FROM INFORMATION_SCHEMA.ROUTINES
    WHERE SPECIFIC_SCHEMA = N'dbo'
    AND SPECIFIC_NAME = N'getCustomer'
    )
    DROP PROCEDURE dbo.getCustomer
    GO
    -- Create the stored procedure in the specified schema
    CREATE PROCEDURE dbo.getCustomer
    @ID int
    -- add more stored procedure parameters here
    AS
    -- body of the stored procedure
    SELECT  c.CustomerID, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerID = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Per creare la stored procedure e assegnargli un'esecuzione dei test, premere **F5**.

## <a name="use-peek-definition-and-go-to-definition"></a>Vai a definizione e utilizzare Visualizza definizione 

1. Aprire un nuovo editor premendo **Ctrl + N**. 

2. Digitare, quindi selezionare **sqlCreateStoredProcedure** dall'elenco di suggerimenti frammento di codice. Digitare **setCustomer** per **StoredProcedureName** e **dbo** per **SchemaName**

3. Sostituire il @param righe con la definizione dei parametri seguenti:

   ```sql
       @json_val nvarchar(max)
   ```

4. Sostituire il corpo della stored procedure con gli elementi seguenti:
   ```sql
   -- body of the stored procedure
   INSERT INTO dbo.Customers
   ```

5. Fare doppio clic su **dbo. I clienti** e selezionare **Visualizza definizione**.

   ![Visualizza definizione](./media/tutorial-sql-editor/peek-definition.png)

6. Utilizzare la definizione della tabella per completare l'istruzione insert seguente:

   ```sql
   INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
   ```
7. L'istruzione finale deve essere:

   ```sql
   -- Create a new stored procedure called 'setCustomer' in schema 'dbo'
   -- Drop the stored procedure if it already exists
   IF EXISTS (
   SELECT *
       FROM INFORMATION_SCHEMA.ROUTINES
       WHERE SPECIFIC_SCHEMA = N'dbo'
       AND SPECIFIC_NAME = N'setCustomer'
   )
   DROP PROCEDURE dbo.setCustomer
   GO
   -- Create the stored procedure in the specified schema
   CREATE PROCEDURE dbo.setCustomer
       @json_val nvarchar(max) 
   AS
       -- body of the stored procedure
       INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Per eseguire lo script, premere **F5**.

## <a name="use-save-query-results-as-json-to-test-our-stored-procedure"></a>Utilizzare salvare i risultati della query come JSON per testare la stored procedure

1. **Seleziona le prime 1000 righe** dal *dbo. I clienti* tabella.

2. Selezionare la prima riga nella visualizzazione risultati e fare clic su **salvare come JSON**.  
3. Fare clic su **salvare**, e si apre la riga evidenziata in formato JSON.

   ![salvare in formato JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Selezionare i dati JSON e copiarlo.

5. Aprire una nuova query per *TutorialDB* e completare il seguente script di test utilizzando i dati JSON come modello del passaggio precedente. Modificare i valori per *CustomerID*, *nome*, *percorso*, e *posta elettronica*.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerID": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. Eseguire lo script premendo **F5**. Lo script inserisce un nuovo cliente e restituisce le nuove informazioni sul cliente in formato JSON. Fare clic sul risultato per aprire una visualizzazione formattata.

   ![Risultato del test](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Oggetti dello schema di ricerca rapida
> * Modificare i dati di tabella 
> * Scrittura dello script T-SQL utilizzando i frammenti di codice
> * Informazioni sui dettagli di oggetti di database utilizzando Visualizza definizione e Vai a definizione


Per informazioni su come abilitare il **cinque query più lente** esempio informazioni dettagliate, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Abilitare il widget di informazioni dettagliate di esempio le query lente](tutorial-qds-sql-server.md)
