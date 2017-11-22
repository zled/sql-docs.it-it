---
title: Conversione di codice R per l'uso in R Services | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 06/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d403b716d6be6c571f4de76a25ba3f6f7f5c4e8d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="converting-r-code-for-use-in-r-services"></a>Conversione di codice R per l'uso in R Services

Quando si sposta il codice R da R Studio o un altro ambiente di SQL Server, spesso il codice funziona senza ulteriori modifiche quando aggiunti il  *@script*  parametro di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Questo è particolarmente vero se è stata sviluppata la soluzione usando il **RevoScaleR** funzioni, rendendo relativamente semplice modificare i contesti di esecuzione.

In genere si preferirà tuttavia modificare il codice R per l'esecuzione in SQL Server, sia per sfruttare i vantaggi di una maggiore integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia per evitare costosi trasferimenti di dati.

Per esempi di esecuzione di codice R in SQL Server, vedere queste procedure dettagliate:

+ [Analitica nel Database per gli sviluppatori di SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) di seguito viene illustrato come visualizzare il codice R più modulare mediante il wrapping nelle stored procedure

+ [Soluzione di analisi scientifica dei dati end-to-End](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) include un confronto di progettazione delle funzioni di R e T-SQL

## <a name="how-the-data-science-process-changes-in-sql-server"></a>Come il processo di analisi scientifica dei dati viene modificato in SQL Server

Quando si lavora in un ambiente di sviluppo R dedicato, ad esempio [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] o RStudio, il flusso di lavoro tipico al pull dei dati nel computer, quindi analizzare i dati in modo iterativo e quindi scrivere o visualizzare i risultati. Tuttavia, quando il codice R autonomo viene eseguita la migrazione a SQL Server, la maggior parte di questo processo può essere semplificata o delegata ad altri strumenti di SQL Server. Inoltre, tale così possibile migliorare le prestazioni in molti casi.

| Codice esterno | R in SQL Server |
|-------|-------|
| Inserire dati| Definire i dati di input come una query SQL. Evitare lo spostamento dei dati. |
| Riepilogare e visualizzare i dati| Grafici possono essere esportati come immagini o inviati a una workstation remota.|
|Progettazione delle funzionalità| Usare R nel database se non si desidera modificare il codice, ma esamina l'ottimizzazione delle query. Verificare se può risultare più efficiente per chiamare le funzioni di T-SQL o funzioni definite dall'utente personalizzato.|
|Pulizia dei dati come parte del processo di analisi| Eseguire progettazione di funzionalità, estrazione di funzioni e la pulizia dei dati in anticipo come parte di flussi di lavoro dati.|
|Eseguire l'output delle stime in un file| Stime di output a una tabella per evitare lo spostamento dei dati. Incapsulamento stimare funzioni nelle stored procedure per l'accesso diretto dalle applicazioni.|

## <a name="best-practices"></a>Procedure consigliate

+ Prendere nota in anticipo delle dipendenze, ad esempio dei pacchetti necessari. In un ambiente di sviluppo e di test è possibile installare i pacchetti come parte del codice, ma è meglio evitare di farlo in un ambiente di produzione. Inviare una notifica all'amministratore in modo che i pacchetti possano essere installati e testati prima di distribuire il codice.

+ Creare un elenco di controllo dei possibili problemi con i tipi di dati. Lo schema dei risultati previsti in ogni sezione del codice del documento.

+ Identificare le origini dati primarie, ad esempio i dati di training modello o i dati di input per le stime, rispetto alle origini secondarie, ad esempio i fattori, le variabili di raggruppamento aggiuntive e così via. Eseguire il mapping dei set di dati di maggiori dimensioni al parametro di input di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ Modificare le istruzioni di dati di input per lavorare direttamente nel database. Anziché lo spostamento dei dati in un file CSV locale o effettua più chiamate ODBC, è possibile ottenere prestazioni migliori tramite query SQL o le viste che possono essere eseguite direttamente nel database, evitando spostamenti di dati.

+ Usare i piani di query di SQL Server per identificare le attività che possono essere eseguite in parallelo. Se la query di input può essere eseguito in parallelo, impostare `@parallel=1` come parte di che gli argomenti [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). L'elaborazione parallela con questo flag è in genere possibile ogni volta che SQL Server può usare le tabelle partizionate o distribuire una query tra più processi e aggregare i risultati alla fine.

  L'elaborazione parallela con questo flag in genere non è possibile se si esegue il training dei modelli usando algoritmi che richiedono la lettura di tutti i dati o se è necessario creare aggregati.

