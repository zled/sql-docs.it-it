---
title: "Usare il codice R in Transact-SQL (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 4e6fe30d-a105-4d5b-bc05-5e5204753847
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 28
---
# Usare il codice R in Transact-SQL (SQL Server R Services)
Questa esercitazione offre esempi concisi di sintassi per usare R in Servizi R per SQL Server.    
    
    
È un buon punto di partenza se non si ha familiarità con Servizi R per SQL Server e si vogliono acquisire nozioni di base per definire lo script R in una stored procedure T-SQL, usare i dati come input e definire gli output.    
    
**Prerequisiti:** per eseguire il codice R in Servizi R per SQL Server è necessaria la connessione a un'istanza di SQL Server nella quale è già installato R Services.     
    
## Parte 1 - Operazioni di base  

Nelle sezioni seguenti verrà illustrato come estendere la stored procedure tramite l'aggiunta di parametri e come configurare gli input e gli output.   
  
### 1.1. Verificare se R funziona in SQL Server  

Questa query usa la stored procedure di sistema [sp_execute_external_script](https://msdn.microsoft.com/library/mt604368.aspx), che chiama il codice R nel contesto di SQL Server. In questo esempio una query SQL viene passata come input a R e R restituisce il frame di dati corrispondente a SQL Server.     
    
1. Nel menu Start di Windows trovare Microsoft SQL Server Management Studio.     
2. Se non è disponibile, potrebbe essere necessario installarlo: [Scaricare SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).    
3. Nella finestra di dialogo **Connetti al server** digitare il nome di un server o di un'istanza in cui è abilitato Servizi R per SQL Server. Per questi esempi è importante accedere con un account in grado di creare un nuovo database, di eseguire istruzioni SELECT e di visualizzare tabelle.  Aprire una nuova finestra **Query** e incollare questa istruzione nella finestra, per verificare che tutto funzioni correttamente:    
    
    ```sql   
    exec sp_execute_external_script  
      @language =N'R',    
      @script=N'OutputDataSet<-InputDataSet',      
      @input_data_1 =N'select 1 as hello'    
      with result sets (([hello] int not null));    
    go    
    ```   
       
       
  
### <a name="bkmk_SSMSBasics"></a>1.2. Creare dati di prova semplici  
    
Prima di sviluppare una soluzione complessa di analisi scientifica dei dati, è importante comprendere le differenze tra SQL Server e R.    
  
1. Creare una tabella temporanea di dati eseguendo l'istruzione T-SQL seguente.     
   
    ```sql    
    CREATE TABLE #MyData ([Col1] int not null) ON [PRIMARY]    
    INSERT INTO #MyData   VALUES (1);    
    INSERT INTO #MyData   Values (10);    
    INSERT INTO #MyData   Values (100) ;    
    GO    
    ```    
5. Dopo aver creato la tabella, usare questa istruzione per eseguire una query sulla tabella:  
    ```sql  
    SELECT * from #MyData  
    ```  

**Risultati**  
  
|Col1 |   
|----|   
|1|   
|10|   
|100|   
  
    
### 1.3. Ottenere i dati di prova con il codice R    
  
Dopo aver creato la tabella, eseguire questa istruzione:  
  
  ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet <- InputDataSet;'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
    WITH RESULT SETS (([NewColName] int NOT NULL));
  ```    
    
L'istruzione restituisce gli stessi valori ma include un nome di colonna.  
  
**Note**    
- Il parametro *@language* definisce l'estensione del linguaggio da chiamare, in questo caso R.    
- Nel parametro *@script* è possibile definire i comandi da passare al runtime di R come testo Unicode. È anche possibile aggiungere il testo a una variabile di tipo **nvarchar** e chiamare la variabile.    
- La riga `N'OutputDataSet <- InputDataSet;'` passa i dati di input contenuti nel nome della variabile **InputDataSet** predefinita a R e poi ai risultati, senza eseguire altre operazioni. Si noti che R applica la distinzione tra maiuscole e minuscole. I nomi delle variabili di input e di output devono pertanto usare correttamente le maiuscole e le minuscole; in caso contrario verrà generato un errore.    
   
    
Per specificare una variabile di input o di output diversa, usare il parametro *@input_data_1_name* e digitare un identificatore SQL valido. In questo esempio i nomi delle variabili di input e output sono stati modificati rispettivamente in *SQLOut* e *SQLIn*:    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' SQLOut <- SQLIn;'    
    , @input_data_1 = N' SELECT 12 as Col;'    
    , @input_data_1_name  = N'SQLIn'    
    , @output_data_1_name =  N'SQLOut'    
    WITH RESULT SETS (([NewColName] int NOT NULL));    
```    
    
**Note**    
- È necessario specificare all'inizio i parametri obbligatori *@input_data_1* e *@output_data_1* per poter usare i parametri facoltativi *@input_data_1_name* e *@output_data_1_name*.    
- SQL e R non supportano gli stessi tipi di dati; di conseguenza, si verificano spesso conversioni di tipo al momento dell'invio di dati da SQL Server a R e viceversa. Per altre informazioni, vedere [Uso dei tipi di dati di R](../../advanced-analytics/r-services/working-with-r-data-types.md).    
- È possibile passare come parametro un solo set di dati di input ed è possibile restituire un solo set di dati. È tuttavia possibile chiamare altri set di dati dall'interno del codice R e restituire output di altri tipi oltre al set di dati. È anche possibile aggiungere la parola chiave OUTPUT a qualsiasi parametro in modo che venga restituito con i risultati.      
- Lo schema per il set di dati restituito (data.frame di R) è definito dall'istruzione `WITH RESULT SETS`. Provare a omettere l'istruzione e osservare i risultati.    
- I risultati tabulari vengono restituiti nel riquadro **Valori**. I messaggi restituiti dal runtime di R vengono visualizzati in **Messaggi**.     
  
### 1.4. Generare risultati con R    
    
È anche possibile generare valori usando solo lo script R, lasciando la stringa di query di input in _@input_data_1_ vuota. In alternativa, è possibile usare un'istruzione SQL SELECT valida come segnaposto. In questo caso non usare i risultati SQL nello script R.    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' mytextvariable <- c("hello", " ", "world");    
                         OutputDataSet <- as.data.frame(mytextvariable);'    
    , @input_data_1 = N' SELECT 1 as Temp1'    
    WITH RESULT SETS (([col] char(20) NOT NULL));    
```    
    
**Risultati**    
    
    
 |*col* |    
 |-----|    
 |*hello*|    
 |     |    
 |*world*|    
    

A questo punto, provare una versione diversa dell'esempio Hello World riportato sopra.     
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'    
    , @input_data_1 = N'  '    
    WITH RESULT SETS (([col1] varchar(20) , [col2] char(1), [col3] varchar(20) ));    
```    
    
    
**Risultati**    
    
    
 |*col1* | *col2* | *col3*|    
 |-------|-------|-------    
 |*hello*|  |*world*|    
    
Si noti che entrambe le istruzioni creano un vettore con tre valori, ma il secondo esempio restituisce tre colonne con una singola riga mentre il primo restituisce una singola colonna con tre righe. Per quale motivo?
    
Il motivo consiste nel fatto che R offre diversi elementi, ad esempio vettori, matrici ed elenchi, per le operazioni con colonne di valori. Questi strumenti, pur essendo potenti e flessibili, non soddisfano sempre le aspettative degli sviluppatori SQL.  Alcune funzioni R eseguono conversioni implicite di oggetti dati in elenchi e matrici.

> [!TIP] 
> 
> Verificare sempre i risultati e determinare il numero di colonne di dati che verranno restituite dal codice R e i tipi di dati corrispondenti.    
>     
> Indipendentemente dal fatto che il codice R usi matrici, vettori o un'altra struttura di dati, occorre ricordare che il risultato di output dallo script R alla stored procedure deve essere un **frame di dati**.      
  
  
## Parte 2 - Conversione dei dati e altri aspetti  
  
Questa sezione offre una panoramica rapida di alcuni aspetti da considerare quando si esegue il codice R in SQL Server.  
  
+ Tipi di dati: informazioni sulle opzioni di cast e conversione e sulle conversioni implicite  
+ Set di risultati tabulari: informazioni e previsioni sulle modifiche che R può apportare alle colonne e alle righe di dati    
  
### 2.1 Coercizione implicita dei tipi di dati  
    
R e SQL Server non usano gli stessi tipi di dati. È pertanto necessario tenere presenti le restrizioni relative al passaggio di dati tra R e il database. Negli esempi seguenti vengono illustrati alcuni aspetti comuni.   
    
    
1. Eseguire l'istruzione seguente per moltiplicare la matrice con R. In questo script la singola colonna di tre valori viene convertita in una matrice a colonna singola.  Quindi R applica implicitamente la coercizione della seconda variabile `y` in una matrice a colonna singola, per rendere conformi i due argomenti.  
    
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:15);    
      OutputDataSet <- as.data.frame(x %*% y);'    
     , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));    
    ```    
**Risultati**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|
 
  
      
2. A questo punto eseguire il prossimo script, simile al precedente, e verificare che cosa accade quando si modifica la lunghezza della matrice. 
   
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:14);    
      OutputDataSet <- as.data.frame(y %*% x);'    
      , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int ));    
    ```    

