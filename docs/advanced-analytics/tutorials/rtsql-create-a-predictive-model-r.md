---
title: Guida introduttiva per creare un modello predittivo tramite R in SQL Server Machine Learning | Microsoft Docs
description: Questa Guida introduttiva descrive come compilare un modello in R con dati di SQL Server per tracciare le stime.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7ca2fcac5bef63a4abf2449b56c25a600b9255c3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086823"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Guida introduttiva: Creare un modello predittivo tramite R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa Guida introduttiva, si sarà informazioni su come eseguire il training di un modello usando R e quindi salvare il modello in una tabella in SQL Server. Si tratta di un semplice modello di regressione che stima lo spazio di frenata di un'auto in base alla velocità. Si userà il `cars` set di dati incluso in R, perché è piccolo e facile da comprendere.

## <a name="prerequisites"></a>Prerequisiti

Una Guida introduttiva precedente [Hello World in R e SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), vengono fornite informazioni e collegamenti per configurare l'ambiente R necessario per questa Guida introduttiva.

## <a name="create-the-source-data"></a>Creare i dati di origine

Creare prima di tutto una tabella in cui salvare i dati di training.

```sql
CREATE TABLE CarSpeed ([speed] int not null, [distance] int not null)
INSERT INTO CarSpeed
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'car_speed <- cars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'car_speed'
```

+ Alcuni utenti preferiscono usare le tabelle temporanee, ma tenere presente che alcuni client R disconnettere le sessioni tra i batch.

+ Nel runtime R sono inclusi diversi set di dati di piccole e grandi dimensioni. Per ottenere un elenco di set di dati installati con R, digitare `library(help="datasets")` da un prompt dei comandi R.

## <a name="create-a-regression-model"></a>Creare un modello di regressione

I dati sulla velocità delle auto contengono due colonne, entrambe numeriche, `dist` e `speed`. Sono presenti più osservazioni di alcune velocità. Da questi dati si creerà un modello di regressione lineare che descrive alcune relazioni tra la velocità di un'auto e la distanza necessaria per arrestarla.

I requisiti di un modello lineare sono semplici:

+ Definire una formula che descrive la relazione tra la variabile dipendente `speed` e la variabile indipendente `distance`

+ Fornire i dati di input da usare nel training del modello

> [!TIP]
> Se è necessario un aggiornamento per i modelli lineari, si consiglia di questa esercitazione, che descrive il processo di adattamento di un modello tramite rxLinMod: [adattamento di modelli lineari](https://docs.microsoft.com/r-server/r/how-to-revoscaler-linear-model)

Per compilare effettivamente il modello, si definisce la formula nel codice R e si passano i dati come parametro di input.

```sql
DROP PROCEDURE IF EXISTS generate_linear_model;
GO
CREATE PROCEDURE generate_linear_model
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'lrmodel <- rxLinMod(formula = distance ~ speed, data = CarsData);
        trained_model <- data.frame(payload = as.raw(serialize(lrmodel, connection=NULL)));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model varbinary(max)));
END;
GO
```

+ Il primo argomento per rxLinMod è il parametro *formula*, che definisce la distanza come dipendente dalla velocità.
+ I dati di input vengono archiviati nella variabile `CarsData`, popolata dalla query SQL. Se non si assegna un nome specifico ai dati di input, il nome predefinito della variabile sarà _InputDataSet_.

## <a name="create-a-table-for-storing-the-model"></a>Creare una tabella per archiviare il modello

Quindi, archiviare il modello in modo che è possibile ripetere il training o usarlo per la stima. L'output di un pacchetto R che crea un modello è in genere un **oggetto binario**. La tabella in cui si archivia il modello deve quindi contenere una colonna di tipo **varbinary**.

```sql
CREATE TABLE stopping_distance_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null);
```

## <a name="save-the-model"></a>Salvare il modello

Per salvare il modello, eseguire l'istruzione Transact-SQL seguente per chiamare la stored procedure, generare il modello e salvarlo in una tabella.

```sql
INSERT INTO stopping_distance_models (model)
EXEC generate_linear_model;
```

Si noti che se si esegue questo codice una seconda volta, viene visualizzato questo errore:

```
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Un modo per evitare questo errore consiste nell'aggiornare il nome di ogni nuovo modello. È ad esempio possibile sostituire il nome con uno più descrittivo e includere il tipo di modello, il giorno della creazione e così via.

```sql
UPDATE stopping_distance_models
SET model_name = 'rxLinMod ' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="output-additional-variables"></a>Altre variabili di output

In genere l'output di R dalla stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) è limitato a un singolo frame di dati. (Questa limitazione potrebbe essere rimossa in futuro.)

Tuttavia è possibile restituire output di altri tipi, ad esempio scalari, unitamente al frame di dati.

Si supponga, ad esempio, di voler eseguire il training di un modello, ma di visualizzare immediatamente una tabella di coefficienti dal modello. È possibile creare la tabella di coefficienti come set di risultati principale ed eseguire l'output del modello con training in una variabile SQL. È possibile riutilizzare immediatamente il modello chiamando la variabile o è stato possibile salvare il modello a una tabella come illustrato di seguito.

```sql
DECLARE @model varbinary(max), @modelname varchar(30)
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
        speedmodel <- rxLinMod(distance ~ speed, CarsData)
        modelbin <- serialize(speedmodel, NULL)
        OutputDataSet <- data.frame(coefficients(speedmodel));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @params = N'@modelbin varbinary(max) OUTPUT'
    , @modelbin = @model OUTPUT
    WITH RESULT SETS (([Coefficient] float not null));

-- Save the generated model
INSERT INTO [dbo].[stopping_distance_models] (model_name, model)
VALUES ('latest model', @model)
```

**Risultati**

![rslq_basictut_coefficients](media/rslq-basictut-coefficients.PNG)

### <a name="summary"></a>Riepilogo

Tenere presenti queste regole per l'utilizzo di parametri SQL e le variabili R in `sp_execute_external_script`:

+ Tutti i parametri SQL mappati a uno script R devono essere elencati dal nome tra parentesi il  _\@params_ argomento.
+ Aggiungere la parola chiave OUTPUT nell'output di uno di questi parametri, il  _\@params_ elenco.
+ Dopo avere elencato i parametri con mapping, fornire il mapping, riga per riga, dei parametri SQL alle variabili R, immediatamente dopo il  _\@params_ elenco.

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di un modello, nella Guida introduttiva finale, si apprenderà come generare le stime da esso e tracciare i risultati.

> [!div class="nextstepaction"]
> [Guida introduttiva: Stimare e creare un tracciato dal modello](../tutorials/rtsql-predict-and-plot-from-model.md)