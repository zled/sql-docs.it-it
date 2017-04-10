---
title: "R e ottimizzazione dei dati (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6104878-ed19-47a7-ac37-21e4d6e2a1af
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# R e ottimizzazione dei dati (R Services)
In questo argomento vengono descritti i metodi per aggiornare il codice R per migliorare le prestazioni o evitare i problemi noti.

## Contesto di calcolo

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] possono essere di __locale__ o __SQL__ contesto di calcolo durante l'esecuzione di analisi. Quando si utilizza il __locale__ contesto di calcolo, analisi viene eseguita sul computer client e devono essere recuperati i dati da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] in rete. Il calo di prestazioni sostenuti per il trasferimento tramite rete dipende dalle dimensioni dei dati trasferiti, velocità della rete e di altri trasferimenti di rete che si verificano nello stesso momento.

Se il contesto di calcolo è __SQL Server__, quindi le funzioni analitiche vengono eseguite all'interno di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. I dati sono locali per l'attività di analisi, pertanto non è stato introdotto alcun overhead di rete. 

Quando si lavora con grandi set di dati, è consigliabile utilizzare sempre il contesto di calcolo SQL.

## Fattori

Il linguaggio R converte stringhe dalle tabelle in fattori. Richiedere molti oggetti origine dati `colInfo` come parametro per controllare come le colonne vengono considerate. Ad esempio, `c(“fruit” = c(type = “factor”, levels=as.character(c(1:3)), newLevels=c(“apple”, “orange”, “banana”)))` verrà utilizzano numeri interi 1, 2 e 3 da una tabella e considerarli come fattori con livelli `apple`, `orange`, e `banana`. 

Data Scientist spesso utilizzano variabili di fattore in loro formula; Tuttavia, utilizzando i fattori quando i dati di origine sono un numero intero verrà influisce sulle prestazioni come numeri interi vengono convertiti in stringhe in fase di esecuzione. Tuttavia, se la colonna contiene stringhe, è possibile specificare i livelli preventivamente utilizzando `colInfo`. In questo caso, l'istruzione equivalente sarebbe  `c(“fruit” = c(type = “factor”, levels= c(“apple”, “orange”, “banana”)))`, che considera le stringhe come fattori come vengono letti. 

Per evitare conversioni in fase di esecuzione, è consigliabile archiviare i livelli come numeri interi nella tabella e il relativo utilizzo come descritto nel primo esempio di formula. Se non esiste alcuna differenza semantica la generazione del modello, questo approccio può comportare prestazioni migliorate.

## Trasformazioni dei dati

Gli scienziati dati utilizzano spesso le funzioni di trasformazione scritte in R come parte dell'analisi. Le funzioni di trasformazione devono essere applicate a ogni riga recuperata dalla tabella. In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], questa trasformazione viene eseguito in modalità batch e comporta la comunicazione tra il motore di analisi e l'interprete R. Per eseguire la trasformazione, i dati vengono spostati da SQL per il motore di analisi e quindi il processo dell'interprete R e viceversa. Pertanto, utilizzando le trasformazioni possono personalizzatedell significativi effetti negativi sulle prestazioni dell'algoritmo, a seconda della quantità di dati coinvolti.

È più efficiente disporre di tutte le colonne necessarie della tabella o vista prima di eseguire analisi, in questo modo si evita di trasformazioni durante il calcolo. Se non è possibile aggiungere ulteriori colonne alle tabelle esistenti, è consigliabile creare un'altra tabella o vista con le colonne trasformate e utilizzare una query appropriata per recuperare i dati.

## Batch

Origine dati SQL (`RxSqlServerData`) è un'opzione per indicare le dimensioni del batch utilizzando il parametro `rowsPerRead`. Questo parametro specifica il numero di righe da elaborare contemporaneamente. In fase di esecuzione, gli algoritmi leggerà il numero di righe in ogni batch specificato. Per impostazione predefinita, il valore di questo parametro è impostato su 50.000, per garantire che gli algoritmi possono eseguire anche nei computer con memoria insufficiente. Se nel computer è disponibile memoria sufficiente, l'aumento del valore di 500.000 o anche un milione può garantire prestazioni migliori, in particolare per tabelle di grandi dimensioni. 

