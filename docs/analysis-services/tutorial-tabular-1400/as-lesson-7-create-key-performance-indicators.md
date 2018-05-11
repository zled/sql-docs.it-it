---
title: "Lezione dell'esercitazione di Analysis Services 7: creare indicatori di prestazioni chiave | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 679b333fd20ede86751a928720484d260e132877
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-key-performance-indicators"></a>Creare indicatori di prestazioni chiave

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione è creare indicatori di prestazioni chiave (KPI). Gli indicatori KPI vengono utilizzati per misurare le prestazioni di un valore definito da un *Base* misura, contro un *destinazione* definito anch'esso da una misura o da un valore assoluto. Nelle applicazioni client di creazione di report, gli indicatori KPI possono fornire ai professionisti aziendali un metodo semplice e veloce per comprendere l'andamento aziendale in generale o per identificare le tendenze. Per ulteriori informazioni, vedere [gli indicatori KPI](../tabular-models/kpis-ssas-tabular.md)
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 6: creare misure](../tutorial-tabular-1400/as-lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Creare indicatori di prestazioni chiave  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Per creare un KPI InternetCurrentQuarterSalesPerformance  
  
1.  In Progettazione modelli fare clic su di **FactInternetSales** tabella.  
  
2.  Nella griglia delle misure fare clic su una cella vuota.  
  
3.  Sulla barra della formula sopra la tabella digitare la formula seguente: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=DIVIDE([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Questa misura viene utilizzata come misura di Base per l'indicatore KPI.  
  
4.  Nella griglia delle misure, fare doppio clic su **InternetCurrentQuarterSalesPerformance** > **crea KPI**.   
  
5.  Nella finestra di dialogo indicatore di prestazioni chiave (KPI) in **destinazione** selezionare **valore assoluto**, quindi digitare **1.1**.  
  
7.  Nel campo relativo al dispositivo di scorrimento sinistro (in basso) digitare **1**, quindi nel campo relativo al dispositivo di scorrimento destro (in alto), digitare **1.07**.  
  
8.  In **Seleziona stile icona**selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde).
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > Si noti l'espandibile **descrizioni** etichetta sotto gli stili di icona disponibili. Utilizzare le descrizioni per i diversi elementi KPI per semplificarne l'identificazione nelle applicazioni client.  
  
9. Fare clic su **OK** per completare l'indicatore KPI.  
  
    Nella griglia delle misure, si noti l'icona accanto al **InternetCurrentQuarterSalesPerformance** misura. Questa icona indica che la misura funge da valore di base per un indicatore KPI.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Per creare un KPI InternetCurrentQuarterMarginPerformance  
  
1.  Nella griglia delle misure per il **FactInternetSales** tabella, fare clic su una cella vuota.  
  
2.  Sulla barra della formula sopra la tabella digitare la formula seguente:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Fare doppio clic su **InternetCurrentQuarterMarginPerformance** > **crea KPI**.  
  
4.  Nella finestra di dialogo indicatore di prestazioni chiave (KPI) in **destinazione** selezionare **valore assoluto**, quindi digitare **1.25**.   
  
5.  Nel campo dispositivo di scorrimento sinistro (in basso), scorrere fino a quando non viene visualizzato il campo **0,8**, quindi far scorrere il dispositivo di scorrimento destro (in alto) campo, fino a quando non viene visualizzato il campo **1.03**.  
  
6.  In **Seleziona stile icona**selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde), quindi fare clic su **OK**.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 8: Creare prospettive](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).
  
  
