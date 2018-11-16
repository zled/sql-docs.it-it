---
title: Creare una simulazione semplice (amp;#40;procedura approfondita di R e SQL) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b0db5fdfd177f1303432659f7a96b0fbf111c000
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698239"
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>Creare una simulazione semplice (amp;#40;procedura approfondita di R e SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo è il passaggio finale dell'esercitazione approfondita di Data Science, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Finora è stato usato funzioni R che vengono progettate in modo specifico per lo spostamento dei dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e contesto di calcolo locale. Si supponga tuttavia di creare una funzione R personalizzata e di volerla eseguire nel contesto dei server?

È possibile chiamare una funzione arbitraria nel contesto del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando la funzione [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) . È anche possibile usare **rxExec** per distribuire in modo esplicito il lavoro nei diversi core in un singolo server.

In questa lezione, si utilizza il server remoto per creare una simulazione semplice. La simulazione non richiede dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'esempio si limita a illustrare come creare una funzione personalizzata ed eseguirne la chiamata usando la funzione **rxExec** .

Per un esempio più complesso di utilizzo **rxExec**, vedere questo articolo: [parallelismo granulosità grossolana con foreach e rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>Creare la funzione personalizzata

Un comune gioco di casinò consiste nel tirare un paio di dati con le regole seguenti:

- Se si raggiunge un punteggio di 7 o 11 nel tiro iniziale, si vince.
- Se si raggiunge un punteggio di 2, 3 o 12, si perde.
- Se si raggiunge un punteggio di 4, 5, 6, 8, 9 o 10 è possibile continuare a tirare fino a quando non si ottiene lo stesso punteggio e si vince o si ottiene 7 e si perde.

Il gioco può essere facilmente simulato in R creando una funzione personalizzata ed eseguendola più volte.

1.  Creare la funzione personalizzata usando il codice R seguente:
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result \<- "Loss" }
                else if (count > 1 && roll == 7 )
                { result \<- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Per simulare una singola giocata ai dadi, eseguire la funzione.
  
    ```R
    rollDice()
    ```
  
    Si ha vinto o si ha perso?
  
Ora vediamo come è possibile usare **rxExec** per eseguire la funzione più volte, per creare una simulazione che consente di determinare la probabilità di vincita.

## <a name="create-the-simulation"></a>Creare la simulazione

Per eseguire una funzione arbitraria nel contesto del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , viene eseguita una chiamata alla funzione **rxExec** . Sebbene **rxExec** inoltre supporta l'esecuzione distribuita di una funzione in parallelo su nodi o core in un contesto di server, in questo caso, la funzione personalizzata in esecuzione sul computer SQL Server.

1. Chiamare la funzione personalizzata come argomento al **rxExec**, in combinazione con altri parametri che modificano la simulazione.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - Usare l'argomento *timesToRun* per indicare il numero di volte per cui eseguire la funzione.  In questo caso, i dati vengono tirati 20 volte.
  
    - Gli argomenti *RNGseed* e *RNGkind* possono essere usati per controllare la generazione casuale dei numeri. Quando *RNGseed* è impostato su **auto**, viene inizializzato un flusso di numeri casuali parallelo in ogni computer di lavoro.
  
2. La funzione **rxExec** crea un elenco con un elemento per ogni esecuzione; tuttavia, non verranno eseguite molte operazioni fino a quando l'elenco non è completato. Quando tutte le iterazioni vengono completate, la riga che inizia con `length` restituirà un valore.
  
    È quindi possibile andare al passaggio successivo per ottenere un riepilogo del record vincita-perdita.
  
3. Convertire l'elenco restituito in un vettore usando la funzione R `unlist` e creare un riepilogo dei risultati usando la funzione `table` .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    I risultati saranno simili ai seguenti:
  
     *Perdita vincita* *12 8*

## <a name="conclusions"></a>Conclusioni

In questa esercitazione è stata acquisita familiarità con queste attività:
  
-   Recupero dei dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da usare nelle analisi
  
-   Creazione e modifica di origini dati in R
  
-   Passaggio di modelli, dati e grafici tra la workstation e il server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  

Se si desidera provare a usare queste tecniche usando un set di dati più grande di 10 milioni di osservazioni, i file di dati sono disponibili dal sito web analitica Revolution: [indice del set di dati](https://packages.revolutionanalytics.com/datasets)

Per usare nuovamente questa procedura dettagliata con i file di dati più grandi, scaricare i dati e quindi modificare ognuna delle origini dati come segue:

1. Modificare le variabili `ccFraudCsv` e `ccScoreCsv` in modo che punti ai file di dati nuovi
2. Modificare il nome della tabella a cui fa riferimento *sqlFraudTable* a `ccFraud10`
3. Modificare il nome della tabella a cui fa riferimento *sqlScoreTable* a `ccFraudScore10`

## <a name="additional-samples"></a>Esempi aggiuntivi

Ora che si è apprese l'uso di funzioni RevoScaler per passare e trasformare i dati e contesti di calcolo, vedere queste esercitazioni:

[Esercitazioni di R per Machine Learning Services](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>Passaggio precedente

[Spostare i dati tra SQL Server e file XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
