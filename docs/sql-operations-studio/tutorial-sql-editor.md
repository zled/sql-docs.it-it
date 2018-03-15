---
title: 'Esercitazione: Usare l''editor Transact-SQL Studio operazioni SQL (anteprima) per creare oggetti di database | Documenti Microsoft'
description: "Questa esercitazione illustra le funzionalità principali in Studio operazioni SQL (anteprima) che semplificano l'uso di T-SQL."
ms.custom: tools|sos
ms.date: 03/13/2018
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
ms.openlocfilehash: db9cc8185742980b649f9fcc11eced5687201464
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>Esercitazione: Usare l'editor Transact-SQL per creare oggetti di database- [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Creazione ed esecuzione di query, stored procedure, script, e così via sono le attività principali dei professionisti di database. Questa esercitazione illustra le funzionalità chiave nell'editor T-SQL per creare oggetti di database.

In questa esercitazione imparare a usare [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] per:
> [!div class="checklist"]
> * Oggetti di database di ricerca
> * Modificare i dati di tabella 
> * Usare i frammenti di codice per scrivere rapidamente T-SQL
> * Visualizzare i dettagli dell'oggetto database con *Visualizza definizione* e *Vai a definizione*


## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>Un oggetto di database di individuare rapidamente e di eseguire un'attività comune

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] fornisce un widget di ricerca per trovare rapidamente gli oggetti di database. L'elenco dei risultati fornisce un menu di scelta rapida per le attività comuni relative all'oggetto selezionato, ad esempio *modifica dati* per una tabella.

1. Aprire il riquadro Server (**Ctrl + G**), espandere **database**e selezionare **TutorialDB**. 

