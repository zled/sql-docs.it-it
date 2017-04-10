---
title: "Lezione 6: Creare colonne calcolate | Microsoft Docs"
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
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 6: Creare colonne calcolate
In questa lezione verranno creati nuovi dati nel modello aggiungendo colonne calcolate. Una colonna calcolata è basata sui dati già presenti nel modello. Per altre informazioni, vedere [Colonne calcolate &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/calculated-columns-ssas-tabular.md).  
  
Verranno create cinque nuove colonne calcolate in tre tabelle diverse. I passaggi sono leggermente diversi per ogni attività. L'obiettivo è quello di mostrare che vi sono diversi metodi per creare nuove colonne, rinominarle e collocarle in diverse posizioni in una tabella.  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 5: Creare relazioni](../analysis-services/lesson-5-create-relationships.md).  
  
## Creare colonne calcolate  
  
#### Creare una colonna calcolata Month Calendar nella tabella Date  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Vista modelli** nel menu **Modello**, quindi fare clic su **Vista dati**.  
  
    Le colonne calcolate possono essere create solo tramite Progettazione modelli in Vista dati.  
  
2.  In Progettazione modelli fare clic sulla tabella (scheda) **Data**.  
  
3.  Fare clic con il pulsante destro del mouse sulla colonna **Calendar Quarter**, quindi scegliere **Inserisci colonna**.  
  
    Una nuova colonna denominata **CalculatedColumn1** verrà inserita a sinistra della colonna **Calendar Quarter**.  
  
4.  Sulla barra della formula sopra la tabella digitare la formula seguente. La funzionalità Completamento automatico consente di digitare i nomi completi di colonne e tabelle ed elencare le funzioni disponibili.  
  
    **=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
    I valori vengono quindi popolati per tutte le righe nella colonna calcolata. Scorrendo la tabella verso il basso, si vedrà che le righe possono avere valori diversi per questa colonna, in base ai dati presenti in ogni riga.  
  
    > [!NOTE]  
    > Se viene visualizzato un errore, verificare che i nomi di colonna nella formula corrispondano ai nomi di colonna modificati in [Lezione 3: Rinominare colonne](../analysis-services/lesson-3-rename-columns.md).  
  
5.  Rinominare questa colonna in **Month Calendar**.  
  
La colonna calcolata Month Calendar fornisce un nome ordinabile per il mese.  
  
#### Creare una colonna calcolata Day of Week nella tabella Date  
  
1.  Con la tabella **Date** ancora attiva, fare clic sul menu **Colonna**, quindi scegliere **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
  
    **=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]**  
  
    Dopo avere completato la compilazione della formula, premere INVIO. La nuova colonna verrà aggiunta all'estremità destra della tabella.  
  
3.  Rinominare la colonna in **Day of Week**.  
  
4.  Fare clic sull'intestazione di colonna, quindi trascinare la colonna tra le colonne **Day Name** e **Day of Month**.  
  
    > [!TIP]  
    > Lo spostamento delle colonne nella tabella semplifica l'esplorazione.  
  
La colonna calcolata Day of Week fornisce un nome ordinabile per il giorno della settimana.  
  
#### Creare una colonna calcolata Product Subcategory Name nella tabella Product  
  
1.  In Progettazione modelli selezionare la tabella **Product**.  
  
2.  Scorrere fino all'estremità destra della tabella. Si noti che la colonna all'estrema destra è denominata **Aggiungi colonna** (in corsivo). Fare clic sull'intestazione di colonna.  
  
3.  Sulla barra della formula digitare la formula seguente.  
  
    **=RELATED('Product Subcategory'[Product Subcategory Name])**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
4.  Rinominare la colonna in **Product Subcategory Name**.  
  
La colonna calcolata Product Subcategory Name viene utilizzata per creare una gerarchia nella tabella Product, che include dati della colonna Product Subcategory Name della tabella Product Subcategory. Le gerarchie non possono estendersi in più di una tabella. La creazione di gerarchie verrà eseguita più avanti, nella lezione 7.  
  
#### Creare una colonna calcolata Product Category Name nella tabella Product  
  
1.  Con la tabella **Product** ancora attiva, fare clic sul menu **Colonna**, quindi scegliere **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
  
    **=RELATED('Product Category'[Product Category Name])**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
3.  Rinominare la colonna in **Product Category Name**.  
  
La colonna calcolata Product Category Name viene utilizzata per creare una gerarchia nella tabella Product, che include dati della colonna Product Category Name della tabella Product Category. Le gerarchie non possono estendersi in più di una tabella.  
  
#### Creare una colonna calcolata Margin nella tabella Internet Sales  
  
1.  In Progettazione modelli selezionare la tabella **Internet Sales**.  
  
2.  Aggiungere una nuova colonna.  
  
3.  Sulla barra della formula digitare la formula seguente:  
  
    **=[Sales Amount]-[Total Product Cost]**  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
4.  Rinominare la colonna in **Margin**.  
  
5.  Trascinare la colonna tra le colonne **Sales Amount** e **Tax Amt**.  
  
La colonna calcolata Margin viene utilizzata per analizzare i margini di profitto per ogni riga (prodotto).  
  
## Passaggio successivo  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 7: Creare misure](../analysis-services/lesson-7-create-measures.md).  
  
  
  
