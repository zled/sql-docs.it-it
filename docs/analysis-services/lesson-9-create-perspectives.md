---
title: "Lezione 9: Creare prospettive | Microsoft Docs"
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
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 9: Creare prospettive
In questa lezione verrà creata una prospettiva Internet Sales. Una prospettiva consente di definire un subset visualizzabile di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Quando un utente si connette a un modello tramite una prospettiva, vengono visualizzati solo gli oggetti del modello (tabelle, colonne, misure, gerarchie e KPI) come campi definiti in tale prospettiva.  
  
La prospettiva Internet Sales creata in questa lezione escluderà l'oggetto Customer table. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, tali oggetti sono ancora presenti nel modello; tuttavia non sono visibili in un elenco di campi di un client di creazione di report. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire punti di vista diversi del modello, ad esempio relativi a inventario e forza vendita.  
  
Per altre informazioni, vedere [Prospettive &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario aver completato la lezione precedente: [Lezione 8: Creare indicatori di prestazioni chiave](../analysis-services/lesson-8-create-key-performance-indicators.md).  
  
## Creare prospettive  
  
#### Per creare una prospettiva Internet Sales  
  
1.  In Progettazione modelli, nel menu **Modello** scegliere **Prospettive** e quindi **Crea e gestisci**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Per rinominare la prospettiva, fare doppio clic sull'intestazione di colonna **New Perspective 1** e quindi digitare **Internet Sales**.  
  
4.  In **Campi** selezionare le tabelle seguenti: **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory** e **Internet Sales**.  
  
    Si noti che sono state escluse la tabella Customer e tutte le colonne relative da questa prospettiva. In un secondo momento, nella Lezione 12 si utilizzerà la funzionalità Analizza in Excel per testare questa prospettiva. L'elenco campi tabella pivot di Excel includerà ogni tabella a eccezione di Customer.  
  
5.  Verificare le selezioni, assicurandosi che la tabella **Customer** non sia selezionata e fare clic su **OK**.  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 10: Creare gerarchie](../analysis-services/lesson-10-create-hierarchies.md).  
  
  
  
