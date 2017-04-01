---
title: "Aggiunta dei rientri | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Aggiunta dei rientri
L'editor di query consente di impostare un rientro per sezioni estese di codice con un singolo passaggio e di modificare l'ampiezza del rientro.  
  
## Aggiunta di un rientro al codice  
  
#### Per aggiungere un rientro a più righe di codice  
  
1.  Sulla barra degli strumenti fare clic su **Nuova query**.  
  
2.  Creare una seconda query per selezionare le colonne **BusinessEntityID**, FirstName, **MiddleName** e **LastName** dalla tabella **Person** dello schema **Person**. Posizionare ogni colonna su una riga separata in modo che il codice abbia l'aspetto seguente:  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  Selezionare tutto il testo compreso tra `BusinessEntityID` e `LastName`.  
  
4.  Sulla barra degli strumenti **Editor SQL** fare clic su **Aumenta rientro** per aggiungere un rientro a tutte le righe contemporaneamente.  
  
#### Per modificare il rientro predefinito  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Editor di testo**, espandere **Tutti i linguaggi** e fare clic su **Tabulazioni** per impostare i valori del rientro nel modo appropriato. Si noti che è possibile modificare le dimensioni del rientro e delle tabulazioni e specificare se le tabulazioni vengono convertite in spazi.  
  
    ![Aspetto della finestra di dialogo Schede](../../tools/sql-server-management-studio/media/tabsdialog.gif "Aspetto della finestra di dialogo Schede")  
  
3.  Scegliere **OK**.  
  
## Attività successiva della lezione  
[Ingrandimento dell'editor di query](../../tools/sql-server-management-studio/maximizing-query-editor.md)  
  
  
  
