---
title: "Lezione dell'esercitazione di Analysis Services 5: creare colonne calcolate | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8406ff8e3bf6981dedea21f6916101aa42b1061a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-calculated-columns"></a>Creare colonne calcolate

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, creare dati nel modello aggiungendo colonne calcolate. È possibile creare colonne calcolate (come le colonne personalizzate) quando si usa recupera dati, utilizzando l'Editor di Query o, più avanti in simili della finestra di progettazione del modello eseguire qui. Per ulteriori informazioni, vedere [le colonne calcolate](../tabular-models/ssas-calculated-columns.md).
  
Create cinque nuove colonne calcolate in tre tabelle diverse. I passaggi sono leggermente diversi per ogni attività che mostra esistono diversi modi per creare colonne, rinominarle e posizionarli in diverse posizioni in una tabella.  

In questa lezione è anche in cui utilizzare innanzitutto Data Analysis Expressions (DAX). DAX è un linguaggio speciale per la creazione di espressioni formula altamente personalizzabili per i modelli tabulari. In questa esercitazione è utilizzare DAX per creare colonne calcolate, misure e filtri di ruolo. Per ulteriori informazioni, vedere [DAX nei modelli tabulari](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md). 
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 4: creare relazioni](../tutorial-tabular-1400/as-lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Creare colonne calcolate  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Creare una colonna calcolata di MonthCalendar della tabella DimDate  
  
1.  Fare clic su di **modello** menu > **vista modello** > **vista dati**.  
  
    Le colonne calcolate possono essere create solo tramite Progettazione modelli in Vista dati.  
  
2.  In Progettazione modelli fare clic su di **DimDate** tabella (scheda).  
  
3.  Fare doppio clic su di **CalendarQuarter** intestazione di colonna e quindi fare clic su **Inserisci colonna**.  
  
    Una nuova colonna denominata **CalculatedColumn1** verrà inserita a sinistra della colonna **Calendar Quarter** .  
  
4.  Nella barra della formula sopra la tabella digitare la seguente formula DAX: completamento automatico consente di digitare i nomi completi di colonne e tabelle e vengono elencate le funzioni disponibili.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    I valori vengono quindi popolati per tutte le righe nella colonna calcolata. Se si scorre verso il basso nella tabella, si noterà righe possono avere valori diversi per questa colonna, in base ai dati in ogni riga.    
  
5.  Rinominare questa colonna come **MonthCalendar**. 

    ![as-lesson5-newcolumn](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
MonthCalendar calcolato colonna fornisce un nome ordinabile per mese.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Creare una colonna calcolata DayOfWeek della tabella DimDate  
  
1.  Con il **DimDate** ancora attiva, fare clic di tabella il **colonna** menu e quindi fare clic su **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Al termine della compilazione della formula, premere INVIO. La nuova colonna verrà aggiunta all'estremità destra della tabella.  
  
3.  Rinominare la colonna in **DayOfWeek**.  
  
4.  Fare clic sull'intestazione di colonna e quindi trascinare la colonna tra la **EnglishDayNameOfWeek** colonna e **DayNumberOfMonth** colonna.  
  
    > [!TIP]  
    > Lo spostamento delle colonne nella tabella semplifica l'esplorazione.  
  
L'enumerazione DayOfWeek calcolato colonna fornisce un nome ordinabile per il giorno della settimana.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Creare una colonna calcolata ProductSubcategoryName nella tabella DimProduct  
  
  
1.  Nel **DimProduct** tabella, scorrimento all'estrema destra della tabella. Si noti che la colonna all'estrema destra è denominata **Aggiungi colonna** (in corsivo). Fare clic sull'intestazione di colonna.  
  
2.  Sulla barra della formula digitare la formula seguente:  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Rinominare la colonna in **ProductSubcategoryName**.  
  
La colonna calcolata ProductSubcategoryName viene utilizzata per creare una gerarchia nella tabella DimProduct, inclusi i dati dalla colonna EnglishProductSubcategoryName nella tabella DimProductSubcategory. Le gerarchie non possono estendersi in più di una tabella. Creare gerarchie in un secondo momento nella lezione 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Creare una colonna calcolata ProductCategoryName nella tabella DimProduct  
  
1.  Con il **DimProduct** ancora attiva, fare clic di tabella il **colonna** menu e quindi fare clic su **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Rinominare la colonna in **ProductCategoryName**.  
  
La colonna calcolata di ProductCategoryName viene utilizzata per creare una gerarchia nella tabella DimProduct, inclusi i dati dalla colonna EnglishProductCategoryName nella tabella DimProductCategory. Le gerarchie non possono estendersi in più di una tabella.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Creare una colonna calcolata Margin nella tabella FactInternetSales  
  
1.  In Progettazione modelli selezionare la **FactInternetSales** tabella.  
  
2.  Creare una nuova colonna calcolata tra il **SalesAmount** colonna e **TaxAmt** colonna.  
  
3.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Rinominare la colonna in **Margin**.  
 
      ![as-lesson5-newmargin](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    La colonna calcolata Margin viene utilizzata per analizzare i margini di profitto per ogni vendita.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 6: Creare misure](../tutorial-tabular-1400/as-lesson-6-create-measures.md).
  
  
  
