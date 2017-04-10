---
title: "Conversione di codice R per l&#39;utilizzo nei servizi di R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Conversione di codice R per l&#39;utilizzo nei servizi di R
Quando si sposta codice R da R Studio o un altro ambiente di SQL Server, spesso il codice funzionerà senza ulteriori modifiche quando aggiunto al *@script* parametro di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Ciò è particolarmente vero se è stata sviluppata la soluzione con le funzioni di ridimensionamento, rendendo relativamente semplice modificare i contesti di esecuzione.    
    
Tuttavia, in genere si dovranno modificare il codice R per l'esecuzione in SQL Server, sia in grado di sfruttare la maggiore integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ed evitare costoso trasferimento dei dati.   
   
   
## Risorse  
  
Per visualizzare esempi di come è possibile eseguire codice R in SQL Server, vedere queste procedure dettagliate:   
+ [Analisi dei dati nel Database per gli sviluppatori di SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)    
  Viene illustrato come effettuare il codice R più modulare includendola in stored procedure  
+ [Soluzione di analisi scientifica dei dati end-to-End](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)    
  Include un confronto della progettazione di funzionalità in R e T-SQL

## Modifiche al processo di analisi scientifica dei dati in SQL Server  
  
Quando si lavora [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)], RStudio, o altro ambiente, è un tipico flusso di lavoro per estrarre i dati nel computer, analizzare i dati in modo interattivo, quindi scrivere o visualizzare i risultati. Tuttavia, quando viene eseguita la migrazione di codice autonomo R a SQL Server, gran parte di questo processo può essere semplificata o delegare ad altri strumenti di SQL Server:

| Codice esterno | R in SQL Server |
|-------|-------|
| Inserire dati| Definire i dati di input come una query SQL all'interno del database | 
| Riepilogare e visualizzare i dati| Nessuna modifica; grafici possono essere esportati come immagini o inviati a un computer remoto|
|Progettazione di funzionalità| È possibile usare R nel database, ma può risultare più efficace per chiamare le funzioni di T-SQL o funzioni definite dall'utente personalizzata|
|Parte del processo di analisi di pulizia dei dati| Pulizia dei dati può essere delegata a processi ETL ed eseguita in anticipo|
|Stime di output in un file| Restituire stime alla tabella o eseguire il wrapping `predict` nelle stored procedure per l'accesso diretto da parte di applicazioni|
  

  
## Procedure consigliate  
  
+ Prendere nota delle dipendenze, ad esempio i pacchetti necessari, in anticipo. In un ambiente di test e sviluppo, potrebbe essere necessario installare pacchetti come parte del codice, ma questa è una pessima abitudine in un ambiente di produzione. Avvisare l'amministratore in modo che i pacchetti possono essere installati e testati prima di distribuire il codice.  
+ Rendere un elenco di controllo di dati possibili problemi di tipo. Documentare gli schemi dei risultati previsti in ogni sezione del codice.  
+ Identificare le origini di dati primario, ad esempio dati di training del modello o dati di input per le stime e secondarie origini, ad esempio fattori, le variabili di raggruppamento aggiuntive e così via. Eseguire il mapping del set di dati più grande per il parametro di input di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
+ Modificare le istruzioni di dati di input per lavorare direttamente nel database. Anziché lo spostamento dei dati in un file CSV locale o eseguendo più chiamate ODBC, si otterrà prestazioni migliori tramite query SQL o le viste che possono essere eseguite direttamente nel database, evitando lo spostamento dei dati.  
+ Utilizzare piani di query di SQL Server per identificare le attività che possono essere eseguite in parallelo. Se la query di input può essere eseguite in parallelo, impostare `@parallel=1` come parte di sp_execute_external_script che gli argomenti. Con questo flag di elaborazione parallela è in genere possibile ogni volta che SQL Server può funzionare con le tabelle partizionate o distribuire una query tra più processi e aggregare i risultati alla fine. 
   Con questo flag di elaborazione parallela in genere non è possibile se non si utilizzano algoritmi che richiedono tutti i dati da leggere i modelli di training, o se è necessario creare le aggregazioni. 
