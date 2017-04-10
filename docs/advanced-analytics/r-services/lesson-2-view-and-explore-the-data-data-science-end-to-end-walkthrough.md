---
title: "Lezione 2: Visualizzare ed esplorare i dati (procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
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
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: 32
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 26
---
# Lezione 2: Visualizzare ed esplorare i dati (procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
L'esplorazione dei dati è una parte importante della modellazione dei dati e richiede la revisione riepiloghi degli oggetti dati da usare nell'analisi, nonché la visualizzazione dei dati. In questa lezione si apprenderà ad esplorare gli oggetti dati e a generare i grafici usando sia [!INCLUDE[tsql](../../includes/tsql-md.md)] , sia le funzioni di R incluse in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Verranno quindi generati i grafici per visualizzare i dati, usando le nuove funzioni incluse nei pacchetti installati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
> [!TIP]  
> Si ha già dimestichezza con R?  
>   
> Ora che tutti i dati sono stati scaricati ed è stato preparato l'ambiente, l’utente può eseguire lo script R completo in RStudio o in qualsiasi altro ambiente ed esplorare le funzionalità per conto proprio. È sufficiente aprire il file RSQL_Walkthrough.R ed evidenziare ed eseguire singole righe o eseguire l'intero script come demo.  
>   
> Per maggiori dettagli sulle funzioni di RevoScaleR e suggerimenti per l'uso dei dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in R, continuare con l'esercitazione, che usa esattamente lo stesso script.  
  
## <a name="verify-downloaded-data-using-sql"></a>Verificare i dati scaricati usando SQL  
Per prima cosa, è opportuno verificare che i dati siano stati caricati correttamente.  
  
1.  Collegarsi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    È possibile usare un'ampia gamma di strumenti per connettersi e visualizzare i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]    
    -   Esplora server in Visual Studio  
  
2.  Espandere il database che è stato creato. L'immagine seguente illustra il nuovo database, le tabelle e le funzioni in **Esplora server.**  
  
    ![new database objects created by script](../../advanced-analytics/r-services/media/rsql-e2e-ssms-newobjects.PNG "new database objects created by script")  
  
3.  È anche possibile eseguire query semplici sui dati. Ad esempio, in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]fare clic con il pulsante destro del mouse sulla tabella e selezionare **Seleziona le prime 1000 righe** per generare ed eseguire questa query:  
  
    ```  
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]  
    ```  
    Se nella tabella non vengono visualizzati dati, vedere la sezione [Risoluzione dei problemi](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md) nell'argomento precedente.
      
4.  Per visualizzare i tipi di dati e lo schema dei dati, è possibile usare le viste di gestione del sistema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```  
    SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
    FROM [TaxiSample].INFORMATION_SCHEMA.COLUMNS  
    WHERE TABLE_NAME = N'nyctaxi_sample';  
    ```  
  
    > [!TIP]  
    > Per ottenere informazioni dettagliate su come è stata creata la tabella di dati, è anche possibile esaminare lo script di `create-db-tb-upload-data.sql`.  
  
### <a name="generate-summaries-using-sql"></a>Generare riepiloghi con SQL  
Uno dei punti di forza che rendono [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] perfetto per l'uso in combinazione con R è la possibilità di eseguire molto velocemente i calcoli basati su set.  Il codice che ha creato la tabella per questa procedura dettagliata ha applicato anche un [indice columnstore](../Topic/Columnstore%20Indexes%20Guide.md) per eseguire calcoli ancora più veloci.   
  
```  
SELECT DISTINCT [passenger_count]  
    , ROUND (SUM ([fare_amount]),0) as TotalFares   
    , ROUND (AVG ([fare_amount]),0) as AvgFares  
FROM [dbo].[nyctaxi_sample]  
GROUP BY [passenger_count]   
ORDER BY  AvgFares desc  
```  

Nei passaggi successivi si userà R per generare alcuni riepiloghi e grafici più sofisticati con i dati di SQL Server.  
  
## <a name="next-steps"></a>Passaggi successivi  
[Visualizzare e riepilogare i dati con R &#40;procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/view-and-summarize-data-using-r-data-science-end-to-end-walkthrough.md)  
  
[Creare grafici e tracciati con R &#40;procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
[Lezione 1: Preparare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>Vedere anche  
[Guida agli indici columnstore](../Topic/Columnstore%20Indexes%20Guide.md)  
  
  
  
