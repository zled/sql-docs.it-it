---
title: "Lezione 2: Creare ed eseguire script R (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/26/2016"
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
ms.assetid: 51e8e66f-a0a5-4e96-aa71-f5c870e6d0d4
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Lezione 2: Creare ed eseguire script R (Procedura approfondita per l&#39;analisi scientifica dei dati)
Dopo aver impostato le origini dati e stabilito uno o più contesti di calcolo, è possibile usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire alcuni script R avanzati.  In questa lezione si userà il contesto di calcolo server per eseguire alcune attività comuni di apprendimento automatico:  
  
-   Visualizzare dati e generare alcune statistiche di riepilogo    
-   Creare un modello di regressione lineare    
-   Creare un modello di regressione logistica    
-   Assegnare punteggi ai nuovi dati e creare un istogramma dei punteggi  
  
## Impostare il contesto di calcolo server  
Prima di eseguire qualsiasi codice R è necessario specificare il contesto di calcolo *current* o *active*.  
  
1.  Per attivare un contesto di calcolo già definito tramite R, usare la funzione *rxSetComputeContext* come illustrato di seguito:  
  
    ```R  
    rxSetComputeContext(sqlCompute)   
    ```  
  
    Dopo l'esecuzione di questa istruzione, tutti i calcoli successivi si svolgeranno nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indicato nel parametro *sqlCompute*.  
  
  
2.  Se si decide di eseguire il codice R sulla propria workstation, reimpostare il contesto di calcolo sul computer locale mediante la parola chiave  **local** .  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
    Per l'elenco delle parole chiave supportate da questa funzione digitare `help("rxSetComputeContext")` da una riga di comando di R.  
  
> [!NOTE]  
> Dopo che è stato specificato, il contesto di calcolo resta attivo fino a quando non lo si modifica. Tuttavia, qualsiasi script R *non* eseguibile in un contesto server remoto verrà eseguito localmente.  
  
## Calcolare statistiche di riepilogo  
Per capire come funziona il contesto di calcolo, usare la sorgente dati *sqlFraudDS* per generare statistiche di riepilogo.  Tenere presente che l'oggetto origine dati definisce solo i dati che saranno usati. Non modifica il contesto di calcolo.

+ Per eseguire il riepilogo localmente, usare *rxSetComputeContext* e specificare la parola chiave "local".
+ Per creare gli stessi calcoli nel computer con SQL Server, passare al contesto di calcolo SQL definito in precedenza.  

  
1.  Chiamare la funzione *rxSummary* e passare gli argomenti obbligatori, ad esempio la formula e l'origine dati, e assegnare i risultati alla variabile *sumOut*.  
  
    ```R  
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)  
  
    ```  
  
    Con il linguaggio R sono disponibili molte funzioni di riepilogo. La funzione *rxSummary* supporta tuttavia l'esecuzione in diversi contesti remoti tra cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Per altre informazioni su funzioni simili, vedere [Data Summaries ](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) (Riepiloghi di dati) e le informazioni di [riferimento a ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler).
  
2.  Al termine dell'elaborazione, è possibile stampare il contenuto della variabile *sumOut* nella console.  
  
    ```R  
    sumOut  
    ```  
  
    > [!NOTE]  
    > Non stampare i risultati prima che siano stati restituiti dal computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Potrebbe verificarsi un errore.  
  
  
**Risultati**  
  
*Summary Statistics Results for: ~gender + balance + numTrans +*   
 *numIntlTrans + creditLine*    
 *Data: sqlFraudDS (RxSqlServerData Data Source)*    
 *Number of valid observations: 10000*    
 *Name  Mean    StdDev  Min Max ValidObs    MissingObs*    
 *balance       4075.0318 3926.558714            0   25626 100000*    
 *numTrans        29.1061   26.619923 0     100 10000    0           100000*    
 *numIntlTrans     4.0868    8.726757 0      60 10000    0           100000*    
 *creditLine       9.1856    9.870364 1      75 10000    0          100000 Category Counts for gender*    
 *Number of categories: 2*    
 *Number of valid observations: 10000*   
 *Number of missing observations: 0*    
 *gender Counts*    
 *Male   6154*    
  *Female 3846*  
  
## Aggiungere valori di colonna minimo e massimo  
Le statistiche di riepilogo calcolate hanno restituito informazioni utili sui dati da inserire nell'origine dati per l'uso in ulteriori calcoli. Ad esempio, i valori minimo e massimo possono essere usati per calcolare istogrammi. Si decide quindi di aggiungere i valori minimo e massimo all'origine dati *RxSqlServerData*.  
  
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] include funzioni ottimizzate che convertono in modo molto efficiente dati integer in dati fattore di categoria.  
  
1.  Per iniziare si configurano alcune variabili temporanee.  
  
    ```R  
    sumDF <- sumOut$sDataFrame   
    var <- sumDF$Name    
    ```  
  
2.  Usare la variabile *ccColInfo* creata in precedenza per definire le colonne nell'origine dati.  
  
    Saranno aggiunte anche nuove colonne calcolate (*numTrans*, *numIntlTrans* e *creditLine*) alla raccolta di colonne.  
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",  
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")), 
        cardholder = list(type = "factor",  
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
  
    ```  
  
3.  Dopo aver aggiornato la raccolta di colonne è possibile applicare l'istruzione seguente per creare una versione aggiornata dell'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definita in precedenza.  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlFraudTable,   
        colInfo = ccColInfo,        
        rowsPerRead = sqlRowsPerRead)   
    ```  
  
    L'origine dati *sqlFraudDS* include ora le nuove colonne aggiunte in *ccColInfo*.  
  
Queste modifiche interessano solo l'oggetto origine dati in R, mentre nella tabella di database non sono stati ancora scritti nuovi dati. È tuttavia possibile usare i dati acquisiti nella variabile *sumOut* per creare visualizzazioni e riepiloghi. Il passaggio successivo illustrerà come eseguire questa operazione usando i contesti di calcolo. 

> [!TIP]
> Se non si ricorda il contesto di calcolo che si sta usando, scegliere `rxGetComputeContext()`.  Se il valore restituito è `RxLocalSeq Compute Context`, il contesto che si sta usando è quello locale.
  
## Passaggio successivo  
[Visualizzare i dati di SQL Server mediante R &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/visualize-sql-server-data-using-r-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Definire e usare i contesti di calcolo &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
  
  
