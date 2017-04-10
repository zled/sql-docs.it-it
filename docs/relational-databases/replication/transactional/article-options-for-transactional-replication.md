---
title: "Opzioni degli articoli per la replica transazionale | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "articoli [replica di SQL Server], opzioni di replica transazionale"
  - "replica transazionale, opzioni degli articoli"
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Opzioni degli articoli per la replica transazionale
  Sono disponibili svariate opzioni per gli articoli delle repliche transazionali. La replica transazionale consente infatti di eseguire le operazioni seguenti:  
  
-   Specificare le modalità di propagazione delle modifiche dal server di pubblicazione ai Sottoscrittori. Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
-   Specificare che l'esecuzione di una stored procedure deve essere replicata. Ciò risulta utile per la replica dei risultati di stored procedure orientate alla manutenzione che influiscono su ingenti quantità di dati. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Specificare le opzioni di schema, ad esempio se i vincoli e i trigger vengono copiati nel Sottoscrittore. Per ulteriori informazioni, vedere [specificare le opzioni dello Schema](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Utilizzare i filtri di righe e di colonne. L'applicazione di filtri agli articoli di una tabella consente di creare partizioni di dati da pubblicare. Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  