**Risultati**    
    
|Col1|
|---|    
|1542|    
  
  Questa volta R restituisce come risultato un valore singolo. Il risultato è valido perché i due argomenti sono vettori della stessa lunghezza. Pertanto R restituisce il prodotto interno come matrice.    
    
   
  
### 2.2 Unire o moltiplicare colonne di lunghezza diversa    
    
  
Lo script seguente illustra alcuni comportamenti di R che potrebbero non soddisfare le aspettative di uno sviluppatore di database.   
  
Lo script definisce una nuova matrice numerica di lunghezza 6 e la archivia nella variabile R `df1`. La matrice numerica viene quindi combinata con i numeri interi della tabella #MyData, che contiene 3 valori, per creare un nuovo frame di dati `df2`.   
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
               df1 <- as.data.frame( array(1:6) );    
               df2 <- as.data.frame( c( InputDataSet , df1 ));    
               OutputDataSet <- df2'    
    , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));    
```    
    
**Risultati**    
    
|*Col2*|*Col3*|    
|----|----|    
|1|1|    
|10|2|    
|100|3|    
|1|4|    
|10|5|    
|100|6|    
    
R include varie funzioni che creano output tabulari, ma tali funzioni eseguono operazioni molto diverse sui valori a seconda dell'oggetto dati R. Dato che questa stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] richiede che sia gli input sia gli output vengano passati come data.frame, sarà necessario usare spesso funzioni per convertire colonne e righe da e in frame di dati.    
    
In caso di dubbi sull'oggetto dati R che viene usato, aggiungere la funzione R `str()` o una delle funzioni di identificazione (`is.matrix`, `is.vector` e così via) per esaminare i risultati e ottenere lo schema effettivo e i tipi di valore.    
  
  
Per altre informazioni, vedere l'articolo di Hadley Wickham sulle [strutture di dati R](http://adv-r.had.co.nz/Data-structures.html).    
    
### 2.3 Identificare i tipi di dati e verificare gli schemi   
Appare evidente l'importanza di sapere esattamente quante colonne verranno restituite dal codice R e quale sarà il tipo di dati di ogni colonna.     
    
  
La funzione `str()` nello script R fa sì che lo schema dati dell'oggetto R venga restituito come messaggio informativo. 

Ad esempio l'istruzione seguente restituisce lo schema della tabella #MyData.    
        
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' str(InputDataSet);'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
      WITH RESULT SETS undefined;    
```    
    
    
**Risultati**    
    
