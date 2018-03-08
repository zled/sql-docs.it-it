---
title: Connessione all'editor di query | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
caps.latest.revision: "26"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 739a1ae0f65b4a2ca0f6efb803c851773e0bd730
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-2-1---connecting-with-query-editor"></a>Lezione 2-1 - Connessione all'editor di query
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente di scrivere o modificare codice quando non si è connessi al server. Ciò risulta utile quando il server non è disponibile o quando si desidera risparmiare risorse di rete o di server limitate. È inoltre possibile connettere l'editor di query a una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza la necessità di avviare una nuova finestra dell'editor di query o di immettere nuovamente il codice.  
  
## <a name="coding-offline"></a>Codifica offline  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a>Per scrivere codice offline e quindi connettersi a server diversi  
  
1.  Sulla barra degli strumenti di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] fare clic su **Query del motore di database** per aprire l'editor di query.  
  
2.  Nella finestra di dialogo **Connetti al motore di database** fare clic su **Annulla**. Verrà avviato l'editor di query e la barra del titolo indicherà che l'editor non è connesso a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Nel riquadro del codice digitare la seguente istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
    A questo punto è possibile stabilire la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] facendo clic su **Connetti**, **Esegui**, **Analizza**o **Visualizza piano di esecuzione stimato**disponibili nel menu **Query** , sulla barra degli strumenti dell'editor di query o nel menu di scelta rapida facendo clic con il pulsante destro del mouse nella finestra dell'editor di query. Per questa procedura verrà utilizzata la barra degli strumenti.  
  
4.  Sulla barra degli strumenti fare clic sul pulsante **Esegui** per visualizzare la finestra di dialogo **Connetti al motore di database** .  
  
5.  Nella casella di testo **Nome server** digitare il nome del server e fare clic su **Opzioni**.  
  
6.  Nella scheda **Proprietà connessione** , nell'elenco **Connetti al database** selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e fare clic su **Connetti**.  
  
7.  Per visualizzare un'altra finestra dell'editor di query con la stessa connessione, fare clic su **Nuova query**sulla barra degli strumenti.  
  
8.  Per cambiare le connessioni, fare clic con il pulsante destro del mouse nella finestra dell'editor di query, scegliere **Connessione**e quindi **Cambia connessione**.  
  
9. Nella finestra di dialogo **Connetti a SQL Server** selezionare un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se disponibile e quindi fare clic su **Connetti**.  
  
Questa nuova caratteristica dell'editor di query consente di eseguire facilmente lo stesso codice su diversi server. Ciò può risultare utile per le azioni di manutenzione che coinvolgono server simili.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Aggiunta dei rientri](../../tools/sql-server-management-studio/lesson-2-2-adding-indentation.md)  
  
  
  
