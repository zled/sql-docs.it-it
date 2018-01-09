---
title: 'Lezione 13: Analizza in Excel | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d202c423a513949b425ac016ebfbcdbe6fe4b321
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-12-analyze-in-excel"></a>Lezione 12: Analizza in Excel
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione si utilizzerà l'analizza nella funzionalità di Excel in SSDT per aprire Microsoft Excel, creare automaticamente una connessione all'origine dati nell'area di lavoro modello e aggiungere automaticamente una tabella pivot al foglio di lavoro. La funzionalità Analizza in Excel offre un metodo rapido e semplice per testare l'efficacia della progettazione del modello prima di distribuirlo. Non si eseguirà alcuna analisi dei dati in questa lezione. Lo scopo di questa lezione è acquisire familiarità con gli strumenti che è possibile utilizzare per testare la progettazione del modello. A differenza dell'utilizzo di analisi nella funzionalità di Excel, destinata agli autori di modelli, gli utenti finali utilizzeranno applicazioni di reporting, come Excel o Power BI per connettersi e sfogliare i dati del modello distribuito client.  
  
Per completare questa lezione, è necessario che Excel sia installato nello stesso computer come SSDT. Per i dettagli, vedere [Analizza in Excel](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisites  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 11: creare ruoli](../analysis-services/lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Sfogliare il modello utilizzando la prospettiva predefinita e la prospettiva Internet Sales  
In queste prime attività, si sfoglierà il modello utilizzando la prospettiva predefinita, che include tutti gli oggetti modello, e la prospettiva Internet Sales è in precedenza. La prospettiva Internet Sales esclude l'oggetto Customer table.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Per sfogliare il modello tramite la prospettiva predefinita  
  
1.  Fare clic su di **modello** menu > **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** fare clic su **OK**.  
  
    Verrà aperto Excel con una nuova cartella di lavoro. Viene creata una connessione all'origine dati utilizzando l'account utente corrente e la prospettiva predefinita viene utilizzata per definire campi visualizzabili. Una tabella pivot viene automaticamente aggiunto al foglio di lavoro.  
  
3.  In Excel, nel **elenco campi tabella pivot**, si noti il **DimDate** e **FactInternetSales** vengono visualizzati i gruppi di misure, nonché il **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**,  **DimProductSubcategory**, e **FactInternetSales** le tabelle con le rispettive colonne vengono visualizzate.  
  
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Per sfogliare il modello tramite la prospettiva Internet Sales  
  
1.  Fare clic su di **modello** menu e quindi fare clic su **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** lasciare selezionata l'opzione **Utente di Windows corrente** , quindi nell'elenco a discesa **Prospettiva** selezionare **Internet Sales**e fare clic su **OK**. 
    
    ![come-tabulare-lesson12-prospettiva](../analysis-services/media/as-tabular-lesson12-perspective.png)
    
3.  In Excel, in **PivotTable Fields**, si noti la tabella DimCustomer viene escluso dall'elenco di campi.  
    
    ![come tabulare-lesson12-campi](../analysis-services/media/as-tabular-lesson12-fields.png)
    
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="browse-by-using-roles"></a>Sfoglia utilizzando i ruoli  
I ruoli sono una parte integrante di qualsiasi modello tabulare. Senza almeno un ruolo a cui gli utenti vengono aggiunti come membri, gli utenti non saranno in grado di accedere e analizzare i dati utilizzando il modello. La funzionalità Analizza in Excel consente di testare i ruoli che sono stati definiti dall'utente.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Per esplorare utilizzando il ruolo utente Sales Manager  
  
1.  In SSDT, fare clic su di **modello** menu e quindi fare clic su **analizza in Excel**.  
  
2.  Nel **analizza in Excel** della finestra di dialogo **specificare il nome utente o ruolo da utilizzare per connettersi al modello**selezionare **ruolo**, quindi nella casella di riepilogo a discesa, selezionare **Sales Manager**, quindi fare clic su **OK**.  
  
    Verrà aperto Excel con una nuova cartella di lavoro. Viene creata automaticamente una tabella pivot. L'elenco di campi tabella pivot include tutti i campi dati disponibili nel nuovo modello.  
      
3.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 13: distribuire](../analysis-services/lesson-13-deploy.md).

  
  
  
