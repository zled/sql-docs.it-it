---
title: "Lezione 5: Creare relazioni | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 5: Creare relazioni
In questa lezione verranno verificate le relazioni create automaticamente al momento dell'importazione dei dati e verranno aggiunte nuove relazioni tra tabelle diverse. Una relazione è una connessione tra due tabelle che stabilisce in che modo devono essere correlati i dati nelle due tabelle. Tra la tabella Product e la tabella Product Subcategory vi è ad esempio una relazione basata sul fatto che ogni prodotto appartiene a una sottocategoria. Per altre informazioni, vedere [Relazioni &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **10 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 3: Rinominare colonne](../analysis-services/lesson-3-rename-columns.md).  
  
## Esaminare le relazioni esistenti e aggiungere nuove relazioni  
Quando sono stati importati i dati utilizzando l'Importazione guidata tabella, sono state importate sette tabelle del database AdventureWorksDW. In genere, se si importano dati da un'origine relazionale, le relazioni esistenti vengono importate automaticamente insieme ai dati. Prima di procedere con la creazione del modello, è tuttavia necessario verificare che le relazioni tra tabelle siano state create correttamente. Per questa esercitazione, verranno inoltre aggiunte tre nuove relazioni.  
  
#### Per esaminare le relazioni esistenti  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]scegliere **Vista modelli** dal menu **Modello**, quindi fare clic su **Vista diagramma**.  
  
    La finestra Progettazione modelli viene ora visualizzata nella vista diagramma, un formato grafico in cui sono visualizzate tutte le tabelle importate, con linee tra di esse. Le linee tra le tabelle indicano le relazioni create automaticamente quando sono stati importati i dati.  
  
    Usare i controlli della mini mappa nell'angolo inferiore destro di Progettazione modelli per regolare la vista in modo da includere il maggior numero di tabelle possibile. È anche possibile fare clic sulle tabelle e trascinarle in posizioni diverse, avvicinandole o disponendole in un ordine particolare. Lo spostamento delle tabelle non influisce sulle relazioni già presenti tra le tabelle. Per visualizzare tutte le colonne di una tabella specifica, fare clic su un bordo della tabella e trascinare per espanderla o renderla più piccola.  
  
2.  Fare clic sulla linea continua tra la tabella **Customer** e la tabella **Geography**. La linea continua tra queste due tabelle indica che questa relazione è attiva, ovvero viene utilizzata per impostazione predefinita nel calcolo delle formule DAX.  
  
    Si noti che la colonna **Geography Id** nella tabella **Customer** e la colonna **Geography Id** nella tabella **Geography** appaiono ora entrambe all'interno di una casella. Ciò indica che si tratta delle colonne utilizzate nella relazione. Le proprietà della relazione sono ora visualizzate nella finestra **Proprietà**.  
  
    > [!TIP]  
    > Oltre a usare Progettazione modelli nella vista diagramma, è anche possibile usare la finestra di dialogo **Gestisci relazioni** per specificare le relazioni tra tutte le tabelle in formato di tabella. Fare clic sul menu **Tabella** e quindi su **Gestisci relazioni**. Nella finestra di dialogo **Gestisci relazioni** sono visualizzate le relazioni create automaticamente quando sono stati importati i dati.  
  
3.  Usare Progettazione modelli nella vista diagramma oppure la finestra di dialogo **Gestisci relazioni** per verificare che le relazioni seguenti siano state create quando ognuna delle tabelle è stata importata dal database AdventureWorksDW:  
  
    |Attiva|Tabella|Tabella di ricerca correlata|  
    |----------|---------|------------------------|  
    |Sì|**Customer [Geography Id]**|**Geography [Geography Id]**|  
    |Sì|**Product [Product Subcategory Id]**|**Product Subcategory [Product Subcategory Id]**|  
    |Sì|**Product Subcategory [Product Category Id]**|**Product Category [Product Category Id]**|  
    |Sì|**Internet Sales [Customer Id]**|**Customer [Customer Id]**|  
    |Sì|**Internet Sales [Product Id]**|**Product [Product Id]**|  
  
Se qualsiasi relazione indicata nella tabella precedente non è presente, verificare che il modello includa le tabelle seguenti: Customer, Date, Geography, Product, Product Category, Product Subcategory e Internet Sales. Se tabelle della stessa connessione all'origine dati vengono importate in momenti distinti, non verranno create relazioni tra tali tabelle, che dovranno essere create manualmente.  
  
In alcuni casi, potrebbe essere necessario creare relazioni aggiuntive tra tabelle nel modello per supportare una logica di business specifica. Per questa esercitazione, è necessario creare tre relazioni aggiuntive tra la tabella Internet Sales e la tabella Date.  
  
#### Per aggiungere nuove relazioni tra tabelle  
  
1.  In Progettazione modelli, nella tabella **Internet Sales** fare clic e tenere premuto il pulsante del mouse sulla colonna **Order Date**, quindi trascinare il cursore nella colonna **Date** della tabella **Date** e infine rilasciare.  
  
    Viene visualizzata una linea continua per indicare che è stata creata una relazione attiva tra la colonna **Order Date** nella tabella **Internet Sales** e la colonna **Date** nella tabella **Date**.  
  
    > [!NOTE]  
    > Quando si creano relazioni, l'ordine tra la tabella primaria e la tabella di ricerca correlata viene definito automaticamente in modo corretto.  
  
2.  Nella tabella **Internet Sales** fare clic e tenere premuto il pulsante del mouse sulla colonna **Due Date**, quindi trascinare il cursore nella colonna **Date** della tabella **Date** e infine rilasciare.  
  
    Viene visualizzata una linea punteggiata per indicare che è stata creata una relazione non attiva tra la colonna **Due Date** nella tabella **Internet Sales** e la colonna **Date** nella tabella **Date**. È possibile creare più relazioni tra tabelle, ma può essere attiva una sola relazione per volta.  
  
3.  Creare infine un'ulteriore relazione. In Progettazione modelli, nella tabella **Internet Sales** fare clic e tenere premuto il pulsante del mouse sulla colonna **Ship Date**, quindi trascinare il cursore nella colonna **Date** della tabella **Date** e infine rilasciare.  
  
    Viene visualizzata una linea punteggiata per indicare che è stata creata una relazione non attiva tra la colonna **Ship Date** nella tabella **Internet Sales** e la colonna **Date** nella tabella **Date**.  
  
## Passaggio successivo  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 6: Creare colonne calcolate](../analysis-services/lesson-6-create-calculated-columns.md).  
  
  
  
