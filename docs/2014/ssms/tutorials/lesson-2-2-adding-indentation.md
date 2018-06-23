---
title: Aggiungere rientri | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 24
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a81ee88e551e45989d32fbd9f71623444a737ef2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166754"
---
# <a name="adding-indentation"></a>Aggiunta dei rientri
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
  
     ![Aspetto della finestra di dialogo Schede](media/tabsdialog.gif "Aspetto della finestra di dialogo Schede")  
  
3.  Fare clic su **OK**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Ingrandimento dell'editor di query](lesson-2-3-maximizing-query-editor.md)  
  
  