---
title: Eseguire Python con T-SQL | Documenti Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- Python
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7ab513960d3e102725bde6762fcf4de117554db
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="run-python-using-t-sql"></a>Eseguire Python con T-SQL

Questo esempio viene illustrato come eseguire un semplice script Python in SQL Server, tramite la stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

## <a name="step-1-create-the-test-data-table"></a>Passaggio 1. Creare la tabella di dati di test

In primo luogo, si creeranno alcuni dati aggiuntivi, da utilizzare durante il mapping di nomi dei giorni della settimana per i dati di origine. Eseguire l'istruzione T-SQL seguente per creare la tabella.

```SQL
CREATE TABLE PythonTest (
    [DayOfWeek] varchar(10) NOT NULL,
    [Amount] float NOT NULL
    )
GO

INSERT INTO PythonTest VALUES
('Sunday', 10.0),
('Monday', 11.1),
('Tuesday', 12.2),
('Wednesday', 13.3),
('Thursday', 14.4),
('Friday', 15.5),
('Saturday', 16.6),
('Friday', 17.7),
('Monday', 18.8),
('Sunday', 19.9)
GO
```

## <a name="step-2-run-the-hello-world-script"></a>Passaggio 2. Eseguire lo script "Hello World"

Il codice seguente viene caricato il file eseguibile di Python, passa i dati di input e per ogni riga di dati di input, aggiorna il nome del giorno nella tabella con un numero che rappresenta l'indice del giorno della settimana.

Prendere nota del parametro  *@RowsPerRead* . Questo parametro specifica il numero di righe che vengono passati al runtime di Python da SQL Server.

La libreria di analisi dati di Python, noto come **pandas**, è necessario per passare dati a SQL Server ed è incluso per impostazione predefinita con servizi di Machine Learning.

```sql
DECLARE @ParamINT INT = 1234567
DECLARE @ParamCharN VARCHAR(6) = 'INPUT '

print '------------------------------------------------------------------------'
print 'Output parameters (before):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)

print 'Dataset (before):'
SELECT * FROM PythonTest

print '------------------------------------------------------------------------'
print 'Dataset (after):'
DECLARE @RowsPerRead INT = 5

execute sp_execute_external_script 
@language = N'Python',
@script = N'
import sys
import os
print("*******************************")
print(sys.version)
print("Hello World")
print(os.getcwd())
print("*******************************")
if ParamINT == 1234567:
       ParamINT = 1
else:
       ParamINT += 1

ParamCharN="OUTPUT"
OutputDataSet = InputDataSet

global daysMap

daysMap = {
       "Monday" : 1,
       "Tuesday" : 2,
       "Wednesday" : 3,
       "Thursday" : 4,
       "Friday" : 5,
       "Saturday" : 6,
       "Sunday" : 7
       }

OutputDataSet["DayOfWeek"] = pandas.Series([daysMap[i] for i in OutputDataSet["DayOfWeek"]], index = OutputDataSet.index, dtype = "int32")
', 
@input_data_1 = N'SELECT * FROM PythonTest', 
@params = N'@r_rowsPerRead INT, @ParamINT INT OUTPUT, @ParamCharN CHAR(6) OUTPUT',
@r_rowsPerRead = @RowsPerRead,
@paramINT = @ParamINT OUTPUT,
@paramCharN = @ParamCharN OUTPUT
with result sets (("DayOfWeek" int null, "Amount" float null))

print 'Output parameters (after):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)
GO
```

> [!TIP]
> I parametri per questa stored procedure sono descritti in dettaglio in questa Guida rapida: [codice R tramite T-SQL](rtsql-using-r-code-in-transact-sql-quickstart.md).

## <a name="step-3-view-the-results"></a>Passaggio 3. Visualizzare i risultati

La stored procedure restituisce i dati originali, lo script viene applicato e quindi restituisce i dati modificati nel **risultati** riquadro di Management Studio o un altro strumento di query SQL.


|DayOfWeek (prima)| Amount|DayOfWeek (dopo) |
|-----|-----|-----|
|Domenica|10|7|
|Lunedì|11.1|1|
|Martedì|12.2|2|
|Mercoledì|13.3|3|
|Giovedì|14.4|4|
|Venerdì|15.5|5|
|Sabato|16.6|6|
|Venerdì|17.7|5|
|Lunedì|18.8|1|
|Domenica|19.9|7|

I messaggi di stato o gli errori restituiti nella console di Python vengono restituiti come messaggi di **Query** finestra. Di seguito è riportato un estratto dell'output che potrebbe essere visualizzato:

*Risultati di esempio*

```
Output parameters (before):
ParamINT=1234567
ParamCharN=INPUT 
Dataset (before):

(10 rows affected)

Dataset (after):
STDOUT message(s) from external script: 
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

(10 rows affected)
Output parameters (after):
ParamINT=2
ParamCharN=OUTPUT
```

+ L'output del messaggio include la directory di lavoro utilizzata per l'esecuzione di script. In questo esempio, MSSQLSERVER01 fa riferimento all'account di lavoro allocati da SQL Server per gestire il processo. Il GUID è il nome di una cartella temporanea viene creata durante l'esecuzione di script per archiviare gli elementi di dati e script. Le cartelle temporanee sono protetti da SQL Server e pulite per l'oggetto processo di Windows dopo il completamento dello script è terminata.

+ La sezione che contiene il messaggio "Hello World" visualizzato due volte. Ciò accade perché il valore di  *@RowsPerRead*  è stato impostato su 5 e sono presenti 10 righe nella tabella; pertanto, in cui sono necessarie due chiamate di Python per elaborare tutte le righe nella tabella.

    Le esecuzioni di produzione, è consigliabile sperimentare valori diversi per determinare il numero massimo di righe che devono essere passati in ogni batch. Il numero ottimale di righe è dipendente dai dati e è influenzato dal entrambi il numero di colonne nel set di dati e il tipo di dati che si siano passando.

## <a name="resources"></a>Risorse

Vedere questi ulteriori esempi di Python e le esercitazioni per suggerimenti avanzati e demo end-to-end.

+ [Utilizzare revoscalepy Python per creare un modello](use-python-revoscalepy-to-create-model.md)
+ [Nel Database Python per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)
+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se non è possibile trovare la stored procedure, `sp_execute_external_script`, significa che probabile che non è stata completata la configurazione di istanza per il supporto runtime esterni. Dopo l'installazione di SQL Server 2017 e selezionando Python come di machine learning language, è necessario abilitare anche in modo esplicito la funzionalità mediante `sp_configure`e quindi riavviare l'istanza. Per informazioni dettagliate, vedere [programma di installazione di Machine Learning Services con Python](../python/setup-python-machine-learning-services.md).
