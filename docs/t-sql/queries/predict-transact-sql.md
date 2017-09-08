---
title: STIMA (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PREDICT
- PREDICT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PREDICT clause
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 529cb229b6658085d0f2122604a4ed638f66a84c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="predict-transact-sql"></a>STIMA (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Genera un valore stimato o punteggi in base a un modello archiviato.  

## <a name="syntax"></a>Sintassi

```
PREDICT  
(  
  MODEL = @model | model_literal,  
  DATA = object AS <table_alias>  
)  
WITH ( <result_set_definition> )  

<result_set_definition> ::=  
  {  
    { column_name  
      data_type  
      [ COLLATE collation_name ]  
      [ NULL | NOT NULL ]  
    }  
      [,...n ]  
  }  

MODEL = @model | model_literal  
```

### <a name="arguments"></a>Argomenti

**model**

Il `MODEL` parametro viene utilizzato per specificare il modello utilizzato per l'assegnazione dei punteggi o la stima. Il modello viene specificato come una variabile o un valore letterale o un'espressione scalare.

L'oggetto modello può essere creato utilizzando R, Python o un altro strumento.

**dati**

Il parametro di dati viene utilizzato per specificare i dati utilizzati per l'assegnazione dei punteggi o la stima. Dati vengono specificati sotto forma di un'origine della tabella nella query. Origine di tabella può essere una tabella, alias di tabella, alias CTE, vista o funzione con valori di tabella.

**parametri**

Il parametro di parametri viene utilizzato per specificare i parametri definiti dall'utente facoltativi utilizzati per il punteggio o la stima.

Il nome di ogni parametro è specifico per il tipo di modello. Ad esempio, la funzione rxPredict in RevoScaleR supporta il parametro  _@computeResiduals bit_ per supportare i calcoli di residui quando valutazione di un modello di regressione logistica. È possibile passare il nome di parametro e il valore per il `PREDICT` (funzione).

> [NOTA] Questa opzione non è supportata nella versione precedente di SQL Server 2017 e viene inclusa solo a fini di compatibilità di inoltro.

**CON ( \<result_set_definition >)**

La clausola WITH viene utilizzata per specificare lo schema dell'output restituito dal `PREDICT` (funzione).

Oltre alle colonne restituiti dal `PREDICT` funzione stessa, tutte le colonne che fanno parte dei dati di input sono disponibili per l'utilizzo nella query.

### <a name="return-values"></a>Valori restituiti

Nessuno schema predefinito è disponibile. SQL Server non convalida il contenuto del modello e non convalida i valori della colonna restituito.  
- Il `PREDICT` funzione passa attraverso le colonne come input  
- Il `PREDICT` funzione genera inoltre nuove colonne, ma il numero di colonne e i relativi tipi di dati dipende dal tipo di modello che è stato utilizzato per la stima.  

Eventuali messaggi di errore correlati ai dati, il modello o il formato di colonna vengono restituiti dalla funzione di stima sottostante associata al modello.  
- Per RevoScaleR, è la funzione equivalente [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)  
- Per MicrosoftML, la funzione equivalente è [rxPredict.mlModel](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxpredict)  

Non è possibile visualizzare la struttura di modello interno utilizzando `PREDICT`. Se si desidera conoscere il contenuto del modello stesso, è necessario caricare l'oggetto modello, deserializzarlo e utilizzare il codice R appropriato per analizzare il modello.

## <a name="remarks"></a>Osservazioni

Il `PREDICT` funzione è supportata in tutte le edizioni di SQL Server, tra cui Linux.

Non è necessario che sia installato R, Python o un altro computer, l'apprendimento di lingue nel server di utilizzare il `PREDICT` (funzione). È possibile eseguirne il training in un altro ambiente e salvarlo in una tabella di SQL Server per l'utilizzo con `PREDICT`, o chiamare il modello da un'altra istanza di SQL Server che contiene il modello salvato.

### <a name="supported-algorithms"></a>Algoritmi supportati

Il modello in uso deve essere stato creato con uno degli algoritmi supportati dal pacchetto RevoScaleR. Per un elenco di modelli attualmente supportati, vedere [punteggi in tempo reale](../../advanced-analytics/real-time-scoring.md).

### <a name="permissions"></a>Permissions

Non sono necessarie per autorizzazioni `PREDICT`; tuttavia, è necessario che l'utente `EXECUTE` dell'autorizzazione per il database e dell'autorizzazione per eseguire una query tutti i dati che viene utilizzati come input. L'utente deve essere in grado di leggere il modello da una tabella, anche se il modello è stato archiviato in una tabella.

## <a name="examples"></a>Esempi

Gli esempi seguenti illustrano la sintassi per chiamare il metodo `PREDICT`.

### <a name="call-a-stored-model-and-use-it-for-prediction"></a>Chiamare un modello archiviato e utilizzarlo per la stima

Questo esempio viene chiamato un modello di regressione logistica esistente archiviato nella tabella [models_table]. Ottiene il versione più recente modello con training, utilizzando un'istruzione SELECT e quindi passa il modello binario per la funzione di stima. I valori di input rappresentano le funzionalità; l'output rappresenta la classificazione assegnata dal modello.

```sql
DECLARE @logit_model varbinary(max) = "SELECT TOP 1 @model from [models_table]";
DECLARE @input_qry = "SELECT ID, [Gender], [Income] from NewCustomers";

SELECT PREDICT [class]
FROM PREDICT( MODEL = @logit_model,  DATA = @input_qry
WITH (class string);
```

### <a name="using-predict-in-a-from-clause"></a>Utilizzo di stima in una clausola FROM

Questo esempio fa riferimento il `PREDICT` funzionare nel `FROM` clausola di un `SELECT` istruzione:

```sql
SELECT d.*, p.Score
FROM PREDICT(MODEL = @logit_model, 
  DATA = dbo.mytable AS d) WITH (Score float) AS p;
```

L'alias **d** specificato per l'origine della tabella nel _dati_ parametro viene utilizzato per fare riferimento alle colonne appartenenti a dbo.mytable. L'alias **p** specificato per il **PREDICT** funzione viene utilizzata per fare riferimento alle colonne restituite dalla funzione di stima.

### <a name="combining-predict-with-an-insert-statement"></a>La combinazione di stima con un'istruzione INSERT

Uno dei casi di utilizzo comune per la stima consiste nel generare un punteggio per dati di input e quindi inserire i valori stimati in una tabella. Nell'esempio seguente si presuppone che l'applicazione chiamante utilizza una stored procedure per inserire una riga contenente il valore stimato in una tabella:

```sql
CREATE PROCEDURE InsertLoanApplication
(@p1 varchar(100), @p2 varchar(200), @p3 money, @p4 int)
AS
BEGIN
  DECLARE @model varbinary(max) = (select model
  FROM scoring_model
  WHERE model_name = 'ScoringModelV1');
  WITH d as ( SELECT * FROM (values(@p1, @p2, @p3, @p4)) as t(c1, c2, c3, c4) )

  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = d) WITH(score float) as p;
END;
```

Se la procedura accetta più righe tramite un parametro con valori di tabella, quindi può essere scritta come indicato di seguito:

```sql
CREATE PROCEDURE InsertLoanApplications (@new_applications dbo.loan_application_type)
AS
BEGIN
  DECLARE @model varbinary(max) = (SELECT model_bin FROM scoring_models WHERE model_name = 'ScoringModelV1');
  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = @new_applications as d)
  WITH (score float) as p;
END;
```

### <a name="creating-an-r-model-and-generating-scores-using-optional-model-parameters"></a>Creazione di un modello R e generazione di punteggi usando i parametri facoltativi del modello

> [!NOTE]
> Utilizzo dell'argomento di parametri non è supportato nella versione finale candidata 1.

Questo esempio si presuppone che hanno creato un modello di regressione logistica dotato di una matrice di covarianza, tramite una chiamata a RevoScaleR simile al seguente:

```R
logitObj <- rxLogit(Kyphosis ~ Age + Start + Number, data = kyphosis, covCoef = TRUE)
```

Se si archivia il modello in SQL Server in formato binario, è possibile utilizzare la funzione di stima per generare non solo le stime, ma le informazioni aggiuntive supportate dal tipo di modello, ad esempio errore o intervalli di confidenza.

Il codice seguente viene illustrata la chiamata equivalente da R a rxPredict:

```R
rxPredict(logitObj, data = new_kyphosis_data, computeStdErr = TRUE, interval = "confidence")
```

La chiamata equivalente utilizzando il `PREDICT` funzione fornisce anche il punteggio (previsto valore), errore e intervalli di confidenza:

```sql
SELECT d.Age, d.Start, d.Number, p.pred AS Kyphosis_Pred, p.stdErr, p.pred_lower, p.pred_higher
FROM PREDICT( MODEL = @logitObj,  DATA = new_kyphosis_data AS d,
  PARAMETERS = N'computeStdErr bit, interval varchar(30)',
  computeStdErr = 1, interval = 'confidence')
WITH (pred float, stdErr float, pred_lower float, pred_higher float) AS p;
```



