---
title: "Lezione dell'esercitazione di Analysis Services 2: ottenere i dati | Documenti Microsoft"
description: Viene descritto come ottenere e importare i dati del progetto di Analysis Services tutorial.
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 28532aa0c568961802c02515bbcfa99a2c270330
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="get-data"></a>Recuperare i dati

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione è utilizzare **recupera dati** per connettersi al database di esempio AdventureWorksDW, selezionare i dati, l'anteprima e filtro e quindi importarli nell'area di lavoro modello.  
  
Usando recupera dati, è possibile importare dati da una vasta gamma di origini. Dati sono inoltre possibile eseguire query tramite un'espressione Power Query M o [espressione di query SQL nativa](../tabular-models/ssas-import-query.md).

> [!NOTE]
> Attività e le immagini in questa esercitazione mostrano la connessione a un database AdventureWorksDW2014 in un server locale. In alcuni casi, un database AdventureWorksDW in Azure SQL Data Warehouse può visualizzare oggetti diversi. Tuttavia, sono fondamentalmente lo stesso.
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 1: creare un nuovo progetto di modello tabulare](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Creare una connessione  
  
#### <a name="to-create-a-connection-to-the-adventureworksdw-database"></a>Per creare una connessione al database AdventureWorksDW  
  
1.  In **Esplora modelli tabulari**, fare doppio clic su **origini dati** > **Importa da origine dati**.  
  
    Verrà avviata **recupera dati**, che consente di connettersi a un'origine dati. Se non viene visualizzato Esplora modelli tabulari, **Esplora**, fare doppio clic su **Model.bim** per aprire il modello nella finestra di progettazione. 
    
    ![as-lesson2-getdata](../tutorial-tabular-1400/media/as-lesson2-getdata.png)
  
2.  Nel recupero dei dati, fare clic su **Database** > **Database di SQL Server** > **Connetti**.  
  
3.  Nel **Database di SQL Server** finestra di dialogo, nella **Server**, digitare il nome del server in cui è installato il database AdventureWorksDW e quindi fare clic su **Connetti**.  

4.  Quando viene richiesto di immettere le credenziali, è necessario specificare le credenziali di che Analysis Services utilizza per connettersi all'origine dei dati durante l'importazione e l'elaborazione dei dati. In **modalità di rappresentazione**selezionare **rappresentare l'Account**, quindi immettere le credenziali e quindi fare clic su **Connetti**. È consigliabile che utilizzare un account in cui la password non ha scadenza.

    ![as-lesson2-account](../tutorial-tabular-1400/media/as-lesson2-account.png)
  
    > [!NOTE]  
    > L'utilizzo di un account utente e una password di Windows rappresenta il metodo più sicuro per la connessione a un'origine dati.
  
5.  Nel Pannello di navigazione, selezionare il **AdventureWorksDW** database e quindi fare clic su **OK**. Questo modo viene creata la connessione al database. 
  
6.  Nel Pannello di navigazione, selezionare la casella di controllo per le tabelle seguenti: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, e **FactInternetSales**.  

    ![come-della lezione 2-selezionare-tabelle](../tutorial-tabular-1400/media/as-lesson2-select-tables.png)
  
Dopo aver scelto OK, verrà aperto l'Editor di Query. Nella sezione successiva, si seleziona solo i dati da importare.

  
## <a name="filter-the-table-data"></a>Filtrare i dati della tabella  

Le tabelle nel database di esempio AdventureWorksDW sono dati che non sono necessari includere nel modello. Se possibile, si desidera filtrare i dati non necessari per risparmiare spazio in memoria utilizzato dal modello. Escludere alcune colonne dalle tabelle in modo non si importati nel database dell'area di lavoro, o il database modello dopo che è stato distribuito. 
  
#### <a name="to-filter-the-table-data-before-importing"></a>Per filtrare i dati della tabella prima dell'importazione  
  
1.  Nell'Editor di Query, selezionare il **DimCustomer** tabella. Verrà visualizzata una vista della tabella DimCustomer nell'origine dei dati (il database di esempio AdventureWorksDW). 
  
2.  Selezione multipla (Ctrl + clic) **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**, quindi pulsante destro del mouse e quindi fare clic su **Rimuovi colonne**. 

    ![come della lezione 2-remove-colonne](../tutorial-tabular-1400/media/as-lesson2-remove-columns.png)
  
    Poiché i valori per queste colonne non sono attinenti all'analisi delle vendite Internet, non è necessario importare queste colonne. Eliminazione di colonne non necessarie rende il modello più snelli ed efficienti.  

    > [!TIP]
    > Se si commette un errore, è possibile eseguire il backup eliminando un passaggio in **passaggi applicati**.   
    
    ![come della lezione 2-remove-colonne](../tutorial-tabular-1400/media/as-lesson2-remove-step.png)

  
4.  Filtrare le tabelle restanti rimuovendo le colonne seguenti in ogni tabella:  
    
    **DimDate**
    
      |Colonna|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |Colonna|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |Colonna|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |Colonna|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |Colonna|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      Nessuna colonna è stato rimosso.
  
## <a name="Import"></a>Import the selected tables and column data  

Ora che è stato visualizzato in anteprima e filtrati i dati non necessari, è possibile importare il resto dei dati che desiderato. La procedura guidata consente di importare i dati delle tabelle e qualsiasi relazione presente tra le tabelle. Vengono create nuove tabelle e colonne nel modello e non è possibile importare i dati esclusi tramite filtro.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Per importare i dati delle tabelle e delle colonne selezionati  
  
1.  Verificare le selezioni. Se tutto sembra corretto, fare clic su **importazione**. La finestra di dialogo di elaborazione dei dati viene visualizzato lo stato dei dati verrà importati dall'origine dati nel database dell'area di lavoro.
  
    ![as-lesson2-success](../tutorial-tabular-1400/media/as-lesson2-success.png) 
  
2.  Scegliere **Chiudi**.  

  
## <a name="save-your-model-project"></a>Salvare il progetto di modello  

È importante salvare frequentemente il progetto di modello.  
  
#### <a name="to-save-the-model-project"></a>Per salvare il progetto di modello  
  
-   Click **Salva tutto** > **File**.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 3: Contrassegna come tabella data](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md).

  
  
