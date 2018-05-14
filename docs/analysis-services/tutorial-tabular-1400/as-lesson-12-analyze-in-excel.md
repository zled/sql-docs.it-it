---
title: "Lezione dell'esercitazione di Analysis Services 12: analizza in Excel | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d215045f87ed780a4adc97f9ae4fed9ac7e6991a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="analyze-in-excel"></a>Analizza in Excel

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, si usa analizza nella funzionalità di Excel per aprire Microsoft Excel, creare automaticamente una connessione all'area di lavoro modello e aggiungere automaticamente una tabella pivot al foglio di lavoro. La funzionalità Analizza in Excel offre un metodo rapido e semplice per testare l'efficacia della progettazione del modello prima di distribuirlo. In questa lezione non si esegue alcuna analisi dei dati. Lo scopo di questa lezione è acquisire familiarità con gli strumenti che è possibile utilizzare per testare la progettazione del modello.   
  
Per completare questa lezione, è necessario che Excel sia installato nello stesso computer di Visual Studio.
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 11: creare ruoli](../tutorial-tabular-1400/as-lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Sfogliare il modello utilizzando la prospettiva predefinita e la prospettiva Internet Sales  

In queste prime attività, esplorare il modello utilizzando la prospettiva predefinita, che include tutti gli oggetti modello, e la prospettiva Internet Sales è in precedenza. La prospettiva Internet Sales esclude l'oggetto Customer table.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Per sfogliare il modello tramite la prospettiva predefinita  
  
1.  Fare clic su di **modello** menu > **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** fare clic su **OK**.  
  
    Verrà visualizzata la finestra di Excel con una nuova cartella di lavoro. Viene creata una connessione all'origine dati utilizzando l'account utente corrente e la prospettiva predefinita viene utilizzata per definire campi visualizzabili. Una tabella pivot viene automaticamente aggiunto al foglio di lavoro.  
  
3.  In Excel, nel **elenco campi tabella pivot**, si noti il **DimDate** e **FactInternetSales** vengono visualizzati i gruppi di misure. Il **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, e **FactInternetSales** vengono visualizzati anche le tabelle con le rispettive colonne.  
  
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Per sfogliare il modello tramite la prospettiva Internet Sales  
  
1.  Fare clic su di **modello** menu e quindi fare clic su **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** lasciare selezionata l'opzione **Utente di Windows corrente** , quindi nell'elenco a discesa **Prospettiva** selezionare **Internet Sales**e fare clic su **OK**. 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  In Excel, in **PivotTable Fields**, si noti la tabella DimCustomer viene escluso dall'elenco di campi.  
    
    ![campi come lesson12](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="browse-by-using-roles"></a>Sfoglia utilizzando i ruoli  

I ruoli sono una parte importante di qualsiasi modello tabulare. Senza almeno un ruolo a cui gli utenti vengono aggiunti come membri, gli utenti non possono accedere e analizzare i dati utilizzando il modello. La funzionalità Analizza in Excel consente di testare i ruoli che sono stati definiti dall'utente.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Per esplorare utilizzando il ruolo utente Sales Manager  
  
1.  In SSDT, fare clic su di **modello** menu e quindi fare clic su **analizza in Excel**.  
  
2.  In **specificare il nome utente o ruolo da utilizzare per connettersi al modello**selezionare **ruolo**, quindi nella casella di riepilogo a discesa, selezionare **Sales Manager**, quindi fare clic su **OK**.  
  
    Verrà visualizzata la finestra di Excel con una nuova cartella di lavoro. Viene creata automaticamente una tabella pivot. L'elenco campi tabella Pivot include tutti i campi di dati disponibili nel nuovo modello.  
      
3.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

Passare alla lezione successiva: [lezione 13: distribuire](../tutorial-tabular-1400/as-lesson-13-deploy.md).

  
  
  
