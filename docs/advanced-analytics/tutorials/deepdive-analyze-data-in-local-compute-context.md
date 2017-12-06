---
title: Analizzare i dati nel contesto di calcolo locale | Documenti Microsoft
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8e6516b7d203180d5c2a605db1099b1dcbae708
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="analyze-data-in-local-compute-context-data-science-deep-dive"></a>Analizzare i dati nel contesto di calcolo locale (dati scienza approfondimento)

Sebbene sia più veloce per eseguire codice R complesso usando il contesto server, in alcuni casi è semplicemente più conveniente ottenere i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e analizzarlo nella workstation privata.

In questa sezione verrà illustrato come passare ad un contesto di calcolo locale, e spostare dati tra contesti per ottimizzare le prestazioni.

## <a name="create-a-local-summary"></a>Creare un riepilogo locale

1. Modificare il contesto di calcolo per eseguire il lavoro localmente .
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Durante l'estrazione dei dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è spesso possibile ottenere prestazioni migliori, aumentando il numero di righe estratte per ogni lettura.  A tale scopo, aumentare il valore del parametro *rowsPerRead* nell'origine dati.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```
  
    In precedenza, il valore di *rowsPerRead* era impostato su 5000.
  
3. A questo punto chiamare **rxSummary** nella nuova origine dati.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    I risultati effettivi devono essere lo stesso come quando si esegue rxSummary nel contesto del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.  L'operazione potrebbe tuttavia essere più veloce o più lenta a seconda del tipo di connessione al database. Per essere analizzati, i dati vengono infatti trasferiti nel computer locale.


## <a name="next--step"></a>Passaggio successivo

[Spostare dati tra SQL Server e i File con estensione XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>Passaggio precedente

[Eseguire l'analisi di suddivisione in blocchi utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)


