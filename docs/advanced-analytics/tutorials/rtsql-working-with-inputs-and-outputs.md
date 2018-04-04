---
title: Utilizzo di input e output (R nella Guida rapida SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 07/31/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
dev_langs:
- R
- SQL
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 831ca196f4c45c169f398beb39895c7fa29e405f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="working-with-inputs-and-outputs-r-in-sql-quickstart"></a>Utilizzo di input e output (R nella Guida rapida SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Quando si desidera eseguire il codice R in SQL Server, è necessario eseguire il wrapping dello script R in una stored procedure di sistema [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Questa stored procedure permette di avviare il runtime R nel contesto di SQL Server, che passa i dati a R, gestisce le sessioni utente di R in modo sicuro e restituisce gli eventuali risultati al client.

## <a name="bkmk_SSMSBasics"></a>Creare alcuni semplici dati di prova

Creare una tabella di dati di test eseguendo l'istruzione T-SQL seguente:

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

Dopo aver creato la tabella, usare questa istruzione per eseguire una query sulla tabella:
  
```sql
SELECT * FROM RTestData
```

**Risultati**

|col1|
|------|
|*1*|
|*10*|
|*100*|

## <a name="get-the-same-data-using-r-script"></a>Ottenere gli stessi dati con lo script R

Dopo aver creato la tabella, eseguire questa istruzione:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

Ottiene i dati dalla tabella, effettua un round trip mediante il runtime di R e restituisce i valori con il nome di colonna, *NewColName*.

**Risultati**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**Commenti**

+ In Management Studio i risultati tabulari vengono restituiti nel riquadro **Valori**. I messaggi restituiti dal runtime R vengono visualizzati nel riquadro **Messaggi**.
+ Il parametro *@language* definisce l'estensione del linguaggio da chiamare, in questo caso R.
+ Nel parametro *@script* è possibile definire i comandi da passare al runtime R. L'intero script R deve essere incluso in questo argomento come testo Unicode. È anche possibile aggiungere il testo a una variabile di tipo **nvarchar** e quindi chiamare la variabile.
+ I dati restituiti dalla query vengono passati al runtime R, che restituisce i dati a SQL Server come frame di dati.
+ La clausola WITH RESULT SETS definisce lo schema della tabella dati restituita per SQL Server.

## <a name="change-input-or-output-variables"></a>Modificare le variabili di input o output

L'esempio precedente usa i nomi delle variabili di input e output predefiniti _InputDataSet_ e _OutputDataSet_. Per definire i dati di input associati a _InputDatSet_, è necessario usare la variabile *@input_data_1*.

In questo esempio i nomi delle variabili di input e output per la stored procedure sono stati modificati in *SQLOut* e *SQLIn*:

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```

È stato viene visualizzato l'errore, "dell'oggetto SQL\_in non trovato"? Il motivo è che R supporta la distinzione tra maiuscole e minuscole. Nell'esempio lo script R usa le variabili *SQL_in* e *SQL_out*, ma i parametri per la stored procedure usano le variabili *SQL_In* e *SQL_Out*.

Ciò avviene perché R è tra maiuscole e minuscole. Nell'esempio lo script R usa le variabili *SQL_in* e *SQL_out*, ma i parametri per la stored procedure usano le variabili *SQL_In* e *SQL_Out*.
Tenta correzione **solo** il *SQL_In* variabile ed eseguire di nuovo la stored procedure.

Ora viene visualizzato un **diversi** errore:

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

Verrà visualizzato questo errore perché è possibile prevedere la verifica spesso quando si testa nuovo codice R. Significa che lo script R è stato eseguito correttamente, ma ha ricevuto dati non SQL Server o ha ricevuto dati non corretti o imprevisti.

In questo caso, lo schema di output (riga che inizia con **WITH**) specifica che deve essere restituita una colonna di dati Integer, ma poiché R ha inserito i dati in una variabile diversa, nessun dato è stato restituito a SQL Server e, di conseguenza, è stato generato l'errore. Per correggere l'errore, correggere il secondo nome della variabile.

**Ricordare questi requisiti.**

- I nomi delle variabili devono seguire le regole per gli identificatori SQL validi.
- L'ordine dei parametri è importante. È necessario specificare per primi i parametri obbligatori *@input_data_1* e *@output_data_1*, per poi usare i parametri facoltativi *@input_data_1_name* e *@output_data_1_name*.
- È possibile passare come parametro un solo set di dati di input ed è possibile restituire un solo set di dati. È tuttavia possibile chiamare altri set di dati dall'interno del codice R e restituire output di altri tipi oltre al set di dati. È anche possibile aggiungere la parola chiave OUTPUT a qualsiasi parametro in modo che venga restituito con i risultati. Più avanti in questa esercitazione viene fornito un semplice esempio.
- L'istruzione `WITH RESULT SETS` definisce lo schema per i dati, a favore di SQL Server. È necessario specificare tipi di dati compatibili con SQL per ogni colonna restituita da R. È possibile usare la definizione dello schema per specificare anche nuovi nomi di colonna. Non è necessario usare i nomi di colonna dal frame di dati R. In alcuni casi, questa clausola è facoltativa. Provare omettendola e osservare cosa accade.

## <a name="generate-results-using-r"></a>Generare risultati con R

È anche possibile generare valori usando solo lo script R e lasciando vuota la stringa di query di input in _@input_data_1_. In alternativa, usare un'istruzione SQL SELECT valida come segnaposto, senza usare i risultati SQL nello script R.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**Risultati**

*Col1*
*hello*
<code>   </code>
*world*

## <a name="next-lesson"></a>Lezione successiva

Verranno esaminati alcuni dei possibili problemi riscontrati quando si passano dati tra R e SQL Server, ad esempio quelli relativi alle conversioni implicite e alle differenze nei dati tabulari tra R e SQL.

[R e tipi di dati e oggetti dati SQL](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