*STDOUT message (s) from external script:*    
*'data.frame': 3 obs. of 1 variable:*    
*STDOUT message (s) from external script:*    
*$ Col1: int 1   10   100*    
    
  
  
### 2.4 Eseguire il cast o la conversione delle colonne   
  
Quando si inviano dati da SQL Server a R, è spesso necessario eseguire il cast o la conversione dei tipi di dati per garantire che vengano gestiti correttamente.    
  
Quando si usa una query SQL come input per il codice R, i dati subiscono varie trasformazioni:    
- SQL Server inserisce i dati ricevuti della query nel processo R gestito dal servizio Launchpad e li converte in una rappresentazione interna.    
- Il runtime R carica i dati in una variabile data.frame ed esegue a sua volta operazioni sui dati.    
- Il motore di database restituisce i dati a Management Studio o a un altro client usando i tipi di dati SQL Server.  
    
1. Eseguire la seguente query nel data warehouse AdventureWorksDW. La query di dati di input definisce una tabella di dati di vendite da usare per la creazione di una previsione.   
  
    ```sql    
    execute sp_execute_external_script    
       @language = N'R'    
      , @script = N' str(InputDataSet);'    
      , @input_data_1 = N'
           SELECT ReportingDate    
         , CAST(ModelRegion as varchar(50)) as ProductSeries    
         , Amount    
           FROM [AdventureworksDW2016CTP3].[dbo].[vTimeSeries]     
           WHERE [ModelRegion] = ''M200 Europe''    
           ORDER BY ReportingDate ASC ;'    
        WITH RESULT SETS undefined;    
    ```    
  
