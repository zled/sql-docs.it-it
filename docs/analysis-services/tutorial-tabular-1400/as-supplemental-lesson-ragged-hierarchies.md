---
title: 'Lezione supplementare di Analysis Services tutorial: gerarchie incomplete | Documenti Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc5a2164576e2e6142d8835dad6f6c114b7a9c5b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Lezione supplementare - gerarchie incomplete

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione supplementare, risolvere un problema comune quando la trasformazione tramite pivot in gerarchie che contengono valori vuoti (membri) a livelli diversi. Ad esempio, un'organizzazione in cui un responsabile di alto livello ha sia responsabili di reparto sia non responsabili come subalterni. In alternativa, le gerarchie geografiche è composto da paese-regione-città, in cui alcune città non presentano padre o la provincia, ad esempio Washington, città del Vaticano. Quando si dispone di una gerarchia di membri vuoti, spesso discende a livelli diversi o incomplete.

![as-lesson-detail-ragged-hierarchies-table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

I modelli tabulari a livello di compatibilità 1400 presentano un ulteriore **Nascondi membri** proprietà per le gerarchie. Il **predefinito** impostazione presuppone che non esistono membri vuoti a qualsiasi livello. Il **nascondere i membri vuoti** impostazione consente di escludere i membri vuoti dalla gerarchia di quando aggiunto a una tabella pivot o un report.  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
In questo articolo lezione supplementare fa parte di un'esercitazione di modellazione tabulare. Prima di eseguire le attività in questa lezione supplementare, è necessario avere completato tutte le lezioni precedenti o dispone di un progetto di modello di esempio Adventure Works Internet Sales completato. 

Se si crea il progetto AW Internet Sales come parte dell'esercitazione, il modello non contiene ancora dati o gerarchie incomplete. Per completare questa lezione supplementare, è innanzitutto necessario creare il problema mediante l'aggiunta di alcune tabelle aggiuntive, creare relazioni, colonne calcolate, una misura e una nuova gerarchia organizzativa. La parte richiede circa 15 minuti. Quindi, è possibile risolverlo in pochi minuti.  

## <a name="add-tables-and-objects"></a>Aggiungere tabelle e gli oggetti
  
### <a name="to-add-new-tables-to-your-model"></a>Per aggiungere nuove tabelle al modello
  
1.  In Esplora modelli tabulari, espandere **origini dati**, quindi fare clic sulla connessione > **importazione nuove tabelle**.
  
2.  Nel Pannello di navigazione, selezionare **DimEmployee** e **FactResellerSales**, quindi fare clic su **OK**.

3.  Nell'Editor di Query, fare clic su **importazione**

4.  Creare gli elementi seguenti [relazioni](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | Tabella 1           | Colonna       | Direzione del filtro   | tabella 2     | Colonna      | Attiva |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | Valore predefinito            | DimDate     | Data        | Sì    |
    | FactResellerSales | DueDate      | Valore predefinito            | DimDate     | Data        | no     |
    | FactResellerSales | ShipDateKey  | Valore predefinito            | DimDate     | Data        | no     |
    | FactResellerSales | ProductKey   | Valore predefinito            | DimProduct  | ProductKey  | Sì    |
    | FactResellerSales | EmployeeKey  | Per entrambe le tabelle | DimEmployee | EmployeeKey | Sì    |

5. Nel **DimEmployee** tabella, creare la seguente [le colonne calcolate](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **Percorso** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **Nome completo** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **Level1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **Level2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Level5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  Nel **DimEmployee** tabella, creare un [gerarchia](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) denominato **organizzazione**. Aggiungere le colonne seguenti nell'ordine: **Level1**, **Level2**, **Level3**, **Level4**, **Level5**.

7.  Nel **FactResellerSales** tabella, creare la seguente [misura](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Utilizzare [analizza in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) per aprire Excel e creare automaticamente una tabella pivot.

9.  In **PivotTable Fields**, aggiungere il **organizzazione** gerarchia dal **DimEmployee** tabella **righe**e  **ResellerTotalSales** misura il **FactResellerSales** tabella **valori**.

    ![as-lesson-detail-ragged-hierarchies-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Come si vede nella tabella pivot, la gerarchia consente di visualizzare le righe che sono incomplete. Sono presenti molte righe in cui vengono visualizzati i membri vuoti.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Per risolverlo è l'impostazione di proprietà Nascondi membri gerarchia incompleta

1.  In **Esplora modelli tabulari**, espandere **tabelle** > **DimEmployee** > **gerarchie**  >  **Organizzazione**.

2.  In **proprietà** > **Nascondi membri**selezionare **nascondere i membri vuoti**. 

    ![As-Lesson-Detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  In Excel, aggiornare la tabella pivot. 

    ![as-lesson-detail-ragged-hierarchies-pivottable-refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Ora che ha un aspetto decisamente migliore.

## <a name="see-also"></a>Vedere anche   
[Lezione 9: Creare gerarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Lezione supplementare - sicurezza dinamica](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Lezione supplementare - righe di dettaglio](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
