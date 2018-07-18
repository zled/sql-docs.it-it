---
title: Eseguire il wrapping di codice Python in una stored procedure | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3b7ffeac0dfe1e441f188aae67e28004e294fc3e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32805994"
---
# <a name="wrap-python-code-in-a-stored-procedure"></a>Eseguire il wrapping di codice Python in una stored procedure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In un [lezione precedente](run-python-using-t-sql.md), si è appreso come rendere Python di comunicare con SQL Server. In questa lezione si informazioni su come incorporare il codice Python in una stored procedure, per ottenere i dati dei set di dati di esempio Python e scrivere dati in una tabella di SQL Server.

Stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) fornisce wrapper che passano le variabili SQL e set di dati SQL in Python. Inoltre, gestisce l'output dei risultati da Python e li passa a SQL Server in un formato compatibile con i tipi di dati SQL.

Di seguito viene illustrato il funzionamento.

## <a name="prepare-the-database-and-tables"></a>Preparare il database e tabelle

Sebbene sia possibile configurare un client remoto ed eseguire il codice Python con codice di Visual Studio, Visual Studio, PyCharm o altri strumenti, per semplificare lo scenario, tutto il codice in questa lezione deve essere eseguito come parte di una stored procedure.

1. Avviare SQL Server Management Studio e aprire un nuovo **Query** finestra.  

2. Creare un nuovo database per questo progetto e modificare il contesto del **Query** finestra per l'utilizzo del nuovo database.

    ```sql
    CREATE DATABASE sqlpy
    GO
    USE sqlpy
    GO
    ```

    > [!TIP] 
    > Se si ha familiarità con SQL Server o si sta lavorando in un server in cui si è proprietari, un errore comune è di accedere e iniziare a lavorare senza notare in cui si trova il **master** database. Per verificare che si utilizza il database corretto, specificare sempre il contesto utilizzando il `USE <database name>` istruzione.

3. Aggiungere alcune tabelle vuote: uno per archiviare i dati e uno per archiviare i modelli di cui eseguire il training. In un secondo momento si popolano le tabelle con Python.

    Il codice seguente crea la tabella per i dati di training.

    ```sql
    DROP TABLE IF EXISTS iris_data;
    GO
    CREATE TABLE iris_data (
      id INT NOT NULL IDENTITY PRIMARY KEY
      , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
      , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
      , "Species" VARCHAR(100) NOT NULL, "SpeciesId" INT NOT NULL
    );
    ```

    Se si ha familiarità con T-SQL, è opportuno memorizzare il `DROP...IF` istruzione. Quando si tenta di creare una tabella e ne esiste già, SQL Server restituisce un errore: "Si è già un oggetto denominato 'iris_data' nel database". Un modo per evitare tali errori consiste nell'eliminare le tabelle esistenti o altri oggetti come parte del codice.

4. Eseguire il codice seguente per creare la tabella utilizzata per archiviare il modello con training. Per salvare i modelli di Python (o R) in SQL Server, devono essere serializzati e archiviati in una colonna di tipo **varbinary (max)**. 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    Oltre al contenuto del modello, in genere, è necessario anche aggiungere le colonne di altri metadati utile, ad esempio il nome del modello, la data in cui che è stato eseguito il training, l'algoritmo di origine e i parametri, dati di origine e così via. È ora sarà semplicità e usare solo il nome del modello.

## <a name="populate-the-table"></a>Popolare la tabella

Per spostare i dati di training da Python in un Server SQL nella tabella è un processo in più passaggi:

+ Si progetta una stored procedure che ottiene i dati desiderati.
+ Si esegue la stored procedure per recuperare i dati.
+ Utilizzare un'istruzione INSERT per specificare dove devono essere salvati i dati recuperati.

1. Creare la stored procedure seguente che include il codice Python. 

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    from sklearn import datasets
    iris = datasets.load_iris()
    iris_data = pandas.DataFrame(iris.data)
    iris_data["Species"] = pandas.Categorical.from_codes(iris.target, iris.target_names)
    iris_data["SpeciesId"] = iris.target
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

    Quando si esegue questo codice, è necessario ottenere il messaggio "Comandi vengano eseguiti correttamente." Tutto ciò significa è che sia stata creata la stored procedure in base alle specifiche dell'utente.

2. Per popolare la tabella, eseguire la stored procedure e specificare la tabella in cui scrivere i dati. Durante l'esecuzione, la stored procedure esegue il codice Python, che carica il set di dati Iris dai dati di esempio Python incorporati.

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    Se si ha familiarità con T-SQL, tenere presente che l'istruzione INSERT aggiunge solo nuovi dati. non verificare la presenza di dati esistenti, eliminare e ricompilare la tabella. Per evitare la visualizzazione di più copie degli stessi dati in una tabella, è possibile eseguire questa istruzione prima: `TRUNCATE TABLE iris_data`. L'istruzione T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql) istruzione elimina i dati esistenti, ma mantiene intatte la struttura della tabella.

    > [!TIP]
    > Per modificare la stored procedure in un secondo momento, è necessario eliminare e ricreare l'oggetto. Utilizzare il [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql) istruzione. 

3. Per verificare che i dati è stati caricati correttamente, è possibile eseguire alcune semplici query:

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

Nel [lezione successiva](../tutorials/train-score-using-python-in-tsql.md), si crea un modello di machine learning e salvarlo in una tabella.

### <a name="further-reading-about-stored-procedures"></a>Ulteriori informazioni sulle stored procedure

Se si ha familiarità con SQL Server, può risultare complicate inizialmente le stored procedure. Tuttavia, una stored procedure è un'interfaccia potente e flessibile per passare dati tra applicazioni e il server. Utilizzando una stored procedure, è possibile in modo dinamico definire gli input, che consente di passare facilmente in nuovi nomi di modello, i nuovi parametri e i nuovi dati, senza alterare il codice Python.

Per una panoramica del funzionamento delle stored procedure lavoro, vedere [Stored procedure (motore di Database)](https://docs.microsoft.com/sql/relational-databases/stored-procedures/stored-procedures-database-engine), o in questa esercitazione: [scrittura di istruzioni Transact-SQL](https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements).

Esistono inoltre alcune esercitazioni buon nei siti delle community, ad esempio [SQL Server Central](http://www.sqlservercentral.com/) o [Team SQL](http://www.sqlteam.com/).

Come si pensa come è possibile incapsulare meglio il codice Python in T-SQL, considerare anche le seguenti caratteristiche:

+ Definizione dei valori predefiniti per la stored procedure
+ Utilizzando la parola chiave OUTPUT per il passaggio attraverso le variabili di input
+ Creazione di definizioni dello schema utilizzando con risultati per garantire che i dati utilizzati da applicazioni con destra tipi di dati e i nomi di colonna
+ Fornire suggerimenti per migliorare l'elaborazione batch
+ Rappresentazione di un utente diverso per testare il codice, uso di EXECUTE AS clausola

## <a name="next-lesson"></a>Lezione successiva

[Eseguire il training di un modello di Python e generare i punteggi in SQL Server](../tutorials/train-score-using-python-in-tsql.md)
