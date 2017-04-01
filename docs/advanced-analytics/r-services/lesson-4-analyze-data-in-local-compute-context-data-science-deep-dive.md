---
title: "Lezione 4: Analizzare i dati in un contesto di calcolo locale (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
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
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Lezione 4: Analizzare i dati in un contesto di calcolo locale (Procedura approfondita per l&#39;analisi scientifica dei dati)
Sebbene in genere risulti più veloce eseguire un codice R complesso usando il contesto del server, è talvolta più pratico estrarre i dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e analizzarli in una workstation privata.  
  
In questa sezione verrà illustrato come passare ad un contesto di calcolo locale, e spostare dati tra contesti per ottimizzare le prestazioni.  
  
## Creare un riepilogo locale  
  
1.  Modificare il contesto di calcolo per eseguire il lavoro localmente .  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
2.  Durante l'estrazione dei dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è spesso possibile ottenere prestazioni migliori, aumentando il numero di righe estratte per ogni lettura.  A tale scopo, aumentare il valore del parametro *rowsPerRead* nell'origine dati.  
  
    ```R  
    sqlServerDS1 <- RxSqlServerData(  
       connectionString = sqlConnString,        
       table = sqlFraudTable,   
       colInfo = ccColInfo,   
       rowsPerRead = 10000)  
    ```  
  
    In precedenza, il valore di *rowsPerRead* era impostato su 5000.  
  
3.  A questo punto chiamare *rxSummary* nella nuova origine dati.  
  
    ```R  
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)    
    ```  
  
    I risultati effettivi devono corrispondere a quelli ottenuti con l'esecuzione di *rxSummary* nel contesto del computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  L'operazione potrebbe tuttavia essere più veloce o più lenta a seconda del tipo di connessione al database. Per essere analizzati, i dati vengono infatti trasferiti nel computer locale.  
  

## Passaggio successivo  
[Spostare i dati tra SQL Server e file XDF &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
## Passaggio precedente  
[Eseguire un'analisi in blocchi tramite rxDataStep &#40;Procedura approfondita per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
  
  
