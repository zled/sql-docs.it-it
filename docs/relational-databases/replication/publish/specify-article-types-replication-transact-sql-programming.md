---
title: "Impostazione dei tipi di articolo (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "pubblicazione [replica di SQL Server], esecuzione di stored procedure"
  - "articoli [replica di SQL Server], opzioni di replica transazionale"
  - "articoli [replica di SQL Server], opzioni di replica di tipo merge"
  - "stored procedure [replica di SQL Server], pubblicazione"
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Impostazione dei tipi di articolo (programmazione Transact-SQL della replica)
  I tipi di articolo predefiniti per la replica sono gli articoli di tabella, ma è possibile pubblicare altri oggetti di database come articoli, tra cui viste, stored procedure, funzioni definite dall'utente ed esecuzione di stored procedure. È possibile utilizzare le stored procedure di replica per specificare a livello di programmazione un tipo di articolo mentre viene definito. Le stored procedure utilizzate dipendono dal tipo di replica e dal tipo di articolo.  
  
> [!NOTE]  
>  La designazione di solo schema durante la definizione di articoli di tabelle, viste e stored procedure indica che verrà replicata solo la definizione dell'oggetto.  
  
### Per pubblicare un articolo di tabella in una pubblicazione transazionale o snapshot  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare uno dei valori seguenti per **@type** per definire il tipo di articolo:  
  
    -   **logbased** -un articolo di tabella basato su log, ovvero l'impostazione predefinita per la replica transazionale e snapshot. Con la replica vengono automaticamente generate la stored procedure utilizzata per il filtro orizzontale e la vista che definisce un articolo con filtro verticale.  
  
    -   **logbased manualfilter** -un articolo basato su log in cui la stored procedure utilizzata per il filtro orizzontale viene manualmente creata e definita dall'utente e specificata per **@filter**. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** -un articolo basato su log, filtrato in verticale in cui la vista che definisce l'articolo con filtro verticale viene creata e definita dall'utente e specificata per **@sync_object**. Per ulteriori informazioni, vedere [definire e modificare un filtro di riga statico](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) e [definire e modificare un filtro di colonna](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** -un basato su log, orizzontalmente e verticalmente filtrati articolo in cui sia la stored procedure utilizzata per il filtro orizzontale e la vista che definisce l'articolo con filtro verticale vengono creati e definiti dall'utente e specificata per **@filter** e **@sync_object**, rispettivamente. Per ulteriori informazioni, vedere [definire e modificare un filtro di riga statico](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) e [definire e modificare un filtro di colonna](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     In questo modo viene definito un nuovo articolo per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Per **logbased manualboth** e **logbased manualfilter** articoli, eseguire [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) per generare la stored procedure di filtro per un articolo con filtro orizzontale. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Per **logbased manualboth**, **logbased manualview**, e **logbased manualfilter** articoli, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) per generare la vista che definisce l'articolo con filtro verticale. Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Per pubblicare un articolo di vista o di vista indicizzata in una pubblicazione transazionale o snapshot  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare uno dei valori seguenti per **@type** per definire il tipo di articolo:  
  
    -   **indicizzare view logbased** -un articolo di vista indicizzata basato su log. Con la replica vengono automaticamente generate la stored procedure utilizzata per il filtro orizzontale e la vista che definisce un articolo con filtro verticale.  
  
    -   **schema della vista solo** -un articolo solo schema di vista. È necessario replicare anche la tabella di base.  
  
    -   **solo schema di vista indicizzata** -un articolo solo schema vista indicizzata. È necessario replicare anche la tabella di base.  
  
    -   **indicizzare view logbased manualfilter** -un articolo di vista indicizzata basato su log in cui la stored procedure utilizzata per il filtro orizzontale viene manualmente creata e definita dall'utente e specificata per **@filter**. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
    -   **indicizzare view logbased manualview** -un articolo di vista indicizzata basato su log in cui la vista che definisce un articolo con filtro verticale viene creata e definita dall'utente e specificata per **@sync_object**. Per ulteriori informazioni, vedere [definire e modificare un filtro di riga statico](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) e [definire e modificare un filtro di colonna](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
    -   **indicizzare view logbased manualboth** -un articolo di vista indicizzata basato su log in cui sia la stored procedure utilizzata per il filtro orizzontale e la vista che definisce un articolo con filtro verticale sono creato e definito dall'utente e specificata per **@filter** e **@sync_object**, rispettivamente. Per ulteriori informazioni, vedere [definire e modificare un filtro di riga statico](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) e [definire e modificare un filtro di colonna](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
     In questo modo viene definito un nuovo articolo per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Per **logbased manualboth** e **logbased manualfilter** articoli, eseguire [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) per generare la stored procedure di filtro per un articolo con filtro orizzontale. Per altre informazioni, vedere [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Per **logbased manualboth**, **logbased manualview**, e **logbased manualfilter** articoli, eseguire [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) per generare la vista che definisce l'articolo con filtro verticale. Per altre informazioni, vedere [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
### Per pubblicare un articolo di stored procedure, esecuzione di stored procedure o funzione definita dall'utente in una pubblicazione transazionale o snapshot  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare uno dei valori seguenti per **@type** per definire il tipo di articolo:  
  
    -   **proc schema solo** -un articolo solo schema di stored procedure.  
  
    -   **proc exec** -replica l'esecuzione della stored procedure in tutti i sottoscrittori dell'articolo. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **serializable proc exec** -replica l'esecuzione della stored procedure solo se viene eseguita all'interno del contesto di una transazione serializzabile. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **Func schema solo** -un articolo solo schema funzione definita dall'utente.  
  
     In questo modo viene definito un nuovo articolo per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Per pubblicare un articolo di tabella o vista in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare uno dei valori seguenti per **@type** per definire il tipo di articolo:  
  
    -   **tabella** -un articolo di tabella.  
  
    -   **solo schema di vista indicizzata** -un articolo solo schema vista indicizzata.  
  
    -   **schema della vista solo** -un articolo solo schema di vista.  
  
     In questo modo viene definito un nuovo articolo per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
### Per pubblicare un articolo di stored procedure o funzione definita dall'utente in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare uno dei valori seguenti per **@type** per definire il tipo di articolo:  
  
    -   **Func schema solo** -un articolo solo schema funzione definita dall'utente.  
  
    -   **proc schema solo** -un articolo solo schema di stored procedure.  
  
     In questo modo viene definito un nuovo articolo per la pubblicazione. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Vedere anche  
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  