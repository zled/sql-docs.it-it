---
title: "Opzioni degli articoli per la replica di tipo merge | Microsoft Docs"
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
  - "replica di tipo merge [replica di SQL Server], opzioni degli articoli"
  - "articoli [replica di SQL Server], opzioni di replica di tipo merge"
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Opzioni degli articoli per la replica di tipo merge
  Sono disponibili diverse opzioni per gli articoli di tabella di merge che consentono di adattare il comportamento della replica alle esigenze delle applicazioni. La replica di tipo merge consente di eseguire le operazioni seguenti:  
  
-   Utilizzare filtri di riga, join e di colonna. L'applicazione di filtri agli articoli di una tabella consente di creare partizioni di dati da pubblicare. Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Specificare se le modifiche del Sottoscrittore vengono caricate nel server di Pubblicazione. Per le applicazioni in cui è necessario che alcuni o tutti i dati siano di sola lettura nel Sottoscrittore, gli articoli di solo download sono vantaggiosi in termini di prestazioni. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con gli articoli Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Specificare che le eliminazioni di uno o più articoli non devono essere rilevate dai trigger di replica e dalle tabelle di sistema. Questa opzione può essere utile in molti scenari applicativi, inclusi quelli in cui vengono utilizzate eliminazioni batch che non richiedono una replica. Per ulteriori informazioni, vedere [Ottimizza prestazioni della replica di tipo Merge con rilevamento condizionale eliminare](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md).  
  
-   Specificare l'ordine di elaborazione degli articoli per garantire che corrisponda a quello richiesto dall'applicazione. Per ulteriori informazioni, vedere [specificare l'elaborazione dell'ordine di articoli di Merge](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
-   Specificare che i set di record correlati devono essere elaborati come unità. Per impostazione predefinita, la replica di tipo merge elabora le modifiche nelle tabelle procedendo riga per riga. Per ulteriori informazioni, vedere [modifiche a un gruppo di righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
-   Utilizzare il rilevamento e la risoluzione dei conflitti per i casi in cui è possibile che gli stessi dati vengano modificati in più nodi di una topologia. Per ulteriori informazioni, vedere [rilevare e risolvere i conflitti di replica di tipo Merge](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md).  
  
-   Specificare le opzioni di schema, ad esempio se i vincoli e i trigger vengono copiati nel Sottoscrittore. Per ulteriori informazioni, vedere [specificare le opzioni dello Schema](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Utilizzare un gestore della logica di business in grado di rispondere a molte condizioni durante la sincronizzazione, ad esempio modifiche dei dati, conflitti ed errori. Per ulteriori informazioni, vedere [eseguire logica di Business durante la sincronizzazione di tipo Merge](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  