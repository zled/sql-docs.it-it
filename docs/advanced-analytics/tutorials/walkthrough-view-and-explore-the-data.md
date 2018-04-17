---
title: Visualizzare ed esplorare i dati di utilizzo di SQL (procedura dettagliata) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b933337c1234f09f0a8963c1979a86a9ab61db53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="view-and-explore-the-data-using-sql-walkthrough"></a>Visualizzare ed esplorare i dati di utilizzo di SQL (procedura dettagliata)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'esplorazione dei dati è una parte importante della modellazione dei dati e richiede la revisione riepiloghi degli oggetti dati da usare nell'analisi, nonché la visualizzazione dei dati. In questa lezione, esplorare gli oggetti dati e generare grafici, utilizzando sia [!INCLUDE[tsql](../../includes/tsql-md.md)] e delle funzioni R incluse nella [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Quindi è generare grafici per visualizzare i dati, utilizzando nuove funzioni fornite da pacchetti installati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

> [!TIP]
> Si ha già dimestichezza con R?
>   
> Ora che tutti i dati sono stati scaricati ed è stato preparato l'ambiente, l’utente può eseguire lo script R completo in RStudio o in qualsiasi altro ambiente ed esplorare le funzionalità per conto proprio. È sufficiente aprire il file RSQL_Walkthrough.R ed evidenziare ed eseguire singole righe o eseguire l'intero script come demo.
>   
> Per maggiori dettagli sulle funzioni di RevoScaleR e suggerimenti per l'uso dei dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in R, continuare con l'esercitazione, che usa esattamente lo stesso script.

## <a name="verify-downloaded-data-using-sql-server"></a>Verificare i dati scaricati utilizzando SQL Server

Per prima cosa, è opportuno verificare che i dati siano stati caricati correttamente.

1. Connettere il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza utilizzando lo strumento di gestione di database preferito, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Esplora Server in Visual Studio o Visual Studio Code.

2. Selezionare il database creato, quindi espandere per visualizzare il nuovo database, tabelle e funzioni.
  
    ![rsql_e2e_ssms_newobjects](media/rsql-e2e-ssms-newobjects.PNG)
  
3.  Per verificare che i dati caricati correttamente, la tabella e scegliere **seleziona le prime 1000 righe**. L'opzione di menu consente di eseguire questa query:

    ```SQL
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]
    ```
    Se nella tabella non vengono visualizzati dati, vedere la sezione [Risoluzione dei problemi](walkthrough-prepare-the-data.md) nell'argomento precedente.

4. Questa tabella di dati è stata ottimizzata per i calcoli basati su set, aggiungendo un [indice columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md). Eseguire questa istruzione per generare un breve riepilogo per la tabella.

    ```SQL
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
    Nella lezione successiva verranno generati alcuni riepiloghi più complessi usando R.

## <a name="next-lesson"></a>Lezione successiva

[Riepilogare i dati con R](walkthrough-view-and-summarize-data-using-r.md)

## <a name="previous-lesson"></a>Lezione precedente

[Preparare i dati di utilizzo di PowerShell](walkthrough-prepare-the-data.md)
