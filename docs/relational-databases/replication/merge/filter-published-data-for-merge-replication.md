---
title: "Filtro dei dati pubblicati per la replica di tipo merge | Microsoft Docs"
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
  - "replica di tipo merge [replica di SQL Server], filtro di dati pubblicati"
  - "replica [SQL Server], filtro di dati pubblicati"
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Filtro dei dati pubblicati per la replica di tipo merge
  Oltre ai filtri di riga e di colonna statici che è possibile definire con altri tipi di replica, la replica di tipo merge offre filtri di riga con parametri e filtri join. Per ulteriori informazioni sui filtri di riga statici e di colonna, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 La replica di tipo merge viene utilizzata in molte applicazioni che supportano gli utenti mobili. Tali applicazioni hanno in genere un gran numero di sottoscrizioni ognuna delle quali riceve un set di dati univoco. I filtri con parametri combinati con i filtri join consentono a un amministratore di impostare una pubblicazione (o un numero limitato di pubblicazioni) e di fornire set di dati diversi agli utenti, riducendo l'overhead di gestione introdotto con la creazione di più pubblicazioni.  
  
-   I filtri con parametri consentono l'invio di partizioni diverse di dati a Sottoscrittori diversi senza richiedere la creazione di più pubblicazioni. Ad esempio, è possibile filtrare una tabella in modo che i dati di uno specifico rappresentante vengano replicati solo a tale rappresentante. I filtri con parametri hanno una varietà di opzioni che consentono di personalizzare il filtraggio per ottimizzare le prestazioni e adattarsi ai dati e ai requisiti dell'applicazione. Per altre informazioni, vedere [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   I filtri join sono utilizzati insieme ai filtri con parametri per estendere il filtraggio alle tabelle correlate e possono essere utilizzati anche insieme ai filtri statici. Ad esempio, il rappresentante in genere dispone di dati in altre tabelle, ad esempio le tabelle relative a clienti e ordini. Questi dati possono essere filtrati in modo che il rappresentante riceva solo i dati relativi ai clienti e ai rispettivi ordini. Per ulteriori informazioni, vedere [filtri Join](../../../relational-databases/replication/merge/join-filters.md).  
  
 Non deve includere un filtro di **rowguidcol** utilizzata dalla replica per identificare le righe. Per impostazione predefinita la colonna aggiunta in fase di configurare la replica di tipo merge ed è denominato **rowguid**.  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  