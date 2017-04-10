---
title: "Lezione 4: Contrassegna come tabella data | Microsoft Docs"
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
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 4: Contrassegna come tabella data
Nella Lezione 2: Aggiungere dati è stata importata una tabella delle dimensioni denominata DimDate che è stata poi rinominata Date. Mentre nel modello questa tabella è ora denominata Date, può anche essere nota come *tabella data*, in quanto sono contenuti dati relativi a data e ora.  
  
Ogni volta che si usano le funzioni di Business Intelligence per le gerarchie temporali nei calcoli, come accadrà più avanti per creare le misure, è necessario specificare le proprietà della tabella relativa alla data, tra cui una *tabella data* e un identificatore univoco *colonna data* in tale tabella. È quindi possibile creare relazioni valide tra altre tabelle e la tabella data, che sono necessarie per eseguire calcoli utilizzando le funzioni di Business Intelligence per le gerarchie temporali DAX.  
  
In questa lezione si contrassegnerà la tabella data importata e rinominata come *tabella data* e la colonna data (nella tabella data) come *colonna data* (identificatore univoco). Gli utilizzi del nome Data possono creare confusione, ma solo inizialmente.  
  
Tempo stimato per il completamento della lezione: **3 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 3: Rinominare colonne](../analysis-services/lesson-3-rename-columns.md).  
  
### Per impostare Contrassegna come tabella data  
  
1.  In Progettazione modelli fare clic sulla tabella (scheda) **Data**.  
  
2.  Selezionare la colonna **Data**, quindi nella finestra **Proprietà** verificare che **Data** sia selezionata in **Tipo di dati**.  
  
3.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
4.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco.  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 5: Creare relazioni](../analysis-services/lesson-5-create-relationships.md).  
  
  
  
