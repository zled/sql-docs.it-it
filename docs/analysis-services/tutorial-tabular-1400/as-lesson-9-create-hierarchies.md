---
title: "Lezione dell'esercitazione di Analysis Services 9: creare gerarchie | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
ms.openlocfilehash: df99d05373d4d3087ef1d5fa5324ec645bf000b6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-hierarchies"></a>Creare gerarchie

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione è creare gerarchie. Le gerarchie sono gruppi di colonne disposte in livelli. Ad esempio, una gerarchia Geografia potrebbe essere sottolivelli per paese, stato, provincia e città. Le gerarchie possono essere visualizzate separatamente rispetto alle altre colonne in un elenco di campi di un'applicazione client di creazione di report, per semplificarne l'esplorazione e l'inserimento in un report da parte degli utenti client. Per ulteriori informazioni, vedere [gerarchie](../tabular-models/hierarchies-ssas-tabular.md)
  
Per creare gerarchie, utilizzare Progettazione modelli in *vista diagramma*. Creazione e la gestione di gerarchie non è supportata in vista dati.  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 8: creare prospettive](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Creare gerarchie  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Per creare una gerarchia di categorie della tabella DimProduct  
  
1.  In Progettazione modelli (vista diagramma) fare doppio clic su di **DimProduct** tabella > **crea gerarchia**. Verrà visualizzata una nuova gerarchia nella parte inferiore della finestra della tabella. Rinominare la gerarchia **categoria**.  
  
2.  Fare clic e trascinare il **ProductCategoryName** la nuova colonna **categoria** gerarchia.  
  
3.  Nel **categoria** gerarchia, fare doppio clic su **ProductCategoryName** > **rinominare**, quindi digitare **categoria**.  
  
    > [!NOTE]  
    > La ridenominazione di una colonna in una gerarchia non comporta la ridenominazione della colonna nella tabella. Una colonna in una gerarchia è solo una rappresentazione della colonna nella tabella.  
  
4.  Fare clic e trascinare il **ProductSubcategoryName** colonna per il **categoria** gerarchia. Rinominare la cartella **Subcategory**. 
  
5.  Fare doppio clic su di **ModelName** colonna > **aggiungere alla gerarchia**, quindi selezionare **categoria**. Rinominare la cartella **modello**.

6.  Infine, aggiungere **EnglishProductName** alla gerarchia di categorie. Rinominare la cartella **prodotto**.  

    ![as-lesson9-category](../tutorial-tabular-1400/media/as-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Per creare gerarchie nella tabella DimDate  
  
1.  Nel **DimDate** tabella, creare una gerarchia denominata **calendario**.  
  
3.  Aggiungere le colonne seguenti nell'ordine:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  Nel **DimDate** tabella, creare un **fiscale** gerarchia. Includere le colonne seguenti nell'ordine:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Infine, nel **DimDate** tabella, creare un **ProductionCalendar** gerarchia. Includere le colonne seguenti nell'ordine:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 10: Creare partizioni](../tutorial-tabular-1400/as-lesson-10-create-partitions.md). 
  
  
