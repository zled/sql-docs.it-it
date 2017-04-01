---
title: "Lezione 10: Creare gerarchie | Microsoft Docs"
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
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 10: Creare gerarchie
In questa lezione si procederà alla creazione di gerarchie. Le gerarchie sono gruppi di colonne disposti in livelli. Una gerarchia Geografia potrebbe ad esempio includere i sottolivelli Paese, Stato, Regione e Città. Le gerarchie possono essere visualizzate separatamente rispetto alle altre colonne in un elenco di campi di un'applicazione client di creazione di report, per semplificarne l'esplorazione e l'inserimento in un report da parte degli utenti client. Per altre informazioni, vedere [Gerarchie &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Per creare le gerarchi viene usata la funzionalità Progettazione modelli in *Vista diagramma*. La creazione e la gestione di gerarchie non sono supportate in Progettazione modelli in Vista dati.  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 9: Creare prospettive](../Topic/Lesson%209:%20Create%20Perspectives.md).  
  
## Creare gerarchie  
  
#### Per creare una gerarchia Category nella tabella Product  
  
1.  In Progettazione modelli fare clic sul menu **Modello**, scegliere **Vista modelli** e fare clic su **Vista diagramma**.  
  
  
  
2.  Fare clic con il pulsante destro del mouse sulla tabella **Product** e scegliere **Crea gerarchia**. Verrà visualizzata una nuova gerarchia nella parte inferiore della finestra della tabella.  
  
3.  Rinominare la gerarchia digitando **Category** e premere INVIO.  
  
4.  Nella tabella **Product** fare clic sulla colonna **Product Category Name**, trascinarla nella gerarchia **Category** e infine rilasciarla sopra il nome **Category**.  
  
5.  Nella gerarchia **Category** fare clic con il pulsante destro del mouse sulla colonna **Product Category Name**, fare clic su **Rinomina** e digitare **Category**.  
  
    > [!NOTE]  
    > La ridenominazione di una colonna in una gerarchia non comporta la ridenominazione della colonna nella tabella. Una colonna in una gerarchia è solo una rappresentazione della colonna nella tabella.  
  
6.  Nella tabella **Product** fare clic e trascinare la colonna **Product Subcategory Name** nella gerarchia **Category**.  
  
7.  Rinominare **Product Subcategory Name**in **Subcategory**.  
  
8.  Selezionare e trascinare le colonne **Model Name** e **Product Name** nell'ordine e posizionarle sotto la colonna **Product Subcategory Name**. Rinominare queste colonne in **Model** e **Product**, rispettivamente.  
  
#### Per creare gerarchie nella tabella Date  
  
1.  In Progettazione modelli fare clic con il pulsante destro del mouse sulla tabella **Date** e scegliere **Crea gerarchia**.  
  
2.  Rinominare la gerarchia in **Calendar**.  
  
3.  Aggiungere le colonne seguenti, in ordine, quindi rinominarle:  
  
    |Colonna|Rinominare in:|  
    |----------|--------------|  
    |Calendar Year|Year|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Day|  
  
4.  Nella tabella **Date** ripetere i passaggi precedenti, creando una gerarchia **Fiscal** e includendo le colonne seguenti:  
  
    |Colonna|Rinominare in:|  
    |----------|--------------|  
    |Fiscal Year|Year|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|Day|  
  
5.  Infine, nella tabella **Date** ripetere i passaggi precedenti, creando una gerarchia **Production Calendar** e includendo le colonne seguenti:  
  
    |Colonna|Rinominare in:|  
    |----------|--------------|  
    |Calendar Year|Year|  
    |Week Number Of Year|Week|  
    |Day Of Week|Day|  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 11: Creare partizioni](../analysis-services/lesson-11-create-partitions.md).  
  
  
  
