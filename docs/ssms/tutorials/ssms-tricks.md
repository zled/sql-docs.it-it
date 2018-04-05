---
Title: 'Tutorial: Additional Tips and Tricks for using SSMS'
description: 'Esercitazione che illustra suggerimenti e consigli aggiuntivi per usare SSMS. '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
ms.openlocfilehash: 792d6c7fe69a1b8ec77c70d0fbfa6ceaa92d808a
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>Esercitazione: Suggerimenti e consigli per l'uso di SSMS
Questa esercitazione offre alcuni suggerimenti aggiuntivi per l'uso di SQL Server Management Studio. In questo articolo viene illustrato come eseguire quanto segue: 

> [!div class="checklist"]
> * Inserire e rimuovere commenti nel testo Transact-SQL (T-SQL)
> * Impostare un rientro del testo
> * Filtrare oggetti in Esplora oggetti
> * Accedere al log degli errori di SQL Server
> * Trovare il nome dell'istanza di SQL Server

## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, sono necessari SQL Server Management Studio, l'accesso a SQL Server e un database AdventureWorks. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Scaricare un [database campione AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Le istruzioni per il ripristino dei database in SSMS sono disponibili in [Ripristino di un database](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 

## <a name="comment--uncomment-your-t-sql-code"></a>Inserire e rimuovere commenti nel codice T-SQL
È possibile inserire e rimuovere commenti in parti del testo usando il pulsante dei commenti sulla barra degli strumenti. Il testo che viene impostato come commento non viene eseguito. 

1. Aprire SQL Server Management Studio. 
2. Connettersi a SQL Server.
3. Aprire una finestra **Nuova query**. 
4. Incollare il frammento di codice T-SQL seguente nella finestra del testo: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 


5. Evidenziare la parte del testo **Alter Database** e fare clic su **Commento** sulla barra degli strumenti: 

    ![Commento](media/ssms-tricks/comment.png)
6. Fare clic su **Esegui** per eseguire la parte di testo senza commenti. 
7. Evidenziare tutto tranne il comando **Alter Database** e fare clic su **Commento** sulla barra degli strumenti:

    ![Commentare tutto](media/ssms-tricks/commenteverything.png)

8. Evidenziare la parte **Alter Database** e fare clic su **Uncomment** (Rimuovi commento) per rimuovere i commenti:

    ![Rimuovere il commento](media/ssms-tricks/uncomment.png)
    
9. Fare clic su **Esegui** per eseguire la parte di testo senza commenti. 

## <a name="indent-your-text"></a>Impostare un rientro del testo
I pulsanti di rientro consentono di aumentare e ridurre il rientro del testo. 

1. Aprire una finestra **Nuova query**. 
2. Incollare il frammento di codice T-SQL seguente nella finestra del testo: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 
 
3. Evidenziare la parte di testo **Alter Database** e premere **Aumenta rientro** sulla barra degli strumenti per spostare il testo in avanti:

    ![Aumenta rientro](media/ssms-tricks/increaseindent.png)

