---
title: Caricare i dati in memoria usando rxImport | Documenti Microsoft
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 47a42e9a-05a0-4a50-871d-de73253cf070
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85d6174686be113ff9a23985b1d5b5763783c986
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="load-data-into-memory-using-rximport"></a>Caricare i dati in memoria mediante rxImport

La funzione **rxImport** può essere usata per spostare i dati da un'origine dati in un frame di dati in una memoria della sessione R o in un file XDF sul disco. Se non si specifica un file come destinazione, i dati vengono inseriti in memoria come frame di dati.

In questo passaggio, si apprenderà come ottenere dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e quindi utilizzare la funzione rxImport per inserire i dati di interesse in un file locale. In questo modo è possibile analizzare i dati nel contesto di calcolo locale più volte senza dover ripetere la query del database.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Estrarre un subset di dati da SQL Server alla memoria locale

Si è deciso di esaminare in maggior dettaglio solo i clienti ad alto rischio. La tabella di origine in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è grande, pertanto si estrarranno solo le informazioni relative ai clienti ad alto rischio, quindi si caricheranno tali informazioni in un frame di dati nella memoria della workstation locale.

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

3. Usare la funzione **rxImport** per caricare effettivamente i dati in un frame di dati nella sessione R locale.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Se l'operazione è stata eseguita correttamente, il messaggio di stato visualizzato sarà: Rows Read: 35, Total Rows Processed: 35, Total Chunk Time: 0.036 seconds

4. Ora che il frame di dati in memoria contiene le osservazioni con i punteggi di rischio più alti, è possibile usare varie funzioni R per gestire il frame di dati. È possibile ad esempio classificare i clienti in base al punteggio di rischio e stampare quelli con il rischio più elevato.

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

È possibile utilizzare rxImport non solo per spostare i dati, ma per trasformare i dati nel processo di lettura. È ad esempio possibile specificare il numero di caratteri per le colonne a larghezza fissa, includere una descrizione delle variabili, impostare i livelli per le colonne di fattori, nonché creare nuovi livelli da usare dopo l'importazione.

La funzione rxImport assegna i nomi delle variabili alle colonne durante il processo di importazione, ma è possibile specificare i nuovi nomi di variabile utilizzando il *colInfo* parametro ed è possibile modificare i tipi di dati tramite il *colClasses* parametro.

Specificando operazioni aggiuntive nel parametro *transforms* è anche possibile eseguire operazioni di elaborazione elementare su ogni blocco di dati che viene letto.

## <a name="next-step"></a>Passaggio successivo

[Creare una nuova tabella di SQL Server utilizzando rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>Passaggio precedente

[Trasformare i dati usando R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="see-also"></a>Vedere anche

[Esercitazioni di Machine Learning](../../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