+ Dove possibile, sostituire le funzioni R convenzionale con **ridimensionamento** funzioni che supportano l'esecuzione distribuita. Per ulteriori informazioni, vedere [confronto delle funzioni in scala R e R CRAN](Summary%20of%20rx%20Functions.md).
+ Esaminare il codice R per determinare se vi sono passaggi che possono essere eseguiti in modo indipendente o eseguiti in modo più efficiente, utilizzando una chiamata di stored procedure specifica. Ad esempio, si potrebbe decidere di eseguire separatamente l'estrazione di progettazione o la funzionalità di funzionalità e aggiungere i valori in una nuova colonna. Utilizzare T-SQL anziché il codice R per i calcoli basati su set. Per un esempio di una soluzione R che confronta le prestazioni delle funzioni definite dall'utente e R per attività di progettazione di funzionalità, vedere l'esercitazione: [procedura dettagliata End-to-End di analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md).  
  
    
## Restrizioni    
 Tenere presente le restrizioni seguenti durante la conversione del codice R:    
   
**Tipi di dati**    
-   Tutti i tipi di dati R sono supportati. Tuttavia, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta una varietà di tipi di dati maggiore rispetto a R, pertanto alcune conversioni di tipi di dati impliciti vengono eseguiti durante l'invio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati in R e viceversa. Inoltre è sottoposto a cast in modo esplicito o convertire alcuni dati.    
    
- I valori NULL sono supportati. R utilizza la `na` dati costruire per rappresentare i valori mancanti, che è simile ai valori null.    
    
- Per ulteriori informazioni, vedere [utilizzo di tipi di dati R](../../advanced-analytics/r-services/working-with-r-data-types.md).    
 
 **Input e output**   
+ È possibile definire un solo set di dati di input come parte di parametri della stored procedure. Questa query di input per la stored procedure può essere qualsiasi singola istruzione SELECT valida. È consigliabile utilizzare l'input per il set di dati principale e ottenere set di dati più piccoli, se necessario, tramite chiamate a RODBC. 

+ Stored procedure chiamate precedute da EXECUTE non possono essere utilizzate come input per sp_execute_external_script.    
    
+ Tutte le colonne nel set di dati di input devono essere mappate a variabili nello script R. Le variabili vengono mappate automaticamente in base al nome. Si supponga ad esempio che script R contiene una formula simile al seguente:    
    
    ```    
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek    
    ```    
    
     Verrà generato un errore se il set di dati di input non contiene colonne con i nomi corrispondenti ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour e DayOfWeek.    

+ È anche possibile fornire più parametri scalari come input. Tuttavia, tutte le variabili passate come parametri della stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) deve essere mappato a variabili nel codice R. Per impostazione predefinita, il mapping delle variabili in base al nome.
+ Per includere le variabili scalari di input nell'output del codice R, aggiungere solo i **OUTPUT** parola chiave quando si definisce la variabile.             
+ In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], il codice R è limitato per l'output di un singolo set di dati come oggetto frame. Tuttavia, è anche possibile produrre più scalare restituisce, tra cui tracciati in formato binario e modelli in formato varbinary.    
    
+ In genere, è possibile restituire il set di dati restituiti dallo script R senza dover specificare i nomi delle colonne di output, tramite l'opzione con RESULT SETS UNDEFINED. Tuttavia, tutte le variabili nello script R che si desidera restituire devono essere mappate ai parametri di output SQL.
    
+ Se lo script R utilizza l'argomento `@parallel=1`, è necessario definire lo schema di output. Il motivo è che più processi potrebbero essere creati da SQL Server per eseguire la query in parallelo, con i risultati raccolti alla fine. Pertanto, è necessario definire lo schema di output prima di possono creare i processi paralleli.

 **Dipendenze**
 + Evitare di installare pacchetti dal codice R. In SQL Server, pacchetti devono essere installati in anticipo.  
  
  
  

