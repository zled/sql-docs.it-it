---
title: Converti il codice R per l'utilizzo in servizi di SQL Server Machine Learning | Documenti di Microsoft"
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf3d272bd4b5c1227aa8a1969727ea17f5b65596
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>Converti il codice R per l'esecuzione nelle istanze di SQL Server (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce indicazioni di alto livello su come modificare il codice R per funzionare in SQL Server. 

Quando si sposta il codice R da R Studio o un altro ambiente di SQL Server, in genere il codice funziona senza ulteriori modifiche: ad esempio, se il codice è semplice, ad esempio una funzione che accetta alcuni input e restituisce un valore. È inoltre più semplice per le soluzioni di porta che utilizzano il **RevoScaleR** o **MicrosoftML** pacchetti, che supportano l'esecuzione in contesti di esecuzione diversi con modifiche minime.

Tuttavia, il codice potrebbe richiedere modifiche sostanziali se una qualsiasi delle condizioni seguenti:

+ Utilizzare librerie R che accedono alla rete o che non può essere installato in SQL Server.
+ Il codice effettua una chiamata a origini dati all'esterno di SQL Server, ad esempio fogli di lavoro di Excel, i file nelle condivisioni e altri database. 
+ Si desidera eseguire il codice di *@script* parametro di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) e inoltre i parametri per la stored procedure.
+ La soluzione originale include più passaggi che potrebbero essere più efficienti in un ambiente di produzione se eseguite in modo indipendente, ad esempio la preparazione dei dati o di progettazione di funzionalità rispetto al modello di training, creazione di report o di punteggio.
+ Si desidera migliorare ottimizzare le prestazioni modificando le librerie, tramite l'esecuzione parallela, o offload alcune operazioni di elaborazione a SQL Server. 

## <a name="step-1-plan-requirements-and-resources"></a>Passaggio 1. Requisiti del piano e risorse

**Pacchetti**

+ Determinare quali pacchetti sono necessari e verificare che funzionino in SQL Server.
 
+ Installare i pacchetti in anticipo, nella libreria di pacchetto predefinito utilizzata dai servizi di Machine Learning. Librerie utente non sono supportate.

**Origini dei dati** 