2. A questo punto esaminare i risultati della funzione `str` per vedere come sono stati gestiti in R i dati di input.
      
**Risultati**    
    
  *STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:*    
  *STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"*    
  *STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1 ...*    
  *STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950*    
    
    
**Note**    
    
- Alcuni tipi di dati di SQL Server non sono supportati da R. Per evitare errori, è pertanto consigliabile specificare le colonne singolarmente ed eseguire il cast di alcune colonne.    
- Il predicato stringa nella clausola WHERE deve essere racchiuso tra due set di virgolette singole.    
- La colonna datetime è stata restituita come tipo di dati R **POSIXct**.    
- La colonna [ProductSeries] è stata identificata (correttamente) come **factor**.    
     
  
### 2.5 Usare più input   
È possibile passare come parametro un solo set di dati di input. Tuttavia è possibile chiamare altri set di dati dall'interno del codice R mediante RODBC.     
  
Il codice dell'esempio seguente effettua una chiamata al pacchetto RODBC specificando i dati in un'istruzione SELECT.    
    
```sql    
    @script = N' 
       <other R code here>;    
       library(RODBC);    
       connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");        dbhandle <- odbcDriverConnect(connStr)    
       OutputDataSet <- sqlQuery(dbhandle, "SELECT * from <table_name>");    
       <more R code combining the data>'    
```

È consigliabile usare RODBC per ottenere da SQL Server set di dati più piccoli, ad esempio ricerche o elenchi di fattori, e usare il parametro @input_data per ottenere set di dati più grandi, come quelli usati per il training di un modello. 


### 2.6 Generare più output

In SQL Server 2016 l'output di R dalla stored procedure sp_execute_external_script è limitato a un singolo data.frame o set di dati. (Questa limitazione potrebbe essere rimossa in futuro.)   
Tuttavia è possibile restituire output di altri tipi unitamente al set di dati. Ad esempio è possibile eseguire il training di un modello usando come input un singolo set di dati, ma restituire come output una tabella di statistiche e come oggetto il modello sottoposto a training.    
    
È anche possibile aggiungere la parola chiave `OUTPUT` a qualsiasi parametro di input in modo che venga restituito con i risultati.   
    
### 2.7 Elaborazione parallela    
    
Se si usa un set di dati di grandi dimensioni e la query SQL che ottiene i dati può generare un piano di query parallelo, è possibile eseguire lo script R in parallelo impostando il parametro *@parallel* su 1. Ciò risulta in genere utile quando si valuta un set di risultati di grandi dimensioni. Se si usa questa opzione, è necessario specificare in anticipo lo schema dei risultati di output mediante WITH RESULT SETS.    
    
Tuttavia questo parametro non avrà alcun effetto se si esegue il training di un modello che usa tutte le righe. Per tali casi è consigliabile usare i pacchetti **ScaleR**. Tali pacchetti possono distribuire automaticamente l'elaborazione senza che sia necessario specificare *@parallel =1* nella chiamata a sp_execute_external_script.    
    
      
  
## Parte 3. Wrapping di funzioni R in stored procedure  
  
R può includere molte funzioni statistiche avanzate, la cui riproduzione in T-SQL potrebbe richiedere l'uso di codice complesso.  Con R Services è tuttavia possibile eseguire script di utilità R in una stored procedure per supportare attività quali:   
    
