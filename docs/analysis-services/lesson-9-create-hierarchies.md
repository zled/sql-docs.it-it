---
title: 'Lezione 10: Creare gerarchie | Documenti Microsoft'
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 003cf0dbb536397f1bebd4811a8d15c99a8211f5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-9-create-hierarchies"></a>Lezione 9: Creare gerarchie
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione si procederà alla creazione di gerarchie. Le gerarchie sono gruppi di colonne disposti in livelli. Una gerarchia Geografia potrebbe ad esempio includere i sottolivelli Paese, Stato, Regione e Città. Le gerarchie possono essere visualizzate separatamente rispetto alle altre colonne in un elenco di campi di un'applicazione client di creazione di report, per semplificarne l'esplorazione e l'inserimento in un report da parte degli utenti client. Per ulteriori informazioni, vedere [gerarchie](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Per creare gerarchie, si utilizzerà Progettazione modelli in *vista diagramma*. Creazione e la gestione di gerarchie non è supportata in vista dati.  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 8: creare prospettive](../analysis-services/lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Creare gerarchie  
  
#### <a name="to-create-a-category-hierarchy-in-the-dimproduct-table"></a>Per creare una gerarchia di categorie della tabella DimProduct  
  
1.  In Progettazione modelli (vista diagramma) fare doppio clic su di **DimProduct** tabella > **crea gerarchia**. Verrà visualizzata una nuova gerarchia nella parte inferiore della finestra della tabella. Rinominare la gerarchia **categoria**.  
  
2.  Fare clic e trascinare il **ProductCategoryName** la nuova colonna **categoria** gerarchia.  
  
3.  Nel **categoria** gerarchia, fare doppio clic su di **ProductCategoryName** > **rinominare**, quindi digitare **categoria**.  
  
    > [!NOTE]  
    > La ridenominazione di una colonna in una gerarchia non comporta la ridenominazione della colonna nella tabella. Una colonna in una gerarchia è solo una rappresentazione della colonna nella tabella.  
  
4.  Fare clic e trascinare il **ProductSubcategoryName** colonna per il **categoria** gerarchia. Rinominare la cartella **Subcategory**. 
  
5.  Fare doppio clic su di **ModelName** colonna > **aggiungere alla gerarchia**, quindi selezionare **categoria**. Eseguire la stessa operazione **EnglishProductName**. Rinominare queste colonne nella gerarchia di **modello** e **prodotto**.  

    ![come tabulare-lesson9-categorie](../analysis-services/media/as-tabular-lesson9-category.png)
  
#### <a name="to-create-hierarchies-in-the-dimdate-table"></a>Per creare gerarchie nella tabella DimDate  
  
1.  Nel **DimDate** tabella, creare una nuova gerarchia denominata **calendario**.  
  
3.  Aggiungere le colonne seguenti nell'ordine:

    *  CalendarYear
    *  CalendarSemester
    *  CalendarQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
    
4.  Nel **DimDate** tabella, creare un **fiscale** gerarchia. Includere le colonne seguenti:  
  
    *  FiscalYear
    *  FiscalSemester
    *  FiscalQuarter
    *  MonthCalendar
    *  DayNumberOfMonth
  
5.  Infine, nel **DimDate** tabella, creare un **ProductionCalendar** gerarchia. Includere le colonne seguenti:  
    *  CalendarYear
    *  WeekNumberOfYear
    *  DayNumberOfWeek
  
 ## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 10: creare partizioni](../analysis-services/lesson-10-create-partitions.md). 
  
  