+ Se si desidera incorporare il codice R in [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), identificare le origini di dati primario e secondario. 

    + **Primario** origini dei dati sono grandi set di dati, ad esempio dati di training del modello o di input per le stime. Pianificazione eseguire il mapping del set di dati più grande per il parametro di input di [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + **Secondario** origini dei dati sono in genere più piccoli set di dati, quali gli elenchi di fattori o variabili di raggruppamento aggiuntive. 
    
    Attualmente, sp_execute_external_script supporta solo un singolo set di dati come input per la stored procedure. Tuttavia, è possibile aggiungere più input scalare o binary.

    Chiamate di stored procedure precedute da EXECUTE non possono essere utilizzate come input per [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). È possibile utilizzare le query, viste o qualsiasi altra istruzione SELECT valida.

+ Determinare gli output, che è necessario. Se si esegue codice R con sp_execute_external_script, la stored procedure può restituire solo un frame di dati di conseguenza. Tuttavia, possibile generare più output scalare, inclusi grafici e modelli in formato binario, nonché altri valori scalari derivati dal codice R o SQL parametri.

**Tipi di dati**

+ Creare un elenco di controllo dei possibili problemi con i tipi di dati.

    Tutti i tipi di dati R sono supportati da servizi di SQL Server machine Learning. Tuttavia, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta una più ampia gamma di tipi di dati rispetto a R. Di conseguenza, alcune conversioni di tipi di dati impliciti vengono eseguite quando si inviano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati a R e viceversa. Potrebbe essere necessario eseguire il cast in modo esplicito o convertire alcuni dati. 

    I valori NULL sono supportati. Tuttavia, R Usa il `na` costrutto di dati per rappresentare un valore mancante, che è simile a un valore null.

+ Provare a eliminare la dipendenza da dati che non possono essere utilizzati da r, ad esempio, rowid e tipi di dati GUID da SQL Server non possono essere utilizzati da R e generano errori.

    Per ulteriori informazioni, vedere [tipi di dati e delle librerie R](../r/r-libraries-and-data-types.md).

## <a name="step-2-convert-or-repackage-code"></a>Passaggio 2. Convertire o ricreare il pacchetto di codice

Quanto si modifica il codice varia a seconda che si desidera inviare il codice R da un client remoto per l'esecuzione nel contesto di calcolo di SQL Server o intende distribuire il codice come parte di una stored procedure, che può fornire migliori prestazioni e sicurezza dei dati. Wrapping del codice in una stored procedure, vengono imposti alcuni requisiti aggiuntivi. 

+ Definire i dati di input primari come una query SQL, laddove possibile, per evitare lo spostamento dei dati.

+ Quando si esegue una stored procedure R, è possibile passare attraverso più **scalare** input. Per i parametri che si desidera utilizzare nell'output, aggiungere il **OUTPUT** (parola chiave). 

    Ad esempio, l'input scalare seguente `@model_name` contiene il nome del modello, che è anche l'output nella rispettiva colonna nei risultati:

    ```SQL
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ Tutte le variabili passate come parametri della stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) deve essere mappato a variabili nel codice R. Per impostazione predefinita, il mapping delle variabili viene eseguito in base al nome.

    Inoltre, tutte le colonne del set di dati di input devono essere mappate a variabili dello script R.  Si supponga, ad esempio, che lo script R contiene una formula simile alla seguente:

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    Se il set di dati di input non contiene colonne con i nomi corrispondenti ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour e DayOfWeek, viene generato un errore.

+ In alcuni casi, uno schema di output deve essere definito in anticipo per i risultati.

    Per inserire i dati in una tabella, ad esempio, è necessario utilizzare il **con SET di risultati** clausola per specificare lo schema.

    Lo schema di output è necessario anche se lo script R utilizza l'argomento `@parallel=1`. perché SQL Server potrebbe creare più processi per eseguire la query in parallelo, raccogliendo i risultati alla fine. Pertanto, è necessario preparare lo schema di output prima di possono creare i processi paralleli.
    
    In altri casi, è possibile omettere lo schema di risultati utilizzando l'opzione **con RESULT SETS UNDEFINED**. Questa istruzione restituisce il set di dati dallo script R senza le colonne di denominazione o specificando i tipi di dati SQL.

+ Si consiglia di generare dati timing o rilevamento utilizzando T-SQL anziché di R.

    Ad esempio, è possibile passare l'ora di sistema o altre informazioni utilizzate per il controllo e l'archiviazione con l'aggiunta di una chiamata di T-SQL che viene passata tramite i risultati, anziché la generazione di dati simili nello script R. 

**Migliorare le prestazioni e sicurezza**

+ Evitare di scrivere risultati intermedi in un file o stime. Scrivere le stime a una tabella, per evitare lo spostamento dei dati.

+ Eseguire tutte le query in anticipo ed esaminare i piani di query di SQL Server per identificare le attività che possono essere eseguite in parallelo.

    Se la query di input può essere eseguito in parallelo, impostare `@parallel=1` come parte di che gli argomenti [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). 

    L'elaborazione parallela con questo flag è in genere possibile ogni volta che SQL Server può usare le tabelle partizionate o distribuire una query tra più processi e aggregare i risultati alla fine. L'elaborazione parallela con questo flag in genere non è possibile se si esegue il training dei modelli usando algoritmi che richiedono la lettura di tutti i dati o se è necessario creare aggregati.

+ Riesaminare il codice R per determinare se ci sono passaggi che possono essere eseguiti in modo indipendente o più efficiente, usando una chiamata alle stored procedure separata. Ad esempio, è possibile ottenere migliori prestazioni mediante Progettazione funzionalità o l'estrazione di funzioni separatamente e il salvataggio dei valori in una tabella.

+ È possibile utilizzare T-SQL anziché codice R per i calcoli basati su set.

    Ad esempio, questa soluzione di R Mostra funzioni definite dall'utente di T-SQL e R è possibile eseguire la stessa attività di progettazione di funzionalità: [procedura dettagliata End-to-End di analisi scientifica dei dati](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Se possibile, sostituire convenzionale R le funzioni con **ScaleR** funzioni che supportano l'esecuzione distribuita. Per ulteriori informazioni, vedere [funzioni di R di scala e confronto di Base R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Con uno sviluppatore di database per determinare come migliorare le prestazioni tramite funzionalità di SQL Server, ad esempio, vedere [tabelle con ottimizzazione per la memoria](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables), o, se si dispone dell'edizione Enterprise, [Resource Governor](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)).

    Per altre informazioni, vedere [SQL Server ottimizzazione suggerimenti e consigli per i servizi Analitica](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>Passaggio 3. Preparare per la distribuzione

+ Inviare una notifica all'amministratore in modo che i pacchetti possano essere installati e testati prima di distribuire il codice. 

    In un ambiente di sviluppo, potrebbe essere sufficiente installare i pacchetti come parte del codice, ma questa è una procedura non valida in un ambiente di produzione. 

    Librerie utente non sono supportate, indipendentemente dal fatto che si utilizza una stored procedure o eseguire il codice R nel contesto di calcolo di SQL Server.

**Creare un pacchetto del codice R in una stored procedure**

+ Se il codice è relativamente semplice, è possibile incorporarlo in una funzione definita dall'utente di T-SQL senza alcuna modifica, come descritto in questi esempi:

    + [Creare una funzione di R che viene eseguito in rxExec](..\tutorials\deepdive-create-a-simple-simulation.md)
    + [Funzionalità di progettazione utilizzando T-SQL e R](..\tutorials\sqldev-create-data-features-using-t-sql.md)

+ Se il codice è più complesso, utilizzare il pacchetto R **sqlrutils** per convertire il codice. Questo pacchetto è stato progettato per consentire agli utenti di R esperti di scrivere codice buona stored procedure. 

    Il primo passaggio è necessario riscrivere il codice R come una singola funzione con definito chiaramente input e output.

    Utilizzare quindi la **sqlrutils** pacchetto per generare l'input e output nel formato corretto. Il **sqlrutils** pacchetto genera il codice della stored procedure completa e può anche registrare la stored procedure nel database. 

    Per ulteriori informazioni ed esempi, vedere [SqlRUtils](../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md).

**Integrazione con altri flussi di lavoro**

+ Sfruttare gli strumenti di T-SQL e processi ETL. Eseguire progettazione di funzionalità, estrazione di funzioni e la pulizia dei dati in anticipo come parte di flussi di lavoro dati.

    Quando si lavora in un ambiente di sviluppo R dedicato, ad esempio [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] o RStudio, è possibile effettuare il pull dei dati nel computer, analizzare i dati in modo iterativo e quindi scrivere o visualizzare i risultati. 
    
    Tuttavia, quando il codice R autonomo viene eseguita la migrazione a SQL Server, la maggior parte di questo processo può essere semplificata o delegata ad altri strumenti di SQL Server. 

+ Utilizzare le strategie di visualizzazione protetta e asincrona.

    Gli utenti di SQL Server spesso non è possibile accedere a file nel server e gli strumenti SQL client non supportano in genere il dispositivo di grafica R. Se si generano grafici o altre immagini come parte della soluzione, è consigliabile esportare i grafici come dati binari e salvataggio in una tabella o la scrittura.

+ Eseguire il wrapping di funzioni di stima e assegnazione dei punteggi nelle stored procedure per l'accesso diretto dalle applicazioni.

### <a name="other-resources"></a>Altre risorse

Per visualizzare gli esempi di come è possibile distribuire una soluzione di R in SQL Server, vedere gli esempi seguenti:

+ [Compilare un modello predittivo per le aziende di noleggio ski con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Analitica nel Database per gli sviluppatori di SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md) viene illustrato come effettuare il codice R più modulare eseguendo il wrapping nelle stored procedure

+ [Soluzione di analisi scientifica dei dati end-to-End](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) include un confronto di progettazione delle funzioni di R e T-SQL
