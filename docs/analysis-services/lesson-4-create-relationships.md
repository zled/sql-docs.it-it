---
title: 'Lezione 5: Creare relazioni | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 096f19dc25973b2d515c6ccfb9961e7b0fe07c21
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-4-create-relationships"></a>Lezione 4: Creare relazioni
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verrà verificare le relazioni create automaticamente durante l'importazione dei dati e aggiungere nuove relazioni tra tabelle diverse. Una relazione è una connessione tra due tabelle che stabilisce in che modo devono essere correlati i dati nelle due tabelle. Ad esempio, la tabella DimProduct e la tabella DimProductSubcategory dispongono di una relazione basata sul fatto che ogni prodotto appartiene a una sottocategoria. Per ulteriori informazioni, vedere [relazioni](../analysis-services/tabular-models/relationships-ssas-tabular.md).
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 3: contrassegna come tabella data](../analysis-services/lesson-3-mark-as-date-table.md). 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Esaminare le relazioni esistenti e aggiungere nuove relazioni  
Durante l'importazione di dati tramite l'importazione guidata tabella, sarà possibile ottenere sette tabelle dal database AdventureWorksDW. In genere, quando si importano dati da un'origine relazionale, le relazioni esistenti vengono importate automaticamente insieme ai dati. Prima di procedere con la creazione del modello, è tuttavia necessario verificare che le relazioni tra tabelle siano state create correttamente. Per questa esercitazione, verranno inoltre aggiunte tre nuove relazioni.  
  
#### <a name="to-review-existing-relationships"></a>Per esaminare le relazioni esistenti  
  
1.  Fare clic su di **modello** menu > **vista modello** > **vista diagramma**.  

    La finestra Progettazione modelli viene ora visualizzata nella vista diagramma, un formato grafico in cui sono visualizzate tutte le tabelle importate, con linee tra di esse. Le linee tra le tabelle indicano le relazioni create automaticamente quando sono stati importati i dati.
    
    ![come-tabulare-lesson4-diagramma](../analysis-services/media/as-tabular-lesson4-diagram.png)
  
    Usare i controlli della mini mappa nell'angolo inferiore destro di Progettazione modelli per regolare la vista in modo da includere il maggior numero di tabelle possibile. È anche possibile fare clic sulle tabelle e trascinarle in posizioni diverse, avvicinandole o disponendole in un ordine particolare. Lo spostamento delle tabelle non influisce sulle relazioni già presenti tra le tabelle. Per visualizzare tutte le colonne di una tabella specifica, fare clic su un bordo della tabella e trascinare per espanderla o renderla più piccola.  
  
2.  Fare clic sulla linea continua tra il **DimCustomer** tabella e **DimGeography** tabella. La linea continua tra queste due tabelle indica che questa relazione è attiva, ovvero viene utilizzata per impostazione predefinita nel calcolo delle formule DAX.  
  
    Si noti il **GeographyKey** colonna il **DimCustomer** tabella e il **GeographyKey** colonna il **DimGeography** tabella appaiono ora entrambe all'interno di una casella. Ciò indica che si tratta delle colonne utilizzate nella relazione. Le proprietà della relazione sono ora visualizzate nella finestra **Proprietà** .  
  
    > [!TIP]  
    > Oltre a utilizzare Progettazione modelli in vista diagramma, è inoltre possibile utilizzare la finestra di dialogo Gestisci relazioni per mostrare le relazioni tra tutte le tabelle in un formato di tabella. Fare doppio clic su **relazioni** in Esplora modelli tabulari e quindi fare clic su **Gestisci relazioni**. La finestra di dialogo Gestisci relazioni sono illustrate le relazioni create automaticamente durante l'importazione dei dati.  
  
3.  Utilizzare Progettazione modelli in vista diagramma o la finestra di dialogo Gestisci relazioni, per verificare le relazioni seguenti siano state create quando ognuna delle tabelle sono state importate dal database AdventureWorksDW:  
  
    |Attiva|Tabella|Tabella di ricerca correlata|  
    |----------|---------|------------------------|  
    |Sì|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |Sì|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |Sì|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |Sì|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |Sì|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    Se una delle relazioni nella tabella precedente sono mancante, verificare che il modello include le seguenti tabelle: DimCustomer, DimDate, DimGeography, DimProduct, DimProductCategory, DimProductSubcategory e FactInternetSales. Se tabelle della stessa connessione all'origine dati vengono importate in momenti distinti, non verranno create relazioni tra tali tabelle, che dovranno essere create manualmente.  

### <a name="take-a-closer-look"></a>Esaminare attentamente
Nella vista diagramma, si noterà una freccia, un asterisco e un numero di righe che mostrano la relazione tra tabelle.

![come-tabulare-lesson4-line](../analysis-services/media/as-tabular-lesson4-line.png)

La freccia indica la direzione del filtro, che l'asterisco viene illustrata questa tabella è il lato "molti" la cardinalità della relazione e il 1 sono illustrati in questa tabella è il uno lato della relazione. Se si desidera modificare una relazione. ad esempio, modificare la direzione del filtro della relazione o cardinalità, fare doppio clic su questa linea della relazione nella vista diagramma per aprire la finestra di dialogo Modifica relazione.

![come tabulare-lesson4-modifica](../analysis-services/media/as-tabular-lesson4-edit.png)

Probabilmente non sarà mai necessario modificare una relazione. Queste funzionalità sono concepite per la modellazione dei dati avanzate e all'esterno dell'ambito di questa esercitazione. Per ulteriori informazioni, vedere [bidirezionale tra i filtri per i modelli tabulari in SQL Server 2016 Analysis Services](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md).

In alcuni casi, potrebbe essere necessario creare relazioni aggiuntive tra tabelle nel modello per supportare una logica di business specifica. Per questa esercitazione, è necessario creare tre relazioni aggiuntive tra la tabella FactInternetSales e la tabella DimDate.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Per aggiungere nuove relazioni tra tabelle  
  
1.  In Progettazione modelli nel **FactInternetSales** tabella, fare clic e tenere premuto il **OrderDate** colonna, quindi trascinare il cursore di **data** colonna il  **DimDate** tabella e infine rilasciare.  

    Verrà visualizzata di una linea a tinta unita che è stata creata una relazione attiva tra il **OrderDate** colonna il **Internet Sales** tabella e **data** colonna il **Data** tabella. 
  
      ![come tabulare-lesson4-nuovo](../analysis-services/media/as-tabular-lesson4-new.png) 
  
    > [!NOTE]  
    > Quando si creano relazioni, viene selezionata automaticamente la cardinalità e filtro la direzione tra la tabella primaria e la tabella di ricerca correlata.  
  
2.  Nel **FactInternetSales** tabella, fare clic e tenere premuto il **DueDate** colonna, quindi trascinare il cursore di **data** colonna il **DimDate** e quindi rilasciare.  
  
    Viene visualizzato di una linea punteggiata che è stata creata una relazione inattiva tra la **DueDate** colonna il **FactInternetSales** tabella e **data** colonna il  **DimDate** tabella. È possibile creare più relazioni tra tabelle, ma può essere attiva una sola relazione per volta.  
  
3.  Infine, creare una relazione di altre. nel **FactInternetSales** tabella, fare clic e tenere premuto il **ShipDate** colonna, quindi trascinare il cursore di **data** colonna il **DimDate** tabella e quindi rilasciarlo.  
    
     ![come-tabulare-lesson4-newinactive](../analysis-services/media/as-tabular-lesson4-newinactive.png)
  
## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 5: creare colonne calcolate](../analysis-services/lesson-5-create-calculated-columns.md).
  
  
  

