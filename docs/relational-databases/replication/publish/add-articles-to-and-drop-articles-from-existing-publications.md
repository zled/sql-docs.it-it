---
title: "Aggiunta ed eliminazione di articoli a e da pubblicazioni esistenti | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "articoli [replica di SQL Server], eliminazione"
  - "eliminazione di articoli"
  - "removing articles"
  - "rimozione di articoli"
  - "aggiunta di articoli"
  - "amministrazione della replica, articoli"
  - "pubblicazioni [replica di SQL Server], aggiunta ed eliminazione di articoli"
  - "articoli [replica di SQL Server], aggiunta"
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Aggiunta ed eliminazione di articoli a e da pubblicazioni esistenti
  Dopo la creazione di una pubblicazione, è possibile aggiungere ed eliminare articoli. Gli articoli possono essere aggiunti in qualsiasi momento, ma le azioni necessarie per eliminarli dipendono dal tipo di replica e dal momento in cui avviene l'eliminazione.  
  
## Aggiunta di articoli  
 L'aggiunta di un articolo comporta l'aggiunta dell'articolo alla pubblicazione, la creazione di un nuovo snapshot per la pubblicazione e la sincronizzazione della sottoscrizione per applicare lo schema e i dati per il nuovo articolo.  
  
> [!NOTE]  
>  Se si aggiunge un articolo a una pubblicazione di tipo merge e il nuovo articolo dipende da un articolo esistente, è necessario specificare un ordine di elaborazione per entrambi gli articoli utilizzando la **@processing_order** parametro [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Si consideri lo scenario seguente: viene pubblicata una tabella, ma non viene pubblicata una funzione a cui fa riferimento la tabella. Se non si pubblica la funzione, la tabella non può essere creata nel Sottoscrittore. Quando si aggiunge la funzione per la pubblicazione: specificare un valore di **1** per il **@processing_order** parametro **sp_addmergearticle**; e specificare un valore di **2** per il **@processing_order** parametro di **sp_changemergearticle**, specificando il nome della tabella per il parametro **@article**. Questo ordine di elaborazione consente di creare la funzione nel Sottoscrittore prima della tabella dipendente. È possibile utilizzare numeri diversi per ogni articolo, purché il numero per la funzione sia inferiore a quello per la tabella.  
  
1.  Aggiungere uno o più articoli tramite uno dei metodi seguenti:  
  
    -   [Aggiunta ed eliminazione di articoli di una pubblicazione & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
2.  Dopo avere aggiunto un articolo a una pubblicazione, è necessario creare un nuovo snapshot per la pubblicazione. Nel caso si tratti di una pubblicazione di tipo merge con filtri con parametri, sarà necessario creare tutte le partizioni. Tramite l'agente di distribuzione o l'agente di merge vengono quindi copiati lo schema e i dati per il nuovo articolo nel Sottoscrittore, senza reinizializzare l'intera pubblicazione.  
  
    -   Per creare un nuovo snapshot, vedere [creare e applicare lo Snapshot iniziale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    -   Per creare un nuovo snapshot per una pubblicazione di tipo merge con filtri con parametri, vedere [creare uno Snapshot per una pubblicazione di tipo Merge con filtri con parametri](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
3.  Dopo la creazione dello snapshot, sincronizzare la sottoscrizione per copiare lo schema e i dati per il nuovo articolo.  
  
    -   Per sincronizzazione di una sottoscrizione push, vedere [Synchronize a Push Subscription](../../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
    -   Per sincronizzazione di una sottoscrizione pull, vedere [Synchronize a Pull Subscription](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
## Eliminazione di articoli  
 Gli articoli possono essere eliminati da una pubblicazione in qualsiasi momento, ma è necessario tenere in considerazione i comportamenti seguenti:  
  
-   L'eliminazione di un articolo da una pubblicazione non comporta la rimozione dell'oggetto dal database di pubblicazione o dell'oggetto corrispondente dal database di sottoscrizione. Utilizzare DROP \< oggetto> rimuovere questi oggetti, se necessario. Quando si elimina un articolo correlato ad altri articoli pubblicati tramite vincoli di chiave esterna, si consiglia di eliminare la tabella nel Sottoscrittore manualmente o tramite l'esecuzione dello script su richiesta: specificare uno script che include il rilascio appropriata \< oggetto> istruzioni. Per ulteriori informazioni, vedere [eseguire gli script durante la sincronizzazione & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Per pubblicazioni di tipo merge con un livello di compatibilità di 90RTM o superiore, gli articoli possono essere eliminati in qualsiasi momento, ma è necessario un nuovo snapshot. Inoltre:  
  
    -   Se un articolo è un articolo padre in una relazione tra record logici o filtri join, è necessario che prima vengano eliminate le relazioni e di conseguenza sarà necessario eseguire una reinizializzazione.  
  
    -   Se un articolo ha l'ultimo filtro con parametri in una pubblicazione, è necessario reinizializzare le sottoscrizioni.  
  
-   Per pubblicazioni di tipo merge con un livello di compatibilità inferiore a 90RTM, gli articoli possono essere eliminati senza particolari considerazioni prima della sincronizzazione iniziale delle sottoscrizioni. Se un articolo viene eliminato dopo la sincronizzazione di una o più sottoscrizioni, è necessario che le sottoscrizioni vengano eliminate, ricreate e sincronizzate.  
  
-   Per le pubblicazioni snapshot o transazionali, gli articoli possono essere eliminati senza particolari considerazioni prima della creazione delle sottoscrizioni. Se un articolo viene eliminato dopo la creazione di una o più sottoscrizioni, è necessario che le sottoscrizioni vengano eliminate, ricreate e sincronizzate. Per ulteriori informazioni sull'eliminazione delle sottoscrizioni, vedere [sottoscrivere pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md) e [sp_dropsubscription & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). **sp_dropsubscription** consente di eliminare un singolo articolo dalla sottoscrizione anziché l'intera sottoscrizione.  
  
1.  L'eliminazione di un articolo da una pubblicazione implica l'eliminazione dell'articolo e la creazione di un nuovo snapshot per la pubblicazione. Se si elimina un articolo, lo snapshot corrente non è più valido ed è perciò necessario creare un nuovo snapshot.  
  
    -   Per eliminare un articolo da una pubblicazione, vedere [aggiungere Drop ed articoli a e da una pubblicazione & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md) o [eliminare un articolo](../../../relational-databases/replication/publish/delete-an-article.md).  
  
2.  Dopo avere eliminato un articolo da una pubblicazione, è necessario creare un nuovo snapshot per la pubblicazione. Nel caso si tratti di una pubblicazione di tipo merge con filtri con parametri, sarà necessario creare tutte le partizioni.  
  
    -   Per creare un nuovo snapshot, vedere [creare e applicare lo Snapshot iniziale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
    -   Per creare un nuovo snapshot per una pubblicazione di tipo merge con filtri con parametri, vedere [creare uno Snapshot per una pubblicazione di tipo Merge con filtri con parametri](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Come evidenziato sopra, in alcuni casi l'eliminazione di un articolo richiede che le sottoscrizioni vengano eliminate, ricreate e quindi sincronizzate. Per ulteriori informazioni, vedere [sottoscrivere pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md) e [sincronizzare dati](../../../relational-databases/replication/synchronize-data.md).  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Reinizializzare le sottoscrizioni](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Modifiche allo schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  