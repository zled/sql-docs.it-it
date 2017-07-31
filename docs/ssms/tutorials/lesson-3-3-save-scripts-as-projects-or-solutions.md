---
title: Salvare gli script come progetti o soluzioni | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 3772efa6ab55acd4087cd47f897040f782476636
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-3-3---save-scripts-as-projects-or-solutions"></a>Lezione 3-3 - Salvare gli script come progetti o soluzioni
Gli sviluppatori che hanno familiarità con [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio apprezzeranno molto l'inclusione di Esplora soluzioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Gli script che supportano le operazioni aziendali possono essere raggruppati in progetti script gestibili come una soluzione. Quando gli script sono inseriti in soluzioni e progetti script è possibile aprirli come gruppo o salvarli contemporaneamente in un prodotto per il controllo del codice sorgente, ad esempio Visual SourceSafe. I progetti script contengono le informazioni di connessione per assicurare un'esecuzione corretta degli script e possono includere altri tipi di file, ad esempio un file di testo di supporto.  
  
In questa esercitazione verranno illustrate le procedure per la creazione di un breve script che esegue query sul database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] inserita in una soluzione e progetto script.  
  
## <a name="using-script-projects-and-solutions"></a>Utilizzo di soluzioni e progetti script  
  
#### <a name="to-create-a-script-project-and-solution"></a>Per creare una soluzione e progetto script  
  
1.  Avviare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e connettersi a un server con Esplora oggetti.  
  
2.  Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nella casella di testo **Nome** digitare **StatusCheck**, fare clic su **Script di SQL Server** in **Modelli**, quindi fare clic su **OK** per aprire una nuova soluzione e progetto script.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Connessioni**, quindi scegliere **Nuova connessione**. Verrà visualizzata la finestra di dialogo **Connetti al server** .  
  
5.  Nella casella di riepilogo **Nome server** digitare il nome del server.  
  
6.  Fare clic su **Opzioni**, quindi sulla scheda **Proprietà connessione** .  
  
7.  Nella casella **Connetti al database** sfogliare il server, selezionare il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , quindi fare clic su **Connetti**. Le informazioni di connessione, incluso il database, verranno aggiunte al progetto.  
  
8.  Se non viene visualizzata la finestra Proprietà, fare clic sulla nuova connessione in Esplora soluzioni e quindi premere F4. Verranno visualizzate le proprietà e le informazioni sulla connessione, incluso il **Database iniziale** rappresentato da [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
9. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla connessione, quindi scegliere **Nuova query**. Verrà creata una nuova query denominata **SQLQuery1.sql** , connessa al database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sul server e aggiunta al progetto script.  
  
10. Nell'editor di query digitare la query seguente per determinare il numero di ordini con date di scadenza precedenti alle date di inizio. (È possibile copiare e incollare il codice dalla finestra dell'esercitazione).  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    > Se è necessario maggiore spazio per digitare la query, premere MAIUSC+ALT+INVIO per passare alla modalità a schermo intero.  
  
11. In Esplora soluzioni fare clic con il pulsante destro del mouse su **SQLQuery1**, quindi scegliere **Rinomina**. Digitare **Check Workorders****.sql** come nuovo nome della query e premere INVIO.  
  
12. Per salvare la soluzione e il progetto script, scegliere **Salva tutto** dal menu **File**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Riepilogo: Soluzioni e progetti script](../../tools/sql-server-management-studio/lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
  