+ Ove possibile sostituire le funzioni R convenzionali con funzioni **ScaleR** che supportano l'esecuzione distribuita. Per ulteriori informazioni, vedere [funzioni di R di scala e confronto di Base R](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Riesaminare il codice R per determinare se ci sono passaggi che possono essere eseguiti in modo indipendente o più efficiente, usando una chiamata alle stored procedure separata. È ad esempio possibile decidere di eseguire separatamente la progettazione o l'estrazione delle funzionalità e di aggiungere i valori in una nuova colonna. 

  Utilizzare T-SQL anziché codice R per i calcoli basati su set. Per un esempio di una soluzione di R che confronta funzioni definite dall'utente e R per attività di progettazione di funzionalità, vedere [procedura dettagliata End-to-End di analisi scientifica dei dati](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Utilizzare il pacchetto R **sqlrutils** per convertire il codice in una singola funzione con definito chiaramente input e output, che possono essere facilmente mappati a parametri di stored procedure. Per ulteriori informazioni ed esempi, vedere [SqlRUtils](../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).


## <a name="restrictions"></a>Restrizioni

 Tenere presenti le restrizioni seguenti quando si converte il codice R:

### <a name="data-types"></a>Tipi di dati

-   Sono supportati tutti i tipi di dati R. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta tuttavia una maggiore varietà di tipi di dati rispetto a R, quindi alcune conversioni implicite dei tipi di dati vengono eseguite quando si inviano dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a R e viceversa. Inoltre potrebbe essere necessario eseguire il cast in modo esplicito o convertire alcuni dati.

- I valori NULL sono supportati. Usa R la `na` costrutto di dati per rappresentare un valore mancante, che è simile a un valore null.

Per ulteriori informazioni, vedere [tipi di dati e delle librerie R](../r/r-libraries-and-data-types.md).

### <a name="inputs-and-outputs"></a>Input e output

+ È possibile definire un solo set di dati di input come parte dei parametri di stored procedure. Questa query di input per la stored procedure può essere una singola istruzione SELECT valida. È consigliabile utilizzare l'input per il set di dati più grande e ottenere un set di dati più piccoli in base alle esigenze usando le chiamate a RODBC.

+ Chiamate di stored procedure precedute da EXECUTE non possono essere utilizzate come input per [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ È necessario eseguire il mapping di tutte le colonne nel set di dati di input alle variabili nello script R. Il mapping delle variabili viene eseguito automaticamente in base al nome. Si supponga, ad esempio, che lo script R contiene una formula simile alla seguente:
    
    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
     Se il set di dati di input non contiene colonne con i nomi corrispondenti ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour e DayOfWeek, viene generato un errore.

+ È anche possibile specificare più parametri scalari come input. È tuttavia necessario eseguire il mapping delle variabili passate come parametri della stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) alle variabili nel codice R. Per impostazione predefinita, il mapping delle variabili viene eseguito in base al nome.

+ Per includere variabili di input scalari nell'output del codice R, è sufficiente aggiungere la parola chiave **OUTPUT** quando si definisce la variabile.

+ In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] il codice R è limitato all'output di un singolo sei di dati come oggetto data.frame. È anche possibile tuttavia creare più output scalari, inclusi tracciati in formato binario e modelli in formato varbinary.

+ È in genere possibile creare l'output del set di dati restituito dallo script R senza dover specificare i nomi delle colonne di output, usando l'opzione WITH RESULT SETS UNDEFINED. È tuttavia necessario eseguire il mapping delle variabili nello script R di cui si vuole creare l'output ai parametri di output di SQL.

+ Se lo script R usa l'argomento `@parallel=1`, è necessario definire lo schema di output perché SQL Server potrebbe creare più processi per eseguire la query in parallelo, raccogliendo i risultati alla fine. Pertanto, lo schema di output deve essere definito prima di possono creare i processi paralleli.

### <a name="dependencies"></a>Dipendenze

 + Evitare di installare pacchetti dal codice R. In SQL Server, i pacchetti devono essere installati in anticipo.
 
  Assicurarsi di installare i pacchetti nella libreria di pacchetto predefinito utilizzata dai servizi di Machine Learning. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](../r/r-package-management-for-sql-server-r-services.md)