- Applicare funzioni matematiche e statistiche di R ai dati di SQL Server    
    
- Creare funzioni con valori di tabella o funzioni scalari che usano codice R    
     

 In genere è necessario incapsulare le chiamate alle funzioni R nelle stored procedure per semplificare il passaggio dei parametri. Per illustrare questo processo, la stessa funzione viene usata nel codice R, in una chiamata della stored procedure ad hoc per sp_execute_external_script, e in una stored procedure che è possibile usare per impostare i parametri della funzione R.
 
      
### 3.1. Generare numeri casuali  
  
L'istruzione seguente usa una delle funzioni R del pacchetto `stats`, caricato per impostazione predefinita quando viene installato R Services. La funzione `rnorm` visualizzata di seguito genera 20 numeri casuali con una distribuzione normale, in base a una media pari a 100.    

Di seguito il funzionamento del codice R.

```r
as.data.frame(rnorm(20, mean = 100));
```

Questa istruzione chiama la funzione di T-SQL e restituisce i risultati a SQL Server.  
   
```sql    
EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N' 
         OutputDataSet <- as.data.frame(rnorm(20, mean = 100));'    
    , @input_data_1 = N'   ;'    
      WITH RESULT SETS (([Density] float NOT NULL));    
```    

Successivamente, viene eseguito il wrapping della stored procedure in un'altra stored procedure per semplificare il passaggio dei parametri. È necessario definire i parametri di input nell'argomento _@params_ ed eseguire il mapping di ogni parametro al parametro R corrispondente in base al nome.

```sql
CREATE PROCEDURE MyRNorm (@mynorm int, @mymean int)
AS
    EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynorm, mymean));'    
    , @input_data_1 = N'   ;' 
    , @params = N' @mynorm int, @mymean int'  
    , @mynorm = @mynorm
    , @mymean = @mymean
    WITH RESULT SETS (([Density] float NOT NULL));    
```

Chiamare la nuova stored procedure e passare i valori.

```sql
exec MyRNorm @mynorm = 20,@mymean = 100
```  
    
### 3.2 Altri usi delle funzioni di utilità R  
  
Questo esempio chiama uno dei pacchetti di utilità R e ne usa la funzione `memory.limit()` per ottenere memoria per l'ambiente corrente. Il pacchetto `utils` è installato ma non caricato per impostazione predefinita.    
    
```sql    
execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
        library(utils);    
        mymemory <- memory.limit();    
        OutputDataSet <- as.data.frame(mymemory);'    
    , @input_data_1 = N' ;'    
     WITH RESULT SETS (([Col1] int not null));    
```    

Nell'esempio successivo si ottiene la lunghezza massima dei numeri interi supportati nel computer corrente, usando la funzione R .Machine, e si restituiscono i risultati alla console.

```R
localmax <- .Machine$integer.max;
localmax;
```

```sql
execute sp_execute_external_script
  @language = N'R'
  , @script = N'
      localmax <- .Machine$integer.max;
      OutputDataSet <- as.data.frame(localmax);'
  , @input_data_1 = N'select [Col1]  from #MyData;'
  WITH RESULT SETS (([MaxIntValue] int not null));
```     
    
Non è comunque sempre detto che R sia la scelta migliore per eseguire questo processo. È possibile che le operazioni basate sui set in SQL Server siano molto più efficienti rispetto ad alcune operazioni che i data scientist sono soliti eseguire in R. Per un esempio in cui sono messe a confronto le funzioni personalizzate di R e di T-SQL, vedere la [procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md). 

È consigliabile valutare caso per caso se è più opportuno eseguire una determinata operazione con R, con T-SQL o con un altro strumento.    
    
    
    
### Risorse aggiuntive    
    
[Procedura approfondita per l'analisi scientifica dei dati: uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md): questa procedura dettagliata offre un'esperienza pratica, con attività comuni di analisi scientifica dei dati    
[Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md): questa procedura dettagliata illustra un processo di sviluppo e distribuzione che bilancia gli approcci R e SQL       
[Analisi avanzata per lo sviluppatore SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md): illustra la messa in funzione completa del modello per gli sviluppatori SQL     
    
    
    
    