Aumentando questo valore può non sempre producono risultati migliori è possibile che alcuni esperimenti per determinare il valore ottimale. I vantaggi di questo oggetto sarà più evidenti in un set di dati di grandi dimensioni con più processi (`numTasks` impostata su un valore maggiore di `1`).

## Elaborazione parallela

Per migliorare le prestazioni dell'esecuzione di funzioni analitiche in rx [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] si basa sull'elaborazione parallela utilizzando i core disponibili nel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] macchina. Esistono due modi per ottenere la parallelizzazione con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]:

* Quando si utilizza il `sp_execute_external_script` stored procedure per eseguire uno script R, impostare il `@parallel` parametro `1`. Ciò è utile per gli script R che non utilizzano funzioni RevoScaleR, che in genere sono precedute da "rx". Se lo script utilizza le funzioni RevoScaleR, l'elaborazione parallela viene gestito automaticamente e non è necessario impostare `@parallel` a `1`.

    Se lo script R può essere eseguite in parallelo e se il [!INCLUDE[tsql_md](../../includes/tsql-md.md)] query possono essere eseguite in parallelo, quindi [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] creerà più processi paralleli (fino al __massimo grado di parallelismo MAXDOP__ impostazione per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)],) ed eseguire lo script stesso in tutti i processi. Ogni processo riceve solo una parte dei dati, in modo che questo non è utile con gli script che devono visualizzare tutti i dati, ad esempio durante il training di un modello. Tuttavia, è utile quando si eseguono attività, ad esempio stima batch in parallelo. Per ulteriori informazioni sull'utilizzo di parallelismo con [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), vedere il __suggerimenti per utenti esperti: l'elaborazione parallela__ sezione [utilizzando codice R in Transact-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md).

* Quando si utilizzano funzioni di ricezione con un contesto di calcolo di SQL Server, impostare `numTasks` al numero di processi che si desidera creare. Il numero effettivo di processi creati è determinato da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], e può essere inferiore a quello richiesto. Il numero di processi creati non può mai essere più __MAXDOP__.

    Se lo script R può essere eseguite in parallelo e se il [!INCLUDE[tsql_md](../../includes/tsql-md.md)] query possono essere eseguite in parallelo, quindi [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] creerà più processi paralleli quando si esegue le funzioni di ricezione.

Il numero di processi che verrà creato dipende da un'ampia gamma di fattori quali la governance delle risorse, l'utilizzo corrente di risorse e altre sessioni e il piano di esecuzione di query per la query utilizzata con lo script R. 

### Parallelizzazione delle query

Per garantire che i dati possono essere analizzati in parallelo, la query utilizzata per recuperare i dati debba essere formulata in modo tale che è possibile eseguire il rendering per l'esecuzione parallela. 

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] supporta l'utilizzo di origini dati SQL tramite `RxSqlServerData` per specificare l'origine. L'origine può essere una tabella o una query. Ad esempio, i seguenti esempi di codice che definiscono entrambi un oggetto di origine di dati R basato su una query SQL:
~~~~
RxSqlServerData(table=”airline”, connectionString = sqlConnString)
~~~~

~~~~
RxSqlServerData(sqlquery=”select [ArrDelay],[CRSDepTime],[DayOfWeek] from airlineWithIndex where rowNum <= 100000”, connectionString = sqlConnString)
~~~~ 

Gli algoritmi di analisi il pull dei grandi volumi di dati dalle tabelle, è importante assicurarsi che la query alla `RxSqlServerData` è ottimizzato per l'esecuzione parallela. Una query che generano un piano di esecuzione parallela può comportare un singolo processo per il calcolo.

[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] può essere utilizzato per analizzare il piano di esecuzione e migliorare le prestazioni della query. Ad esempio, un indice mancante in una tabella può influire sul tempo impiegato per eseguire una query. Vedere [monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md) Per ulteriori informazioni.

