---
title: Aggiungere rientri | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 55241a0b99024f557718654869d0ab728089e569
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-2-2---adding-indentation"></a>Lezione 2-2 - Aggiungere rientri
L'editor di query consente di impostare un rientro per sezioni estese di codice con un singolo passaggio e di modificare l'ampiezza del rientro.  
  
## <a name="indenting-code"></a>Aggiunta di un rientro al codice  
  
#### <a name="to-indent-multiple-lines-of-code"></a>Per aggiungere un rientro a più righe di codice  
  
1.  Sulla barra degli strumenti fare clic su **Nuova query**.  
  
2.  Creare una seconda query per selezionare le colonne **BusinessEntityID**, FirstName, **MiddleName**e **LastName** dalla tabella **Person** dello schema **Person** . Posizionare ogni colonna su una riga separata in modo che il codice abbia l'aspetto seguente:  
  
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
  
#### <a name="to-change-the-default-indentation"></a>Per modificare il rientro predefinito  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Editor di testo**, espandere **Tutti i linguaggi**e fare clic su **Tabulazioni** per impostare i valori del rientro nel modo appropriato. Si noti che è possibile modificare le dimensioni del rientro e delle tabulazioni e specificare se le tabulazioni vengono convertite in spazi.  
  
    ![Aspetto della finestra di dialogo Schede](./media/lesson-2-2-adding-indentation/tabsdialog.gif "Aspetto della finestra di dialogo Schede")  
  
3.  Scegliere **OK**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Ingrandimento dell'editor di query](../../tools/sql-server-management-studio/lesson-2-3-maximizing-query-editor.md)  
  
  
  

