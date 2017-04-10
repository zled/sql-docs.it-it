---
title: "Lezione 3: Trasformare i dati con R (procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
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
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Lezione 3: Trasformare i dati con R (procedura approfondita per l&#39;analisi scientifica dei dati)
Il pacchetto **RevoScaleR** offre diverse funzioni per la trasformazione dei dati in varie fasi dell'analisi:  
  
-   **rxDataStep** può essere usato per creare e trasformare i subset di dati.  
  
-   **rxImport** supporta la trasformazione dei dati quando i dati vengono importati in o da un file XDF o un frame di dati in memoria.  
  
-   Sebbene non siano specificamente destinate allo spostamento dei dati, le funzioni **rxSummary**, **rxCube**, **rxLinMod** e **rxLogit** supportano tutte le trasformazioni dei dati.  
  
In questa sezione verrà illustrato come usare tali funzioni. Si inizia dalla funzione  *rxDataStep*.  
  
## Usare rxDataStep per trasformare le variabili  
La funzione *rxDataStep* elabora i dati un blocco alla volta, leggendo da un'origine dati e scrivendo su un'altra. È possibile specificare le colonne da trasformare, le trasformazioni da caricare e così via.  
  
Per rendere più interessante questo esempio, verrà usata una funzione da un altro pacchetto R per trasformare i dati.  Il pacchetto **Boot** è uno dei pacchetti "consigliati", per questo **Boot** è incluso in ogni distribuzione di R, ma non viene caricato automaticamente all'avvio. Di conseguenza, il pacchetto deve essere già disponibile nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che si sta usando con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Dal pacchetto **Boot**, si userà la funzione *inv.logit*, che calcola l'inverso di una funzione logit. Vale a dire, la funzione *inv.logit* converte una funzione logit di nuovo in una probabilità nella scala [0,1].  
  
> [!TIP]  
> Un altro modo per ottenere stime in questa scala consiste nell'impostare il parametro *type* su **response** nella chiamata originale a *rxPredict*.  
  
1.  Iniziare creando un'origine dati per contenere i dati destinati alla tabella *ccScoreOutput*.  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
2.  Aggiungere un'altra origine dati per contenere i dati per la tabella ccScoreOutput2.  
  
    ```R  
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
    La nuova tabella conterrà tutte le variabili della tabella *ccScoreOutput* precedente più la variabile appena creata.  
  
3.  Impostare il contesto di calcolo sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
  
    ```  
  
4.  Usare la funzione *rxSqlServerTableExists* per verificare se la tabella di output *ccScoreOutput2* esiste già e in tal caso usare la funzione *rxSqlServerDropTable* per eliminare la tabella.  
  
    ```R    
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")  
  
    ```  
  
5.  Chiamare la funzione *rxDataStep* e specificare le trasformazioni appropriate in un elenco.  
  
    ```R  
    rxDataStep(inData = sqlOutScoreDS,   
        outFile = sqlOutScoreDS2,         
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),        
        transformPackages = "boot",   
        overwrite = TRUE)    
    ```  
  
    Quando si definiscono le trasformazioni applicate a ogni colonna, è possibile specificare anche eventuali pacchetti di R aggiuntivi necessari per eseguire le trasformazioni.  Per altre informazioni sui tipi di trasformazioni che è possibile eseguire, vedere  [Transforming and Subsetting Data](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform) (Trasformazione e creazione di subset di dati)
  
6.  Chiamare *rxGetVarInfo* per visualizzare un riepilogo delle variabili nel set di dati nuovo.  
  
    ```R  
    rxGetVarInfo(sqlOutScoreDS2)  
    ```  
  
**Risultati**  
  
*Var 1: ccFraudLogitScore, tipo: numeric*  
*Var 2: state, tipo: carattere*  
*Var 3: gender, tipo: carattere*  
*Var 4: cardholder, tipo: carattere*  
*Var 5: balance, tipo: integer*  
*Var 6: numTrans, tipo: integer*  
*Var 7: numIntlTrans, tipo: integer*  
*Var 8: creditLine, tipo: integer*  
*Var 9: ccFraudProb, tipo: numeric*  
  
I punteggi della funzione logit originali vengono mantenuti, ma una nuova colonna, *ccFraudProb*, è stata aggiunta, nella quale i punteggi della funzione logit sono rappresentati come valori tra 0 e 1. 

Si noti che le variabili di fattore sono state scritte nella tabella *ccScoreOutput2* come dati di tipo carattere.  Se si vuole usarle come fattori nelle analisi successive, specificare i livelli tramite il parametro *colInfo*.  

  
## Passaggio successivo  
[Caricare i dati in memoria mediante rxImport &#40;approfondimento di analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Lezione 2: Creare ed eseguire script R &#40;procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
  
  