Un altro controllo che possa influire sulle prestazioni è quando la query recupera colonne rispetto a quelle necessarie. Ad esempio, se una formula dipende solo 3 colonne e la tabella include 30 colonne, non utilizzare una query, ad esempio `select *` o uno che consente di selezionare più colonne di quelle necessarie.

> [!NOTE]
> Se viene specificata una tabella nell'origine dati anziché una query, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] internamente determina le colonne necessarie per recuperare dalla tabella; tuttavia, questo approccio è improbabile che l'esecuzione in parallelo.

## Parametri degli algoritmi

Molti algoritmi di formazione rx supportano i parametri per controllare come viene generato il modello di training. Mentre la precisione e la correttezza del modello è importante, le prestazioni dell'algoritmo possono essere altrettanto importante. È possibile modificare i parametri di training del modello parametersthe per aumentare la velocità di calcolo e in molti casi, potrebbe essere in grado di migliorare le prestazioni senza la riduzione della precisione o la correttezza. 

Ad esempio, `rxDTree` supporta il `maxDepth` parametro che controlla la profondità massima dell'albero. Come `maxDepth` è aumentato, le prestazioni possono ridursi, pertanto è importante analizzare i vantaggi di aumentare la profondità e l'impatto sulle prestazioni. 

Uno dei parametri che possono essere utilizzati con `rxLinMod` e `rxLogit` è il `cube` argomento. In questo argomento può essere utilizzato quando la variabile dipendente prima della formula è una variabile di fattore. Se `cube` è impostato su `TRUE`, la regressione viene eseguita utilizzando un inversa partizionata, può essere più veloce e utilizzano meno memoria dei calcoli di regressione standard. Se la formula contiene un numero elevato di variabili, il miglioramento delle prestazioni può essere significativo.

Il [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) manuale dell'utente dispone di informazioni utili per controllare il modello adatto ai vari algoritmi. Ad esempio, con `rxDTree` è possibile controllare il bilanciamento tra precisione complessità e la stima di tempo modificando i parametri, ad esempio `maxNumBins`, `maxDepth`, `maxComplete`, e `maxSurrogate`. L'aumento della profondità per oltre 10 o 15 può rendere il calcolo molto costosa.

Per ulteriori informazioni sull'ottimizzazione delle prestazioni per `rxDForest` e `rxDTree`, vedere [per rxDForest/rxDTree opzioni di ottimizzazione delle prestazioni](https://support.microsoft.com/kb/3104235).

## Modello e stima

Una volta completata la formazione e il modello migliore selezionato, è consigliabile archiviare il modello nel database in modo che sia immediatamente disponibile per le stime. Per l'elaborazione di transazioni online che richiede la stima, caricamento del modello di pre-calcolato dal database per la stima è molto efficiente. Gli script di esempio utilizzano questo approccio per serializzare e archiviare il modello in una tabella di database. Per la stima, il modello è deserializzato dal database.

Alcuni modelli generati dagli algoritmi, ad esempio lm o glm possono essere notevole, soprattutto se utilizzato in un set di dati di grandi dimensioni. Esistono delle limitazioni di dimensione per i dati che possono essere archiviati in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. È necessario eliminare il modello prima di archiviarla nel database.

> [!NOTE] Se si verifica uno scenario importante veloce stima utilizzando un modello archiviato e l'integrazione di analisi in un'applicazione, è consigliabile __DeployR__. Può essere utilizzato per integrare facilmente analisi R all'interno delle applicazioni web, desktop, mobili e dashboard. In particolare, è adatto per l'archiviazione di un modello e l'esecuzione di stima di singola riga utilizzando il modello archiviato. Per ulteriori informazioni, vedere [su DeployR](https://msdn.microsoft.com/microsoft-r/rserver/deployr-about).

## Vedere anche
[Governance delle risorse](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

[CREARE POOL DI RISORSE ESTERNE](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [Guida di ottimizzazione delle prestazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [Configurazione di SQL Server per i servizi di R](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [Case Study di prestazioni](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 