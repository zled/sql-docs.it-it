---
title: "Lezione 1: Conversione di una tabella in una struttura gerarchica | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Lezione 1: Conversione di una tabella in una struttura gerarchica
I clienti che hanno tabelle che utilizzano un self-join per esprimere relazioni gerarchiche possono convertire le tabelle in una struttura gerarchica utilizzando questa lezione come guida. È relativamente facile eseguire la migrazione da questa rappresentazione a **hierarchyid**. Dopo la migrazione, gli utenti avranno una rappresentazione gerarchica compatta e facile da capire che può essere indicizzata in molti modi per eseguire query efficienti.  
  
In questa lezione, verrà esaminata una tabella esistente, verrà creata una nuova tabella contenente una colonna **hierarchyid** , verrà popolata la tabella con i dati della tabella di origine e infine verranno illustrate tre strategie di indicizzazione. In questa lezione sono inclusi gli argomenti seguenti:  
  
-   [Esame della struttura corrente della tabella Employee](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
-   [Popolamento di una tabella con dati gerarchici esistenti](../../relational-databases/tables/populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Ottimizzazione della tabella NewOrg](../../relational-databases/tables/optimizing-the-neworg-table.md)  
  
-   [Riepilogo: Conversione di una tabella in una struttura gerarchica](../../relational-databases/tables/summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## Prerequisiti  
Questa lezione richiede il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## Attività successiva della lezione  
[Esame della struttura corrente della tabella Employee](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
## Lezione successiva  
[Lezione 2: Creazione e gestione di dati in una tabella gerarchica](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
