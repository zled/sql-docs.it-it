---
title: 'Analysis Services tutorial la lezione 4: creare relazioni | Documenti Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 564126e1de4a8019778e33718b48462f633ae232
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044645"
---
# <a name="create-relationships"></a>Creare relazioni

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione si verificare le relazioni create automaticamente durante l'importazione dei dati e aggiungono nuove relazioni tra tabelle diverse. Una relazione è una connessione tra due tabelle che stabilisce in che modo devono essere correlati i dati nelle due tabelle. Ad esempio, la tabella DimProduct e la tabella DimProductSubcategory dispongono di una relazione basata sul fatto che ogni prodotto appartiene a una sottocategoria. Per ulteriori informazioni, vedere [relazioni](../tabular-models/relationships-ssas-tabular.md).
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 3: contrassegna come tabella data](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md). 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>Esaminare le relazioni esistenti e aggiungere nuove relazioni  

Quando sono stati importati dati usando recupera dati, sarà possibile ottenere sette tabelle dal database AdventureWorksDW. In genere, quando si importano dati da un'origine relazionale, le relazioni esistenti vengono importate automaticamente insieme ai dati. Affinché i dati per creare automaticamente le relazioni nel modello di dati, deve essere relazioni tra tabelle nell'origine dati.

Prima di procedere alla creazione del modello, è necessario verificare le relazioni tra tabelle siano state create correttamente. Per questa esercitazione, è inoltre possibile aggiungere tre nuove relazioni.  

  
#### <a name="to-review-existing-relationships"></a>Per esaminare le relazioni esistenti  
  
1.  Fare clic su di **modello** menu > **vista modello** > **vista diagramma**.  

    La progettazione del modello viene visualizzato nella vista diagramma, un formato grafico la visualizzazione di tutte le tabelle importate, con linee tra di essi. Le linee tra le tabelle indicano le relazioni create automaticamente quando sono stati importati i dati.
    
    ![as-lesson4-diagram](../tutorial-tabular-1400/media/as-lesson4-diagram.png)
  
    > [!NOTE]
    > Se non tutte le relazioni tra tabelle, probabilmente significa che non sono presenti relazioni tra tali tabelle nell'origine dei dati.

    Includere come numero di tabelle possibile utilizzando i controlli della mini mappa nell'angolo inferiore destro della finestra di progettazione del modello. È anche possibile fare clic sulle tabelle e trascinarle in posizioni diverse, avvicinandole o disponendole in un ordine particolare. Spostamento di tabelle non influenza le relazioni tra le tabelle. Per visualizzare tutte le colonne in una determinata tabella, fare clic e trascinare un bordo della tabella per espanderla o renderla più piccoli.  
  
2.  Fare clic sulla linea continua tra il **DimCustomer** tabella e **DimGeography** tabella. La linea continua tra queste due tabelle viene illustrata che questa relazione è attiva, vale a dire, che viene utilizzato per impostazione predefinita durante il calcolo delle formule DAX.  
  
    Si noti il **GeographyKey** colonna il **DimCustomer** tabella e il **GeographyKey** colonna il **DimGeography** tabella appaiono ora entrambe all'interno di una casella. Queste colonne vengono utilizzate nella relazione. Le proprietà della relazione sono ora visualizzate nella finestra **Proprietà** .  
  
    > [!TIP]  
    > È inoltre possibile utilizzare la finestra di dialogo Gestisci relazioni per mostrare le relazioni tra tutte le tabelle in un formato di tabella. In Esplora modelli tabulari, fare doppio clic su **relazioni** > **Gestisci relazioni**.
  
3.  Verificare le relazioni seguenti siano state create quando ognuna delle tabelle sono state importate dal database AdventureWorksDW:  
  
    |Attiva|Tabella|Tabella di ricerca correlata|  
    |----------|---------|------------------------|  
    |Sì|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |Sì|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |Sì|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |Sì|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |Sì|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    Se le relazioni sono mancanti, verificare il modello include le seguenti tabelle: DimCustomer, DimDate, DimGeography, DimProduct, DimProductCategory, DimProductSubcategory e FactInternetSales. Se le tabelle dalla stessa connessione origine dati vengono importate in momenti, tutte le relazioni tra diversi tali tabelle non vengono create e devono essere create manualmente. Se nessuna relazione è visualizzato, significa che non sono presenti relazioni nell'origine dei dati. È possibile crearli manualmente nel modello di dati.

### <a name="take-a-closer-look"></a>Esaminare attentamente

Nella vista diagramma, si noti una freccia, un asterisco e un numero di righe che mostrano la relazione tra tabelle.

![as-lesson4-line](../tutorial-tabular-1400/media/as-lesson4-line.png)

La freccia indica la direzione del filtro. L'asterisco viene illustrata la tabella è la *molti* lato la cardinalità della relazione e quello Mostra questa tabella è la *uno* lato della relazione. Se si desidera modificare una relazione. ad esempio, modificare la direzione del filtro della relazione o cardinalità, fare doppio clic sulla linea della relazione per aprire la finestra di dialogo Modifica relazione.

![as-lesson4-edit](../tutorial-tabular-1400/media/as-lesson4-edit.png)

Queste funzionalità sono concepite per la modellazione dei dati avanzate e all'esterno dell'ambito di questa esercitazione. Per ulteriori informazioni, vedere [bidirezionale tra i filtri per i modelli tabulari in Analysis Services](../tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md).

In alcuni casi, potrebbe essere necessario creare relazioni aggiuntive tra tabelle nel modello per supportare una logica di business specifica. Per questa esercitazione, è necessario creare tre relazioni aggiuntive tra la tabella FactInternetSales e la tabella DimDate.  
  
#### <a name="to-add-new-relationships-between-tables"></a>Per aggiungere nuove relazioni tra tabelle  
  
1.  In Progettazione modelli nel **FactInternetSales** tabella, fare clic e tenere premuto il **OrderDate** colonna, quindi trascinare il cursore di **data** colonna il **DimDate** e quindi rilasciare.  

    Verrà visualizzata di una linea a tinta unita che è stata creata una relazione attiva tra il **OrderDate** colonna il **Internet Sales** tabella e **data** colonna il **data** tabella. 
  
      ![as-lesson4-new](../tutorial-tabular-1400/media/as-lesson4-new.png) 
  
    > [!NOTE]  
    > Quando si creano relazioni, viene selezionata automaticamente la cardinalità e filtro la direzione tra la tabella primaria e la tabella di ricerca correlata.  
  
2.  Nel **FactInternetSales** tabella, fare clic e tenere premuto il **DueDate** colonna, quindi trascinare il cursore di **data** colonna il **DimDate** e quindi rilasciare.  
  
    Viene visualizzato di una linea punteggiata che è stata creata una relazione inattiva tra la **DueDate** colonna il **FactInternetSales** tabella e **data** colonna il **DimDate** tabella. È possibile creare più relazioni tra tabelle, ma può essere attiva una sola relazione per volta. Relazioni inattive possono essere reso attive per eseguire aggregazioni speciale nelle espressioni DAX personalizzate.  
  
3.  Creare infine un'ulteriore relazione. Nel **FactInternetSales** tabella, fare clic e tenere premuto il **ShipDate** colonna, quindi trascinare il cursore di **data** colonna il **DimDate** e quindi rilasciare.  
    
     ![as-lesson4-newinactive](../tutorial-tabular-1400/media/as-lesson4-newinactive.png)
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 5: Creare colonne calcolate](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).
  
  
  
