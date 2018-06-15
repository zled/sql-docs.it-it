---
title: Pubblicare l'esecuzione delle stored procedure nella replica transazionale | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b10fedd35293233611cac80d68b08a66c0c796c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32960436"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Pubblicare l'esecuzione delle stored procedure nella replica transazionale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Specificare che nella finestra di dialogo **Proprietà articolo - \<Articolo>** deve essere pubblicata l'esecuzione di una stored procedure, anziché la sola definizione. Questa finestra di dialogo è disponibile nella Creazione guidata nuova pubblicazione e nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per altre informazioni sull'uso della creazione guidata e l'accesso alla finestra di dialogo, vedere [Creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [Visualizzare e modificare le proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 La definizione della procedura, ovvero l'istruzione CREATE PROCEDURE, viene replicata nel Sottoscrittore durante l'inizializzazione della sottoscrizione. Quando la procedura viene eseguita nel server di pubblicazione, la replica esegue la procedura corrispondente nel Sottoscrittore.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Per pubblicare l'esecuzione di una stored procedure  
  
1.  Nella pagina **Articoli** della Creazione guidata nuova pubblicazione o nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare una stored procedure.  
  
2.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di stored procedure evidenziato**.  
  
3.  Nella finestra di dialogo **Proprietà articolo - \<Articolo>** specificare uno dei valori seguenti per l'opzione **Replica**:  
  
    -   **Esecuzione della stored procedure**  
  
    -   **Esecuzione in una transazione serializzata della stored procedure**  
  
         Questa è l'opzione consigliata in quanto replica l'esecuzione della procedura solo se essa viene eseguita all'interno del contesto di una transazione serializzabile. Se viene eseguita in un contesto diverso, le modifiche ai dati delle tabelle pubblicate vengono replicate come una serie di istruzioni DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è visualizzata la finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione dell'esecuzione delle stored procedure nella replica transazionale](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
