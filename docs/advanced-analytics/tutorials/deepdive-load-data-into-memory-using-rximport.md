---
title: Caricare i dati in memoria usando rxImport (SQL e R approfondimento) | Documenti Microsoft
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 47a42e9a-05a0-4a50-871d-de73253cf070
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 71848a5bf0af5b1dcbce24dbd33ba760369f1338
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="load-data-into-memory-using-rximport-sql-and-r-deep-dive"></a>Caricare i dati in memoria usando rxImport (SQL e R approfondimento)

Questo articolo fa parte dell'esercitazione approfondimento di analisi scientifica dei dati, su come usare [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

Il [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) funzione può essere utilizzata per spostare i dati da un'origine dati in un frame di dati in memoria della sessione o in un file con estensione XDF nel disco. Se non si specifica un file come destinazione, i dati vengono inseriti in memoria come frame di dati.

In questo passaggio si informazioni su come ottenere dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e quindi usare il **rxImport** funzione per inserire i dati di interesse in un file locale. In questo modo è possibile analizzare i dati nel contesto di calcolo locale più volte senza dover ripetere la query del database.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Estrarre un subset di dati da SQL Server per la memoria locale

Si è deciso che si desidera esaminare solo gli utenti ad alto rischio in modo più dettagliato. La tabella di origine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è grande, in modo che si desidera ottenere le informazioni relative solo i clienti ad alto rischio. Quindi possibile caricare dati in un frame di dati in memoria della workstation locale.

1. Ripristinare il contesto di calcolo impostandolo sulla workstation locale.

    ```R
    rxSetComputeContext("local")
    ```

2. Creare un nuovo oggetto origine dati SQL Server specificando un'istruzione SQL valida nel parametro *sqlQuery* . Con questo esempio si ottiene un subset delle osservazioni con i punteggi di rischio più alti. In tal modo vengono inseriti nella memoria locale solo i dati effettivamente necessari.

    ```R
    sqlServerProbDS \<- RxSqlServerData(
        sqlQuery = paste("SELECT * FROM ccScoreOutput2",
        "WHERE (ccFraudProb > .99)"),
        connectionString = sqlConnString)
    ```

3. Chiamare la funzione [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) per leggere i dati in un frame di dati nella sessione locale di R.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Se l'operazione ha esito positivo, si dovrebbe vedere un messaggio di stato simile alla seguente: "righe lette: 35, elaborati totale di righe: 35, totale tempo di blocco: 0.036 secondi"

4. Ora che le osservazioni ad alto rischio sono in un frame di dati in memoria, è possibile utilizzare varie funzioni R per modificare il frame di dati. Ad esempio, è possibile ordinare i clienti per il punteggio di rischio e stampa di un elenco di clienti che si presentano più alto rischio.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Risultati**

*ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1*

*9.786345    SD   Male  Principal   23456       25            5 75   0.99994382*

*9.433040    FL Female  Principal   20629       24           28 75   0.99992003*

*8.556785    NY Female  Principal   19064       82           53 43   0.99980784*

*8.188668    AZ Female  Principal   19948       29            0 75   0.99972235*

*7.551699    NY Female  Principal   11051       95            0 75   0.99947516*

*7.335080    NV   Male  Principal   21566        4            6  75   0.9993482*

## <a name="more-about-rximport"></a>Altre informazioni su rxImport

La funzione **rxImport** può essere usata non solo per spostare i dati, ma anche per trasformarli durante il processo di lettura. È ad esempio possibile specificare il numero di caratteri per le colonne a larghezza fissa, includere una descrizione delle variabili, impostare i livelli per le colonne di fattori, nonché creare nuovi livelli da usare dopo l'importazione.

Il **rxImport** funzione assegna i nomi delle variabili alle colonne durante il processo di importazione, ma è possibile specificare i nuovi nomi di variabile utilizzando il *colInfo* parametri o tipi di dati di modifica utilizzando il *colClasses* parametro.

Specificando operazioni aggiuntive nel parametro *transforms* è anche possibile eseguire operazioni di elaborazione elementare su ogni blocco di dati che viene letto.

## <a name="next-step"></a>Passaggio successivo

[Creare una nuova tabella di SQL Server mediante rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>Passaggio precedente

[Trasformare i dati con R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