4. Evidenziare nuovamente la parte **Alter Database** e questa volta fare clic su **Riduci rientro** per riportare indietro il testo. 
    ![Riduci rientro](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>Filtrare oggetti in Esplora oggetti
Quando un database include molti oggetti, può risultare difficile trovare un oggetto specifico. Per semplificare questa operazione, è possibile filtrare gli oggetti. In questa sezione viene illustrato come filtrare le tabelle, ma gli stessi passaggi possono essere applicati a qualsiasi altro nodo all'interno di **Esplora oggetti**

1. Connettersi a SQL Server.
2. Espandere il nodo **Database**.
3. Espandere il nodo del database **AdventureWorks**. 
4. Espandere il nodo **Tabelle**. 
   - Si noterà che è possibile visualizzare tutte le tabelle presenti nel database.
5. Fare clic con il pulsante destro del mouse sul nodo **Tabelle** > **Filtro** > **Impostazioni filtro**:

    ![Impostazioni filtro](media/ssms-tricks/filtersettings.png)

6. Nella finestra Impostazioni filtro, è possibile modificare le impostazioni del filtro. Alcuni esempi:
    - Filtro per il nome: ![Filtro per nome](media/ssms-tricks/filterbyname.png)
    - Filtro per lo schema: ![Filtro per schema](media/ssms-tricks/filterbyschema.png)

7. Per cancellare il filtro, fare clic con il pulsante destro del mouse su **Tabelle** > **Rimuovi filtro**

    ![Rimuovi filtro](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>Accedere al log degli errori di SQL Server
Il log degli errori è un file che contiene i dettagli di ciò che si verifica all'interno di SQL Server. All'interno di SSMS è possibile esplorare tale file ed eseguirvi delle query. È anche reperibile come un file con estensione log su disco.

### <a name="open-error-log-within-ssms"></a>Aprire il log degli errori in SSMS
1. Connettersi a SQL Server.
2. Espandere il nodo **Gestione** . 
3. Espandere il nodo **Log di SQL Server**. 
4. Fare clic con il pulsante destro del mouse sul log degli errori **Current** > **Visualizza log di SQL Server**:

    ![Visualizzare il log degli errori in SSMS](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-error-log-within-ssms"></a>Eseguire query sul log degli errori in SSMS
1. Connettersi a SQL Server.
2. Aprire una finestra **Nuova query**.
3. Incollare il frammento di codice T-SQL seguente nella finestra di query:

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 
4. Modificare il testo tra virgolette singole nel testo di interesse.
5. Eseguire la query e visualizzare i risultati:
   
    ![Eseguire query sul log degli errori](media/ssms-tricks/queryerrorlog.png)


### <a name="find-error-log-location-if-youre-connected-to-sql"></a>Trovare il percorso del log degli errori se si è connessi a SQL
1. Connettersi a SQL Server.
2. Aprire una finestra **Nuova query**.
3. Incollare il frammento di codice T-SQL seguente nella finestra di query e fare clic su **Esegui**:

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. I risultati illustrano il percorso del log degli errori nel file system: 

    ![Trovare il log degli errori mediante query](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-error-log-location-if-you-cannot-connect-to-sql"></a>Trovare il percorso del log degli errori se non è possibile connettersi a SQL
1. Aprire Gestione configurazione SQL Server. 
2. Espandere il nodo **Servizi**.
3. Fare clic con il pulsante destro del mouse sull'istanza di Server SQL > **Proprietà**:

    ![Proprietà della Gestione configurazione](media/ssms-tricks/serverproperties.PNG)

4. Selezionare la scheda **Parametri di avvio**.
5. Nell'area **Parametri esistenti** il percorso dopo "-e" è il percorso del log degli errori: 
    
    ![log degli errori](media/ssms-tricks/errorlog.png)
    - Si noterà che esistono diversi file errorlog.* in questo percorso. Quello che termina con *.log è quello corrente. Quelli che terminano con i numeri sono log precedenti, dal momento che viene creato un nuovo log ad ogni riavvio di SQL Server. 
6. Aprire il file nel Blocco note. 

## <a name="determine-sql-server-name"></a>Determinare il nome di SQL Server...
Esistono diversi modi per determinare il nome di SQL Server, prima e dopo la connessione.  

### <a name="when-you-dont-know-it"></a>...Quando non lo si conosce
1. Seguire la procedura per individuare il [log degli errori di SQL Server su disco](#finding-your-error-log-if-you-cannot-connect-to-sql). 
2. Aprire errorlog.log nel Blocco note. 
3. Scorrere fino a quando non si trova il testo "Il nome del server è":
  - Il testo racchiuso tra virgolette singole è il nome del server SQL Server al quale si eseguirà la connessione: ![Nome del server nel log degli errori](media/ssms-tricks/servernameinlog.png). Il formato è 'NOMEHOST\NOMEISTANZA'. Se viene visualizzato solo il nome host, l'istanza installata è l'istanza predefinita e il suo nome è "MSSQLSERVER". Quando ci si connette a un'istanza predefinita, è sufficiente digitare il nome host per connettersi a SQL Server.  

### <a name="once-youre-connected-to-sql"></a>...Dopo essersi connessi a SQL Server 
Il nome del server SQL Server al quale si è connessi è visualizzato in tre posizioni. 

1. Il nome del server sarà elencato in **Esplora oggetti**:

    ![Nome dell'istanza in Esplora oggetti](media/ssms-tricks/nameinobjectexplorer.png)
2. Il nome del server sarà elencato nella finestra di query:

    ![Nome nella finestra di query](media/ssms-tricks/nameinquerywindow.png)
3. Il nome del server sarà elencato anche nella **finestra Proprietà**.
    - Per accedere a questa finestra, aprire **Visualizza** Menu > **Finestra Proprietà**:

    ![Nome in Proprietà](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>...Se si è connessi a un alias o a un listener del gruppo di disponibilità 
Quando si è connessi a un alias o a un listener del gruppo di disponibilità, sono questi elementi che vengono visualizzati in **Esplora oggetti** e **Proprietà**. In questo caso il nome di SQL Server potrebbe non essere immediatamente evidente e deve essere eseguita una query per recuperarlo. 

1. Connettersi a SQL Server.
2. Aprire una finestra **Nuova query**.
3. Incollare il frammento di codice T-SQL seguente nella finestra: 

  ```sql
   select @@Servername 
 ``` 
4. Visualizzare i risultati della query per identificare il nome del server di SQL Server cui si è connessi: 
    
    ![Query sul nome del server](media/ssms-tricks/queryservername.png)


