---
title: "Lezione dell'esercitazione di Analysis Services 6: creare misure | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61ead234a52f258f2c535f85c0992523b5b4e146
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044505"
---
# <a name="create-measures"></a>Creare misure

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, creare misure da includere nel modello. Come per le colonne calcolate che è stato creato, una misura è un calcolo creato utilizzando una formula DAX. Tuttavia, a differenza delle colonne calcolate, le misure vengono valutate in base a un utente ha selezionato *filtro*. Ad esempio, una particolare colonna o sezionamento aggiunto al campo etichette di riga in una tabella pivot. Viene quindi calcolato un valore per ogni cella nel filtro tramite la misura applicata. Le misure sono calcoli potenti e flessibili che si desidera includere in quasi tutti i modelli tabulari per eseguire calcoli dinamici sui dati numerici. Per ulteriori informazioni, vedere [misure](../tabular-models/measures-ssas-tabular.md).
  
Per creare misure, utilizzare il *griglia delle misure*. Per impostazione predefinita, ogni tabella dispone di una griglia delle misure vuota; Tuttavia, in genere non creare misure per ogni tabella. La griglia delle misure viene visualizzata sotto una tabella di Progettazione modelli se si trova in Vista dati. Per visualizzare o nascondere la griglia delle misure per una tabella, fare clic sul menu **Tabella** , quindi su **Mostra griglia delle misure**.  
  
È possibile creare una misura facendo clic su una cella vuota nella griglia delle misure, e quindi digitando una formula DAX nella barra della formula. Quando premere INVIO per completare la formula, la misura quindi viene visualizzato nella cella. È inoltre possibile creare misure utilizzando una funzione di aggregazione standard facendo clic su una colonna, e quindi fare clic sul pulsante Somma automatica (**∑**) sulla barra degli strumenti. Le misure create utilizzando la funzionalità Somma automatica vengono visualizzate nella cella della griglia delle misure direttamente sotto la colonna, ma possono essere spostate.  
  
In questa lezione, creare misure sia immettendo una formula DAX nella barra della formula e, utilizzando la funzionalità Somma automatica.  
  
Tempo stimato per il completamento della lezione: **30 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 5: creare colonne calcolate](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Creare misure  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Per creare una misura DaysCurrentQuarterToDate della tabella DimDate  
  
1.  In Progettazione modelli fare clic su di **DimDate** tabella.  
  
2.  Nella griglia delle misure fare clic sulla cella vuota in alto a sinistra.  
  
3.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Si noti che la cella superiore sinistra contiene ora un nome di misura, **DaysCurrentQuarterToDate**, seguito dal risultato, **92**. Il risultato non è pertinente a questo punto perché non è stato applicato alcun filtro utente.
    
      ![as-lesson6-newmeasure](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    A differenza delle colonne calcolate, con le formule delle misure è possibile digitare il nome della misura, seguito da due punti, seguiti dall'espressione della formula.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Per creare una misura DaysInCurrentQuarter della tabella DimDate  
  
1.  Con il **DimDate** ancora attiva in Progettazione modelli, nella griglia delle misure, fare clic sulla cella vuota sotto la misura creata.  
  
2.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Quando si crea un rapporto di confronto tra un periodo incompleto e il periodo precedente. La formula deve calcolare la proporzione del periodo trascorsa e confrontarla con la stessa proporzione del periodo precedente. In questo caso, [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] fornisce la proporzione del periodo corrente è scaduto.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Per creare una misura InternetDistinctCountSalesOrder nella tabella FactInternetSales  
  
1.  Fare clic su di **FactInternetSales** tabella.   
  
2.  Fare clic su di **SalesOrderNumber** intestazione di colonna.  
  
3.  Nella barra degli strumenti fare clic sulla freccia giù accanto al pulsante Somma automatica (**∑**), quindi selezionare **DistinctCount**.  
  
    La funzionalità Somma automatica consente di creare automaticamente una misura per la colonna selezionata utilizzando la formula di aggregazione standard DistinctCount.  
    
       ![as-lesson6-newmeasure2](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  Nella griglia delle misure, fare clic su nuova misura e quindi la **proprietà** finestra, in **nome misura**, rinominare la misura in **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Per creare misure aggiuntive nella tabella FactInternetSales  
  
1.  Utilizzando la funzionalità Somma automatica, è possibile creare le misure seguenti e assegnare loro un nome:  

    |Colonna|Nome misura|Somma automatica (∑)|Formula|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|SUM|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|SUM|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|SUM|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|SUM|=SUM([SalesAmount])|  
    |Margin|InternetTotalMargin|SUM|=SUM([Margin])|  
    |TaxAmt|InternetTotalTaxAmt|SUM|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|SUM|=SUM([Freight])|  
  
2.  Fare clic su una cella vuota nella griglia delle misure e utilizzando la barra della formula, creare, le misure personalizzate seguenti nell'ordine:  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Le misure create per la tabella FactInternetSales è utilizzabile per analizzare dati finanziari critici, ad esempio vendite, costi e margine di profitto per elementi definiti dal filtro selezionato di utenti.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 7: Creare indicatori di prestazioni chiave](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  

  
