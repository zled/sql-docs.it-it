---
title: 'Lezione 2: Aggiungere dati | Documenti Microsoft'
ms.custom: 
ms.date: 06/19/2017
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
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: efd2e0c85d8c266050e74d5c363afe33e37c48c1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-2-add-data"></a>Lezione 2: Aggiungere dati
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione, si userà l'importazione guidata tabella in SSDT per connettersi al database di esempio AdventureWorksDW SQL, selezionare i dati, visualizzare in anteprima e filtrare i dati e quindi importare i dati nell'area di lavoro modello.  
  
Utilizzando l'Importazione guidata tabella è possibile importare dati da diverse origini relazionali, quali Access, SQL, Oracle, Sybase, Informix, DB2, Teradata e così via. I passaggi per l'importazione dei dati da ognuna di queste origini relazionali sono molto simili a quanto descritto di seguito. Inoltre è possibile selezionare dati tramite una stored procedure. Per ulteriori informazioni sull'importazione di dati e i diversi tipi di origini dati che è possibile importare, vedere [origini dati](../analysis-services/tabular-models/data-sources-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario aver completato la lezione precedente: [Lezione 1: Creare un nuovo modello di progetto tabulare](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Creare una connessione  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2014-database"></a>Per creare una connessione a un database AdventureWorksDW2014  
  
1.  In Esplora modelli tabulari, fare doppio clic su **origini dati** > **Importa da origine dati**.  
  
    Verrà avviata l'importazione guidata tabella, che consente di configurare una connessione a un'origine dati. Se non viene visualizzato Esplora modelli tabulari, fare doppio clic su **Model.bim** in **Esplora** per aprire il modello nella finestra di progettazione. 
    
    ![come-tabulare-2-tempo](../analysis-services/media/as-tabular-lesson2-tme.png) 

    Nota: Se si crea il modello a livello di compatibilità 1400, si noterà la nuova esperienza di recupera dati anziché l'importazione guidata tabella. Le finestre di dialogo verrà visualizzata alcune differenze rispetto alla procedura seguente, ma è comunque possibile seguire la procedura. 
  
2.  In Importazione guidata tabella, in **database relazionali**, fare clic su **Microsoft SQL Server** > **Avanti**.  
  
3.  Nella pagina **Connessione a un database di Microsoft SQL Server** , in **Nome descrittivo connessione**digitare **Adventure Works DB da SQL**.  
  
4.  In **nome Server**, digitare il nome del server in cui è installato il database AdventureWorksDW.  
  
5.  Nel **nome del Database** campi, selezionare **AdventureWorksDW**, quindi fare clic su **Avanti**.  
  
    ![come-tabulare-2-tiw-name](../analysis-services/media/as-tabular-lesson2-tiw-name.png)
  
6.  Nella pagina **Impostazioni di rappresentazione** specificare le credenziali usate da Analysis Services per la connessione all'origine dati quando vengono importati ed elaborati i dati. Verificare che l'opzione **Nome utente e password specifici di Windows** sia selezionata, immettere le credenziali di accesso a Windows in **Nome utente** e **Password**e fare clic su **Avanti**.  
  
    > [!NOTE]  
    > L'utilizzo di un account utente e una password di Windows rappresenta il metodo più sicuro per la connessione a un'origine dati. Per ulteriori informazioni, vedere [rappresentazione](../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
7.  Nella pagina **Scelta della modalità di importazione dei dati** verificare che l'opzione **Seleziona da un elenco di tabelle e viste per scegliere i dati da importare** sia selezionata. Poiché si vuole selezionare da un elenco di tabelle e viste, fare clic su **Avanti** per visualizzare un elenco di tutte le tabelle di origine nel database di origine.  
  
8.  Nella pagina **Selezione tabelle e viste** selezionare le caselle di controllo corrispondenti alle tabelle seguenti: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**e **FactInternetSales**.  
  
    **NON** fare clic su **Fine**.  
  
## <a name="FilterData"></a>Filter the table data  
La tabella DimCustomer che si sta importando dal database di esempio contiene un subset dei dati dal database di SQL Server Adventure Works originale. Verrà escludere alcune informazioni delle colonne della tabella DimCustomer che non sono necessarie quando importato nel modello. Se possibile, sarà possibile filtrare i dati che non verrà usati per risparmiare spazio in memoria utilizzato dal modello.  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>Per filtrare i dati della tabella prima dell'importazione  
  
1.  Selezionare la riga per il **DimCustomer** tabella e quindi fare clic su **anteprima e filtro**. Verrà visualizzata la finestra **Anteprima tabella selezionata** in cui sono visualizzate tutte le colonne della tabella di origine DimCustomer visualizzata.  
  
2.  Deselezionare la casella di controllo nella parte superiore delle colonne seguenti. **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**. 

    ![come-tabulare-2-tiw-Cancella](../analysis-services/media/as-tabular-lesson2-tiw-clear.png)
  
    Poiché i valori per queste colonne non sono attinenti all'analisi delle vendite Internet, non è necessario importare queste colonne. Eliminando le colonne non consentirà il modello più snelli ed efficienti.  
  
3.  Verificare che tutte le altre colonne siano selezionate e fare clic su **OK**.  
  
    Si noti che viene visualizzata la dicitura **Filtri applicati** nella colonna **Dettagli filtro** nella riga **DimCustomer** . Se si fa clic su tale collegamento, viene visualizzata una descrizione testuale dei filtri appena applicati.  
    
    ![come-tabulare-2--filtri applicati](../analysis-services/media/as-tabular-lesson2-applied-filters.png)
    
  
4.  Filtrare le tabelle restanti deselezionando le caselle di controllo per le colonne seguenti in ogni tabella:  
    
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
  
      |Colonna|  
      |------------------|  
      |**OrderDateKey**|  
      |**DueDateKey**|  
      |**ShipDateKey**|   
  
## <a name="Import"></a>Import the selected tables and column data  
Ora che è stato visualizzato in anteprima e filtrati i dati non necessari, è possibile importare il resto dei dati che desiderato. La procedura guidata consente di importare i dati delle tabelle e qualsiasi relazione presente tra le tabelle. Vengono create nuove tabelle e colonne nel modello e non verranno importati dati esclusi tramite filtro.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Per importare i dati delle tabelle e delle colonne selezionati  
  
1.  Verificare le selezioni. Se tutto sembra corretto, fare clic su **fine**.  
  
    Durante l'importazione dei dati la procedura guidata visualizza il numero di righe recuperate. Una volta importati tutti i dati, verrà visualizzato un messaggio in cui viene indicato il completamento dell'operazione.  
    
    ![come-tabulare-2-operazione riuscita](../analysis-services/media/as-tabular-lesson2-success.png) 
  
    > [!TIP]  
    > Per vedere le relazioni create automaticamente tra le tabelle importate, fare clic su **Dettagli** nella riga **Preparazione dati**. 
  
2.  Scegliere **Chiudi**.  
  
    Chiusura della procedura guidata e la progettazione di modelli ora mostra le tabelle importate. 
  
## <a name="save-your-model-project"></a>Salvare il progetto di modello  
È importante salvare frequentemente il progetto di modello.  
  
#### <a name="to-save-the-model-project"></a>Per salvare il progetto di modello  
  
-   Click **Salva tutto** > **File**.  
  
## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 3: contrassegna come tabella data](../analysis-services/lesson-3-mark-as-date-table.md).

  
  