1. Aprire il *TutorialDB Dashboard* facendo **TutorialDB** e selezionando **Gestisci** dal menu di scelta rapida:

   ![menu di scelta rapida - gestire](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. Nel dashboard, fare doppio clic su **dbo. I clienti** (nel widget di ricerca) e selezionare **modifica dati**.
   
   > [!TIP]
   > Per i database con molti oggetti, usare il widget di ricerca per individuare rapidamente la tabella, vista, e così via che si sta cercando.

   ![widget di ricerca rapida](./media/tutorial-sql-editor/quick-search-widget.png)

1. Modificare il **posta elettronica** colonna nella prima riga, di tipo  *orlando0@adventure-works.com* e premere **invio** per salvare le modifiche.

   ![modificare i dati](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>Usare i frammenti di codice T-SQL per creare stored procedure

Operazioni SQL Studio fornisce diversi frammenti di codice T-SQL incorporati per la creazione rapida di istruzioni.


1. Aprire un nuovo editor di query premendo **Ctrl + N**.

2. Tipo **sql** nell'editor, sulla freccia verso il basso per **sqlCreateStoredProcedure**e premere il *scheda* chiave (o *invio*) per caricare la creazione archiviata frammento di stored procedure.

   ![snippet-list](./media/tutorial-sql-editor/snippet-list.png)

3. Il frammento di stored procedure crea include due campi impostato per la modifica rapida, *StoredProcedureName* e *SchemaName*. Selezionare *StoredProcedureName*, pulsante destro del mouse e selezionare **Modifica tutte le occorrenze**. A questo punto digitare *getCustomer* e tutte le *StoredProcedureName* le voci delle modifiche per *getCustomer*.

   ![snippet](./media/tutorial-sql-editor/snippet.png)

5. Modificare tutte le occorrenze di *SchemaName* a *dbo*. 
6. Il frammento contiene parametri di segnaposto e testo del corpo da aggiornare. Il *EXECUTE* istruzione contiene inoltre il testo segnaposto perché non conoscere il numero di parametri avrà la procedura. Per questa esercitazione il frammento di codice di aggiornamento pertanto risulta simile al codice seguente:

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
    SELECT  c.CustomerId, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerId = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. Per creare la stored procedure e assegnargli un'esecuzione dei test, premere **F5**.

A questo punto viene creata la stored procedure e **risultati** riquadro viene visualizzato il cliente restituito in JSON. Per visualizzare JSON formattato, fare clic sul record restituito. 


## <a name="use-peek-definition"></a>Utilizzare Visualizza definizione 

Operazioni SQL Studio fornisce la possibilità di visualizzare una definizione di oggetti utilizzando la funzionalità di definizione della visualizzazione. In questa sezione viene creata una seconda stored procedure e utilizza finestra Visualizza definizione per vedere quali sono le colonne in una tabella per creare rapidamente il corpo della stored procedure.

1. Aprire un nuovo editor premendo **Ctrl + N**. 

2. Tipo *sql* nell'editor, sulla freccia verso il basso per *sqlCreateStoredProcedure*e premere il *scheda* chiave (o *invio*) per caricare la creazione archiviata frammento di stored procedure.
3. Digitare *setCustomer* per *StoredProcedureName* e *dbo* per *SchemaName*

3. Sostituire il @param segnaposto con la definizione di parametro seguente:

   ```sql
   @json_val nvarchar(max)
   ```

4. Sostituire il corpo della stored procedure con il codice seguente:
   ```sql
   INSERT INTO dbo.Customers
   ```

5. Nel *inserire* si riga appena aggiunta rapida **dbo. I clienti** e selezionare **Visualizza definizione**.

   ![Visualizza definizione](./media/tutorial-sql-editor/peek-definition.png)

6. La definizione della tabella viene visualizzata in modo è possibile visualizzare rapidamente le colonne presenti nella tabella. Fare riferimento all'elenco delle colonne di completare facilmente le istruzioni per la stored procedure. Completare la creazione dell'istruzione INSERT per completare il corpo della stored procedure e chiudere la finestra di definizione visualizzazione aggiunto in precedenza:

   ```sql
   INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
    )
   ```
7. Eliminare (o impostare come commento) i *EXECUTE* comando nella parte inferiore della query.
8. L'intera istruzione dovrebbe essere simile al codice seguente:

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
       INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. Per creare il *setCustomer* stored procedure, premere **F5**.

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>Utilizzare salvare i risultati della query come JSON per testare la procedura setCustomer archiviati

Il *setCustomer* stored procedure creata nella sezione precedente richiede JSON i dati di essere passati nel  *@json_val*  parametro. In questa sezione viene illustrato come ottenere un bit di JSON per passare il parametro in modo è possibile testare la stored procedure formattato correttamente.

1. Nel **server** barra laterale destro la *dbo. I clienti* tabella e fare clic su **seleziona le prime 1000 righe**.

2. Selezionare la prima riga nella visualizzazione dei risultati, verificare che sia selezionata l'intera riga (scegliere il numero 1 nella colonna più a sinistra) e selezionare **salvare come JSON**.  
3. Modificare la cartella in un percorso di ricordare che consente di eliminare il file in un secondo momento (per desktop di esempio) e fare clic su **salvare**. Apertura del file di formato di JSON.

   ![salvare in formato JSON](./media/tutorial-sql-editor/save-as-json.png)

4. Selezionare i dati JSON nell'editor e copiarlo.
5. Aprire un nuovo editor premendo **Ctrl + N**.
6. Nei passaggi precedenti viene illustrato come è possibile ottenere facilmente i dati formattati correttamente per completare la chiamata al *setCustomer* procedura. È possibile visualizzare il codice seguente usa lo stesso formato JSON con nuovi dettagli customer in modo sia possibile testare il *setCustomer* procedura. L'istruzione include la sintassi per dichiarare il parametro ed eseguire di nuovo get e set di procedure. È possibile incollare i dati copiati dalla sezione precedente e modificarlo in modo identico nell'esempio seguente è o semplicemente incollare l'istruzione seguente nell'editor di query.

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerId": 5,
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


Per informazioni su come abilitare il **cinque query più lente** widget, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Abilitare il widget di informazioni dettagliate di esempio le query lente](tutorial-qds-sql-server.md)
