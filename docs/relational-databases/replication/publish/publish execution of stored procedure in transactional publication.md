---
title: "Pubblicazione dell&#39;esecuzione di una stored procedure in una pubblicazione transazionale (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione [replica di SQL Server], esecuzione di stored procedure"
  - "stored procedure [replica di SQL Server], pubblicazione"
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Pubblicazione dell&#39;esecuzione di una stored procedure in una pubblicazione transazionale (SQL Server Management Studio)
  Specificare che l'esecuzione di una stored procedure, anziché solo la definizione, deve essere pubblicata nel **Proprietà articolo - \< articolo>** la finestra di dialogo. Questa finestra di dialogo è disponibile nella creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 La definizione della procedura, ovvero l'istruzione CREATE PROCEDURE, viene replicata nel Sottoscrittore durante l'inizializzazione della sottoscrizione. Quando la procedura viene eseguita nel server di pubblicazione, la replica esegue la procedura corrispondente nel Sottoscrittore.  
  
### Per pubblicare l'esecuzione di una stored procedure  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** finestra di dialogo, selezionare una stored procedure.  
  
2.  Fare clic su **Proprietà articolo**, quindi fare clic su **impostare le proprietà di Stored Procedure evidenziato**.  
  
3.  Nel **Proprietà articolo - \< articolo>** finestra di dialogo specificare uno dei seguenti valori per il **replicare** opzione:  
  
    -   **Esecuzione della stored procedure**  
  
    -   **Esecuzione in una transazione serializzata della stored procedure**  
  
         Questa è l'opzione consigliata in quanto replica l'esecuzione della procedura solo se essa viene eseguita all'interno del contesto di una transazione serializzabile. Se viene eseguita in un contesto diverso, le modifiche ai dati delle tabelle pubblicate vengono replicate come una serie di istruzioni DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
## Vedere anche  
 [Pubblicazione dell'esecuzione delle stored procedure nella replica transazionale](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  