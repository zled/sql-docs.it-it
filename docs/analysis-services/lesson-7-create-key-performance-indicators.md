---
title: 'Lezione 8: Creare indicatori di prestazioni chiave | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1c9a041f0effd496d4d339d5389525cb3b530020
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-7-create-key-performance-indicators"></a>Lezione 7: Creare indicatori di prestazioni chiave
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verranno creati indicatori di prestazioni chiave (KPI). Gli indicatori di prestazioni chiave vengono usati per misurare le prestazioni di un valore, definito mediante una misura di *base* , rispetto a un valore *target* , definito anch'esso da una misura o da un valore assoluto. Nelle applicazioni client di creazione di report, gli indicatori KPI possono fornire ai professionisti aziendali un metodo semplice e veloce per comprendere l'andamento aziendale in generale o per identificare le tendenze. Per ulteriori informazioni, vedere [gli indicatori KPI](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 6: creare misure](../analysis-services/lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Creare indicatori di prestazioni chiave  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Per creare un KPI InternetCurrentQuarterSalesPerformance  
  
1.  In Progettazione modelli fare clic su di **FactInternetSales** tabella (scheda).  
  
2.  Nella griglia delle misure fare clic su una cella vuota.  
  
3.  Sulla barra della formula sopra la tabella digitare la formula seguente: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Tale misura definirà fungerà da misura di base per l'indicatore KPI.  
  
4.  Fare doppio clic su **InternetCurrentQuarterSalesPerformance** > **crea KPI**.   
  
5.  Nella finestra di dialogo indicatore di prestazioni chiave (KPI) in **destinazione** selezionare **valore assoluto**, quindi digitare **1.1**.  
  
7.  Nel campo relativo al dispositivo di scorrimento sinistro (in basso) digitare **1**, quindi nel campo relativo al dispositivo di scorrimento destro (in alto), digitare **1.07**.  
  
8.  In **Seleziona stile icona**selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde).
  
    ![come-tabulare-lesson7-indicatore kpi](../analysis-services/media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > Si noti l'espandibile **descrizioni** etichetta sotto gli stili di icona disponibili. Consente di immettere le descrizioni per i diversi elementi KPI per semplificarne l'identificazione nelle applicazioni client.  
  
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
  
5.  In **Definisci soglie stato**far scorrere il dispositivo di scorrimento sinistro (in basso) fino a quando non viene visualizzato **0.8**, quindi far scorrere il dispositivo di scorrimento destro (in alto) fino a quando non viene visualizzato **1.03**.  
  
6.  In **Seleziona stile icona**selezionare un tipo di icona a rombo (rosso), triangolo (giallo) o cerchio (verde), quindi fare clic su **OK**.  
  
## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 8: creare prospettive](../analysis-services/lesson-8-create-perspectives.md).
  
  
