---
title: Analizzare i dati nel contesto di calcolo locale (SQL e R approfondimento) | Documenti Microsoft
ms.date: 12/18/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: e521ae9ab359ac210383cfb56ded80da4ed181ff
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="analyze-data-in-local-compute-context-sql-and-r-deep-dive"></a>Analizzare i dati nel contesto di calcolo locale (SQL e R approfondimento)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questa sezione informazioni su come tornare a un contesto di calcolo locale e spostare dati tra i contesti per ottimizzare le prestazioni.

Sebbene i potrebbe essere più veloce per eseguire codice R complesso usando il contesto server, a volte è più conveniente ottenere i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e analizzarli in una workstation locale.

## <a name="create-a-local-summary"></a>Creare un riepilogo locale

1. Modificare il contesto di calcolo per eseguire il lavoro localmente .
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Durante l'estrazione dei dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è spesso possibile ottenere prestazioni migliori, aumentando il numero di righe estratte per ogni lettura.  A tale scopo, aumentare il valore del parametro *rowsPerRead* nell'origine dati. In precedenza, il valore di *rowsPerRead* era impostato su 5000.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Chiamare **rxSummary** nella nuova origine dati.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    I risultati effettivi devono corrispondere a quelli ottenuti con l'esecuzione di **rxSummary** nel contesto del computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  L'operazione potrebbe tuttavia essere più veloce o più lenta a seconda del tipo di connessione al database. Per essere analizzati, i dati vengono infatti trasferiti nel computer locale.

## <a name="next-step"></a>Passaggio successivo

[Spostare i dati tra SQL Server e il File con estensione XDF](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>Passaggio precedente

[Eseguire un'analisi in blocchi tramite rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
