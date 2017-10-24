---
title: 'Lezione 5: Creare una simulazione semplice (procedura approfondita di data science) | Microsoft Docs'
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e5bbd69bba01da2aacd3b8912aebac6b4e1c28a1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-simple-simulation"></a>Creare una simulazione semplice

Fino ad oggi si usano già funzioni R progettate specificamente per lo spostamento dei dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e contesto di calcolo locale. Si supponga tuttavia di creare una funzione R personalizzata e di volerla eseguire nel contesto dei server?

È possibile chiamare una funzione arbitraria nel contesto del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando la funzione **rxExec** . È inoltre possibile utilizzare rxExec per distribuire in modo esplicito il lavoro tra core in un singolo nodo del server.

In questa lezione verrà usato il server remoto per creare una simulazione semplice. La simulazione non richiede alcuna [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati; l'esempio illustra solo come progettare una funzione personalizzata e quindi chiamare mediante la funzione rxExec.

Per un esempio più complesso di rxExec di utilizzo, vedere l'articolo: [il parallelismo con granularità grossolana con foreach e rxExec](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-function"></a>Creare la funzione

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
  
Verrà ora descritto come eseguire la funzione più volte per creare una simulazione che consente di determinare la probabilità di vincita.

## <a name="create-the-simulation"></a>Creare la simulazione

Per eseguire una funzione arbitraria nel contesto del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer, si chiama la funzione rxExec. Anche se rxExec supporta inoltre distribuita esecuzione di una funzione in parallelo tra nodi o core in un contesto di server, di seguito si userà solo per eseguire la funzione personalizzata nel server.

1. Chiamare la funzione personalizzata come argomento di rxExec, con alcuni altri parametri che modificano la simulazione.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - Usare l'argomento *timesToRun* per indicare il numero di volte per cui eseguire la funzione.  In questo caso, i dati vengono tirati 20 volte.
  
    - Gli argomenti *RNGseed* e *RNGkind* possono essere usati per controllare la generazione casuale dei numeri. Quando *RNGseed* è impostato su **auto**, viene inizializzato un flusso di numeri casuali parallelo in ogni computer di lavoro.
  
2. La funzione rxExec crea un elenco con un elemento per ogni esecuzione; Tuttavia, non verrà visualizzato quantità il problema fino a quando l'elenco è completo. Quando tutte le iterazioni vengono completate, la riga che inizia con `length` restituirà un valore.
  
    È quindi possibile andare al passaggio successivo per ottenere un riepilogo del record vincita-perdita.
  
3. Convertire l'elenco restituito in un vettore usando la funzione R `unlist` e creare un riepilogo dei risultati usando la funzione `table` .
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    I risultati saranno simili ai seguenti:
  
     *Perdita Win* *8 a 12*

## <a name="conclusions"></a>Conclusioni

In questa esercitazione è stata acquisita familiarità con queste attività:
  
-   Recupero dei dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da usare nelle analisi
  
-   Creazione e modifica di origini dati in R
  
-   Passaggio di modelli, dati e grafici tra la workstation e il server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
>  [!TIP]
> 
> Se si desidera sperimentare queste tecniche utilizzando un set di dati più grande di 10 milioni di osservazioni, i file di dati sono disponibili dal sito web analitica Revolution: [indice dei set di dati](http://packages.revolutionanalytics.com/datasets)
>   
> Per utilizzare nuovamente questa procedura dettagliata con i file di dati più grandi, scaricare i dati e modificare tutte le origini di dati come segue:
>  - Impostare le variabili *ccFraudCsv* e *ccScoreCsv* in modo che puntino ai nuovi file di dati
>  - Modificare il nome della tabella cui viene fatto riferimento in *sqlFraudTable* in *ccFraud10*
>  - Modificare il nome della tabella cui viene fatto riferimento in *sqlScoreTable* in *ccFraudScore10*

## <a name="previous-step"></a>Passaggio precedente

[Spostare dati tra SQL Server e i File con estensione XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)



