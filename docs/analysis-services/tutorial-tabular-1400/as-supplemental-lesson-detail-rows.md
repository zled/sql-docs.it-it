---
title: 'Lezione supplementare di Analysis Services tutorial: righe di dettaglio | Documenti Microsoft'
description: Viene descritto come creare un'espressione di righe di dettaglio nelle esercitazioni su Analysis Services.
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 7efcdc724792656a917b95892ed699bc57590ce7
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="supplemental-lesson---detail-rows"></a>Lezione supplementare - righe di dettaglio

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione supplementare, utilizzare l'Editor DAX per definire un'espressione di righe di dettaglio personalizzata. Un'espressione di righe di dettaglio è una proprietà su una misura, offre agli utenti finali maggiori informazioni sui risultati di una misura aggregati. 
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo lezione supplementare fa parte di un'esercitazione di modellazione tabulare. Prima di eseguire le attività in questa lezione supplementare, è necessario avere completato tutte le lezioni precedenti o dispone di un progetto di modello di esempio Adventure Works Internet Sales completato.  
  
## <a name="whats-the-issue"></a>Che cos'è il problema?

Esaminiamo i dettagli della misura InternetTotalSales, prima di aggiungere un'espressione di righe di dettaglio.

1.  In SSDT, fare clic su di **modello** menu > **analizza in Excel** aprire Excel e creare una tabella pivot vuota.
  
2.  In **PivotTable Fields**, aggiungere il **InternetTotalSales** misure dalla tabella FactInternetSales **valori**, **CalendarYear** dalla tabella DimDate **colonne**, e **EnglishCountryRegionName** a **righe**. La tabella pivot offre ora un risultati aggregati dall'oggetto measure InternetTotalSales per aree e anno. 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. Nella tabella pivot, fare doppio clic su un valore aggregato per un anno e un nome di area. Qui è fatto doppio clic con il valore per l'Australia e l'anno 2014. Consente di aprire un nuovo foglio di contenente dati, ma i dati non utili.

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Ciò che si desidera vedere di seguito è una tabella contenente colonne e righe di dati che contribuiscono al risultato della misura InternetTotalSales aggregato. A tale scopo, è possibile aggiungere un'espressione di righe di dettaglio come proprietà della misura.

## <a name="add-a-detail-rows-expression"></a>Aggiungere un'espressione di righe di dettaglio

#### <a name="to-create-a-detail-rows-expression"></a>Per creare un'espressione di righe di dettaglio 
  
1. Nella griglia delle misure della tabella FactInternetSales, fare clic su di **InternetTotalSales** misura. 

2. In **proprietà** > **espressione righe di dettaglio**, fare clic sul pulsante editor per aprire l'Editor DAX.

    ![as-lesson-detail-rows-ellipse](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. Nell'Editor DAX, immettere l'espressione seguente:

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    Questa espressione consente di specificare i nomi, le colonne e misure dalla tabella FactInternetSales e tabelle correlate vengono restituiti quando un utente fa doppio clic su un risultato aggregato in una tabella pivot o un report.

4. In Excel, eliminare il foglio creato nel passaggio 3, quindi fare doppio clic su un valore aggregato. Questa volta, con una proprietà di espressione di righe di dettaglio definita per la misura, un nuovo foglio apre che contiene dati molto più utili.

    ![as-lesson-detail-rows-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Ridistribuire il modello.

  
## <a name="see-also"></a>Vedere anche  

[Funzione SELECTCOLUMNS (DAX)](https://msdn.microsoft.com/library/mt761759.aspx)  
[Lezione supplementare - Sicurezza dinamica](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Lezione supplementare - Gerarchie incomplete](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
