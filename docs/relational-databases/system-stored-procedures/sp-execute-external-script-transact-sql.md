---
title: sp_execute_external_script (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs: TSQL
helpviewer_keywords: sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d437e6e8d86aa648d9c6ef11a8ca04297cafbaf3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Esegue lo script fornito come argomento in una posizione esterna. Lo script deve essere scritto in una lingua supportata e registrata. La struttura della query è controllato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e gli utenti non possono eseguire operazioni arbitrarie nella query. Per eseguire **sp_execute_external_script**, è prima necessario abilitare gli script esterni tramite il `sp_configure 'external scripts enabled', 1;` istruzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_execute_external_script   
    @language = N'language,   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```  
  
## <a name="arguments"></a>Argomenti  
 @language= N'*language*'  
 Indica il linguaggio di scripting. *lingua* è **sysname**.  

 I valori validi sono `Python` o `R`. 
  
 @script= N'*script*'  
 Script di linguaggio esterno specificato come input un valore letterale o variabile. *script* è **nvarchar (max)**.  
  
 [ @input_data_1_name = N'*input_data_1_name*']  
 Specifica il nome della variabile utilizzata per rappresentare la query definita dal @input_data_1. Il tipo di dati della variabile nello script esterno dipende dalla lingua. In caso di R, la variabile di input è un frame di dati. Nel caso di Python, l'input deve essere in formato tabulare. *input_data_1_name* è **sysname**.  
  
 Valore predefinito è "InputDataSet".  
  
 [ @input_data_1 = N'*input_data_1*']  
 Specifica i dati di input utilizzati dallo script esterno sotto forma di un [!INCLUDE[tsql](../../includes/tsql-md.md)] query. *input_data_1* è **nvarchar (max)**.  
  
 [ @output_data_1_name = N'*output_data_1_name*']  
 Specifica il nome della variabile nello script esterno che contiene i dati da restituire al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo il completamento della chiamata alla stored procedure. Il tipo di dati della variabile nello script esterno dipende dalla lingua. Nel caso di R, l'output deve essere un frame di dati. Nel caso di Python, l'output deve essere un frame di dati pandas. *output_data_1_name* è **sysname**.  
  
 Valore predefinito è "OutputDataSet".  
  
 [ @parallel = 0 | 1 ]  
 Abilitare l'esecuzione parallela di script R, impostando il `@parallel` parametro su 1. Il valore predefinito per questo parametro è 0 (nessun parallelism).  
  
 Per gli script R che non utilizzano le funzioni RevoScaleR, utilizzando il `@parallel` parametro può essere utile per l'elaborazione di grandi set di dati, presupponendo che lo script può essere facilmente parallelizzato. Ad esempio, quando si utilizza l'oggetto R `predict` funzione con un modello per generare nuove stime, impostare `@parallel = 1` come hint per il motore di query. Se la query può essere eseguito in parallelo, le righe vengono distribuite in base al **MAXDOP** impostazione.  
  
 Se `@parallel = 1` e l'output come flusso direttamente al computer client, il `WITH RESULTS SETS` clausola è obbligatoria e deve essere specificato uno schema di output.  
  
 Per gli script R che utilizzano le funzioni RevoScaleR, l'elaborazione parallela viene gestito automaticamente e non è necessario specificare `@parallel = 1` per il **sp_execute_external_script** chiamare.  
  
 [ @params = N' *@parameter_name data_type* [OUT | OUTPUT] [,... n]']  
 Un elenco di dichiarazioni di parametro di input utilizzate nello script esterni.  
  
 [ @parameter1 = '*value1*' [OUT | OUTPUT] [,... n]]  
 Un elenco di valori per i parametri di input utilizzati dallo script esterno.  


## <a name="remarks"></a>Osservazioni  
 Usare **sp_execute_external_script** per eseguire gli script scritti in un linguaggio supportato, ad esempio R. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è costituito da un componente server installato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e da un set di strumenti della workstation e di librerie di connettività che connettono il data scientist all'ambiente ad alte prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Installare R Services (In-Database) durante la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione per abilitare l'esecuzione di script R. Per ulteriori informazioni, vedere [impostare nel Database SQL Server R Services &#40; &#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
 È possibile controllare le risorse usate da uno script esterno tramite la configurazione di un pool di risorse esterne. Per altre informazioni, vedere [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Informazioni sul carico di lavoro possono essere ottenute dalle viste del catalogo di resource governor, viste a gestione dinamica e contatori. Per ulteriori informazioni, vedere [viste del catalogo di Resource Governor &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Relative a resource Governor viste a gestione dinamica &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), e [esterna, SQL Server consente di generare script oggetto](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

Esecuzione di script di monitoraggio tramite [Sys.dm external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) e [Sys.dm external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

 Per impostazione predefinita, i set di risultati restituiti dalla stored procedure sono output con colonne senza nome. I nomi di colonna utilizzati all'interno di uno script sono locali per l'ambiente di scripting e non vengono riflesse nel set di risultati di output. Per denominare le colonne del set di risultati, utilizzare il `WITH RESULTS SET` clausola di [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 Oltre a restituire un set di risultati, è possibile restituire valori scalari di script R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando i parametri di OUTPUT. Nell'esempio seguente viene illustrato l'utilizzo del parametro OUTPUT:  
  
```  
DECLARE @model varbinary(max);  
EXEC sp_execute_external_script  
        @language = N'R'  
        , @script = N'  
    # build classification model to predict tipped or not  
    logitObj <- glm(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource, family = binomial(link=logit));  
  
    # First, serialize a model and put it into a database table  
    modelbin <- serialize(logitObj, NULL);  
    '  
        , @input_data_1 = N'  
SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance  
  FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)  
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d  
'  
        , @input_data_1_name = N'featureDataSource'  
        , @params = N'@modelbin varbinary(max) OUTPUT'  
        , @modelbin = @model OUTPUT;  
```  


## <a name="streaming-execution-for-r-script"></a>Il flusso di esecuzione per lo script R  
 Flusso di esecuzione di script R è supportato specificando `@r_rowsPerRead int parameter` in `@params` insieme.  Il flusso consente gli script R funzionare con i dati che non rientrano nella memoria. Ad esempio, se sono presenti miliardi di righe per l'assegnazione di punteggi con predict-funzione nuovo `@r_rowsPerRead` parametro può essere utilizzato per suddividere l'esecuzione in un flusso alla volta. Poiché questo parametro controlla il numero di righe che vengono inviati ai processi R, può essere utilizzato anche per limitare il numero di righe lette in una sola volta. Questo potrebbe essere utile per limitare i problemi di prestazioni di server se, ad esempio, Training del modello di grandi dimensioni. Si noti che questo parametro può essere usato solo nei casi in cui l'output dello script R non dipende da leggere oppure aprendo l'intero set di righe.  
  
 Sia il `@r_rowsPerRead` parametro per lo streaming e `@parallel` argomento deve essere considerato come hint. Per l'hint da applicare, deve essere possibile generare un piano di query SQL che include l'elaborazione parallela. In caso contrario, l'elaborazione parallela non è abilitato.  
  
> [!NOTE]  
>  Lo streaming e l'elaborazione parallela sono supportati solo in Enterprise Edition. È possibile includere i parametri nelle query in Standard Edition senza che venga generato un errore, ma i parametri non hanno effetto e gli script R eseguiti in un unico processo.  
  
## <a name="restrictions"></a>Restrizioni  
 **Tipi di dati:** i seguenti tipi di dati non sono supportati quando utilizzata nella query di input o i parametri di `sp_execute_external_script` procedure e restituito un errore di tipo non supportato.  
  
 In alternativa, **CAST** la colonna o un valore a un tipo supportato in [!INCLUDE[tsql](../../includes/tsql-md.md)] e inviarlo a R.  
  
-   **cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **ora**  
  
-   **sql_variant**  
  
-   **testo**, **immagine**  
  
-   **xml**  
  
-   **hierarchyid**, **geometry**, **geography**  
  
-   Tipi CLR definiti dall'utente  
  
 **DateTime** i valori nell'input sono convertiti in NA sul lato R per i valori che non rientrano nell'intervallo consentito di valori in R. questa operazione è necessaria perché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente a un intervallo più ampio di valori rispetto a quelle supportate nel linguaggio R.  
  
 I valori a virgola mobile (ad esempio, + Inf, -Inf, NaN) non sono supportati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anche se entrambi i linguaggi utilizzano IEEE 754. Comportamento corrente invia solo i valori per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] direttamente e come un risultato sqlclient in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] genera l'errore. Questi valori vengono convertiti in **NULL**.  
  
 Qualsiasi set di risultati di R che non può essere mappato a un [!INCLUDE[tsql](../../includes/tsql-md.md)] tipo di dati, viene restituita come NULL.  
  
## <a name="permissions"></a>Permissions  
 Richiede **EXECUTE ANY EXTERNAL SCRIPT** autorizzazione del database.  
  
## <a name="examples"></a>Esempi  
 In questa sezione contiene esempi di come utilizzare questa stored procedure per eseguire script R utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
### <a name="a-return-a-data-set-from-r-to-sql-server"></a>A. Restituisce un set di dati da R a SQL Server  
 L'esempio seguente crea una stored procedure che utilizza **sp_execute_external_script** per restituire un set di dati iris da R a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
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
go  
```  
  
### <a name="b-generate-a-model-based-on-data-from-sql-server"></a>B. Generare un modello basato su dati di SQL Server  
 L'esempio seguente crea una stored procedure che utilizza **sp_execute_external_script** per generare un modello di iris e restituire il modello [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  In questo esempio richiede l'installazione del pacchetto e1071. Per ulteriori informazioni, vedere [installare pacchetti R aggiuntivi su SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).  
  
```  
DROP PROC IF EXISTS generate_iris_model;  
go  
  
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
go  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Tipi di dati e le librerie di Python](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Librerie di R e i tipi di dati](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [Servizi R per SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Problemi noti per SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREARE una libreria esterna &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzione di configurazione Server External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [Oggetto External Scripts di SQL Server](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
  
