---
title: "Lezione 5: Creare una simulazione semplice (procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
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
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Lezione 5: Creare una simulazione semplice (procedura approfondita per l&#39;analisi scientifica dei dati)
Fino ad ora sono state usate le funzioni R diSQL Server R Services specificatamente progettate per lo spostamento dei dati tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un contesto di calcolo locale. Si supponga tuttavia di creare una funzione R personalizzata e di volerla eseguire nel contesto dei server?  
  
È possibile chiamare una funzione arbitraria nel contesto del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando la funzione *rxExec*. È anche possibile usare *rxExec* per distribuire in modo esplicito il lavoro nei diversi core in un nodo di server singolo.  
  
In questa lezione verrà usato il server remoto per creare una simulazione semplice. La simulazione non richiede dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'esempio si limita a illustrare come creare una funzione personalizzata ed eseguirne la chiamata usando la funzione *rxExec*.  
  
Per un esempio più complesso dell'uso di *rxExec*, vedere l'articolo all'indirizzo [http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)  
  
## Creare la funzione  
Un comune gioco di casinò consiste nel tirare un paio di dati con le regole seguenti:  
  
-   Se si raggiunge un punteggio di 7 o 11 nel tiro iniziale, si vince.  
  
-   Se si raggiunge un punteggio di 2, 3 o 12, si perde.  
  
-   Se si raggiunge un punteggio di 4, 5, 6, 8, 9 o 10 è possibile continuare a tirare fino a quando non si ottiene lo stesso punteggio e si vince o si ottiene 7 e si perde.  
  
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
                { result <- "Loss" }    
                else if (count > 1 && roll == 7 )   
                { result <- "Loss" }    
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
  
## Creare la simulazione  
Per eseguire una funzione arbitraria nel contesto del computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], viene eseguita una chiamata alla funzione *rxExec*. Sebbene *rxExec* supporti anche l'esecuzione distribuita di una funzione in parallelo su nodi o core in un contesto di server, in questo caso viene usato soltanto per eseguire la funzione personalizzata nel server.  
  
1.  Chiamare la funzione personalizzata come argomento di *rxExec* con altri parametri che modificano la simulazione.  
  
    ```R  
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")   
    length(sqlServerExec)   
    ```  
  
    -   Usare l'argomento *timesToRun* per indicare il numero di volte per cui eseguire la funzione.  In questo caso, i dati vengono tirati 20 volte.  
  
    -   Gli argomenti *RNGseed* e *RNGkind* possono essere usati per controllare la generazione casuale dei numeri. Quando *RNGseed* è impostato su **auto**, viene inizializzato un flusso di numeri casuali parallelo in ogni computer di lavoro.  
  
2.  La funzione *rxExec* crea un elenco con un elemento per ogni esecuzione; tuttavia, non verranno eseguite molte operazioni fino a quando l'elenco non è completato. Quando tutte le iterazioni vengono completate, la riga che inizia con `length` restituirà un valore.  
  
    È quindi possibile andare al passaggio successivo per ottenere un riepilogo del record vincita-perdita.  
  
3.  Convertire l'elenco restituito in un vettore usando la funzione R *unlist* e creare un riepilogo dei risultati usando la funzione *table*.  
  
    ```R  
    table(unlist(sqlServerExec))  
    ```  
  
    I risultati saranno simili ai seguenti:  
  
     *Perdita  Vincita*   
     *12  8*  
  
## Conclusioni  
In questa esercitazione è stata acquisita familiarità con queste attività:  
  
-   Recupero dei dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da usare nelle analisi  
  
-   Creazione e modifica di origini dati in R  
  
-   Passaggio di modelli, dati e grafici tra la workstation e il server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
>  [!TIP]
> 
> Se si vuole esercitarsi con queste tecniche usando un set di dati di dimensioni maggiori di 10 milioni di osservazioni, i file di dati sono disponibili in [http://packages.revolutionanalytics.com/datasets](http://packages.revolutionanalytics.com/datasets).  
>   
> Per usare nuovamente questa procedura dettagliata con i file di dati di dimensioni maggiori, limitarsi a scaricare i dati e quindi modificare le origini dati come segue:   
>  -   Impostare le variabili *ccFraudCsv* e *ccScoreCsv* in modo che puntino ai nuovi file di dati     
>  -   Modificare il nome della tabella cui viene fatto riferimento in *sqlFraudTable* in *ccFraud10*    
>  -   Modificare il nome della tabella cui viene fatto riferimento in *sqlScoreTable* in *ccFraudScore10*   
  
## Passaggio precedente  
[Spostare i dati tra SQL Server e file XDF &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
  
  
