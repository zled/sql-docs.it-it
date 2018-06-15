---
title: sp_execute_external_script (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5660860a3a03a268b0903a0222753f1ea9bc5382
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263107"
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Esegue lo script fornito come argomento in una posizione esterna. Lo script deve essere scritto in una lingua supportata e registrata. Per eseguire **sp_execute_external_script**, è innanzitutto necessario abilitare gli script esterni utilizzando l'istruzione, `sp_configure 'external scripts enabled', 1;`.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```

## <a name="arguments"></a>Argomenti
 @language = N'*language*'  
 Indica il linguaggio di scripting. *linguaggio* viene **sysname**.  

 I valori validi sono `Python` o `R`. 
  
 @script = N'*script*'  
 Script di linguaggio esterno specificato come input un valore letterale o variabile. *script* viene **nvarchar (max)**.  
  
 [ @input_data_1_name = N'*input_data_1_name*']  
 Specifica il nome della variabile utilizzata per rappresentare la query definita dal @input_data_1. Il tipo di dati della variabile nello script esterno dipende dalla lingua. In caso di R, la variabile di input è un frame di dati. Nel caso di Python, l'input deve essere in formato tabulare. *input_data_1_name* viene **sysname**.  
  
 Valore predefinito è `InputDataSet`.  
  
 [ @input_data_1 = N'*input_data_1*']  
 Specifica i dati di input utilizzati dallo script esterno sotto forma di un [!INCLUDE[tsql](../../includes/tsql-md.md)] query. Il tipo di dati *input_data_1* è **nvarchar (max)**.
  
 [ @output_data_1_name = N'*output_data_1_name*']  
 Specifica il nome della variabile nello script esterno che contiene i dati da restituire al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo il completamento della chiamata alla stored procedure. Il tipo di dati della variabile nello script esterno dipende dalla lingua. Per R, l'output deve essere un frame di dati. Per Python, l'output deve essere un frame di dati pandas. *output_data_1_name* viene **sysname**.  
  
 Valore predefinito è "OutputDataSet".  
  
 [ @parallel = 0 | 1] Abilita l'esecuzione parallela di script R impostando il `@parallel` parametro su 1. Il valore predefinito per questo parametro è 0 (nessun parallelism).  
  
 Per gli script R che non utilizzano le funzioni RevoScaleR, utilizzando il `@parallel` parametro può essere utile per l'elaborazione di grandi set di dati, presupponendo che lo script può essere facilmente parallelizzato. Ad esempio, quando si utilizza l'oggetto R `predict` funzione con un modello per generare nuove stime, impostare `@parallel = 1` come hint per il motore di query. Se la query può essere eseguito in parallelo, le righe vengono distribuite in base al **MAXDOP** impostazione.  
  
 Se `@parallel = 1` e l'output come flusso direttamente al computer client, il `WITH RESULTS SETS` clausola è obbligatoria e deve essere specificato uno schema di output.  
  
 Per gli script R che utilizzano le funzioni RevoScaleR, l'elaborazione parallela viene gestito automaticamente e non è necessario specificare `@parallel = 1` per il **sp_execute_external_script** chiamare.  
  
 [ @params = N' *@parameter_name data_type* [OUT | OUTPUT] [,... n]']  
 Un elenco di dichiarazioni di parametro di input utilizzate nello script esterni.  
  
 [ @parameter1 = '*value1*' [OUT | OUTPUT] [,... n]]  
 Un elenco di valori per i parametri di input utilizzati dallo script esterno.  

## <a name="remarks"></a>Osservazioni

Utilizzare **sp_execute_external_script** per eseguire gli script scritti in una lingua supportata. Attualmente, i linguaggi supportati sono R per SQL Server 2016 e Python e R per SQL Server 2017. 

> [!IMPORTANT]
> La struttura della query è controllato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e gli utenti non possono eseguire operazioni arbitrarie nella query. 

Per impostazione predefinita, i set di risultati restituiti dalla stored procedure sono output con colonne senza nome. I nomi di colonna utilizzati all'interno di uno script sono locali per l'ambiente di scripting e non vengono riflesse nel set di risultati di output. Per denominare le colonne del set di risultati, utilizzare il `WITH RESULTS SET` clausola di [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 Oltre a restituire un set di risultati, è possibile restituire valori scalari per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando i parametri di OUTPUT. Nell'esempio seguente viene illustrato l'utilizzo del parametro di OUTPUT per restituire il modello R serializzato che è stato utilizzato come input per lo script:  

In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è costituita da un componente server installato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e un set di strumenti di workstation e librerie di connettività che connettono il data scientist all'ambiente ad alte prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È necessario installare di machine learning componenti durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione per abilitare l'esecuzione di script esterni. Per ulteriori informazioni, vedere [configurare servizi di SQL Server Machine Learning](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).  
  
È possibile controllare le risorse usate da script esterni tramite la configurazione di un pool di risorse esterne. Per altre informazioni, vedere [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Informazioni sul carico di lavoro possono essere ottenute dalle viste del catalogo di resource governor, viste a gestione dinamica e contatori. Per altre informazioni, vedere [viste del catalogo di Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Resource Governor correlati viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), e[ Oggetto script di SQL Server, esterno](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

Esecuzione di script di monitoraggio tramite [Sys.dm external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) e [Sys.dm external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

## <a name="streaming-execution-for-r-and-python-scripts"></a>Esecuzione di flusso per gli script R e Python  

Il flusso consente lo script R o Python operare con più dati che possono adattarsi alla memoria. Per controllare il numero di righe passate durante lo streaming, specificare un valore intero per il parametro, `@r_rowsPerRead` nel `@params` insieme.  Ad esempio, se si è training di un modello che utilizza i dati molto ampio, è possibile regolare il valore per leggere un numero inferiore di righe, per garantire che tutte le righe possono essere inviate in un blocco di dati. È inoltre possibile utilizzare questo parametro per gestire il numero di righe da leggere ed elaborati contemporaneamente, per limitare i problemi di prestazioni di server. 
  
Sia il `@r_rowsPerRead` parametro per lo streaming e `@parallel` argomento deve essere considerato come hint. Per l'hint da applicare, deve essere possibile generare un piano di query SQL che include l'elaborazione parallela. In caso contrario, l'elaborazione parallela non è abilitato.  
  
> [!NOTE]  
>  Lo streaming e l'elaborazione parallela sono supportati solo in Enterprise Edition. È possibile includere i parametri nelle query in Standard Edition senza che venga generato un errore, ma i parametri non hanno effetto e gli script R eseguiti in un unico processo.  
  
## <a name="restrictions"></a>Restrizioni  


### <a name="data-types"></a>Tipi di dati

I seguenti tipi di dati non sono supportati quando utilizzata nella query di input o i parametri di `sp_execute_external_script` procedure e restituito un errore di tipo non supportato.  

In alternativa, **CAST** la colonna o un valore a un tipo supportato in [!INCLUDE[tsql](../../includes/tsql-md.md)] prima dell'invio dello script esterno.  
  
-   **cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **ora**  
  
-   **sql_variant**  
  
-   **testo**, **immagine**  
  
-   **xml**  
  
-   **hierarchyid**, **geometry**, **geography**  
  
-   Tipi CLR definiti dall'utente

In generale, qualsiasi risultato set che non può essere mappato a un [!INCLUDE[tsql](../../includes/tsql-md.md)] tipo di dati, viene restituita come NULL.  

### <a name="restrictions-specific-to-r"></a>Restrizioni per R

Se l'input include **datetime** valori che non rientrano nell'intervallo consentito di valori in R, i valori vengono convertiti in **NA**. Questa operazione è necessaria perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente a un intervallo più ampio di valori rispetto a quelle supportate nel linguaggio R.

I valori float (ad esempio, `+Inf`, `-Inf`, `NaN`) non sono supportate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anche se entrambi i linguaggi utilizzano IEEE 754. Comportamento corrente invia solo i valori per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] direttamente; di conseguenza, il client SQL in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] genera un errore. Pertanto, questi valori vengono convertiti **NULL**.

## <a name="permissions"></a>Autorizzazioni

Richiede **EXECUTE ANY EXTERNAL SCRIPT** autorizzazione del database.  

## <a name="examples"></a>Esempi

In questa sezione contiene esempi di come utilizzare questa stored procedure per eseguire script R o Python utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)].

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Restituisce un set di dati R per SQL Server  

L'esempio seguente crea una stored procedure che utilizza **sp_execute_external_script** per restituire il set di dati Iris incluso in R per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

```sql
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>B. Generare un modello R basato su dati di SQL Server  

L'esempio seguente crea una stored procedure che utilizza **sp_execute_external_script** per generare un modello di iris e restituire il modello [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

> [!NOTE]
>  In questo esempio richiede l'installazione di anticipo del pacchetto e1071. Per ulteriori informazioni, vedere [installare pacchetti R aggiuntivi su SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md).

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
CREATE PROC generate_iris_model
AS
BEGIN
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;
GO
```

Per generare un modello simile tramite Python, è necessario modificare l'identificatore del linguaggio da `@language=N'R'` a `@language = N'Python'` e apportare le modifiche necessarie all'argomento `@script`. In caso contrario, tutti i parametri funzionano allo stesso modo di R.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Creare un modello di Python e generare punteggi da esso

Questo esempio illustra come usare sp\_execute\_external\_script per generare punteggi in un modello Python semplice. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Le intestazioni di colonna usate nel codice Python non vengono trasmesse a SQL Server. Usare quindi l'istruzione WITH RESULTS per specificare i nomi di colonna e i tipi di dati che SQL deve usare.

Per il punteggio, è anche possibile usare la funzione nativa [PREDICT](../../t-sql/queries/predict-transact-sql.md), che è in genere più veloce, perché consente di evitare la chiamata al runtime di Python o R.

## <a name="see-also"></a>Vedere anche

 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Tipi di dati e le librerie di Python](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Librerie di R e i tipi di dati](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [Servizi R per SQL Server](../../advanced-analytics/r/sql-server-r-services.md)   
 [Problemi noti per SQL Server apprendimento automatico servizi](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [CREARE una libreria esterna &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzione di configurazione del server external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [Oggetto External Scripts di SQL Server](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
