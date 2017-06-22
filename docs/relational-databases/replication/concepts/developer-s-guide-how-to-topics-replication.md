---
title: 'Guida per gli sviluppatori: Procedure (replica) | Microsoft Docs'
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 288ed137e701d6cfb416d12b6ff2176c59ec0278
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="developer39s-guide-how-to-topics-replication"></a>Guida per gli sviluppatori: Procedure (replica)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questo argomento sono disponibili i collegamenti alle informazioni sull'esecuzione a livello di codice di attività correlate alla replica.  
  
## <a name="securing-a-replication-topology"></a>Protezione di una topologia di replica  
  
-   [Visualizzare e modificare le impostazioni di sicurezza della replica](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
-   [Gestire gli account nell'elenco di accesso alla pubblicazione](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>Configurazione, modifica e disabilitazione della pubblicazione e della distribuzione (replica)  
  
-   [Configurare la pubblicazione e la distribuzione](../../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
-   [Visualizzare e modificare le proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [Disabilitare la pubblicazione e la distribuzione](../../../relational-databases/replication/disable-publishing-and-distribution.md)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>Creazione, modifica ed eliminazione di pubblicazioni e articoli  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Definire un articolo](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [Visualizzare e modificare le proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [Visualizzare e modificare le proprietà degli articoli](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [Eliminare una pubblicazione](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [Eliminare un articolo](../../../relational-databases/replication/publish/delete-an-article.md)  
  
-   [Creare una pubblicazione da un database Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Impostare il periodo di scadenza per le sottoscrizioni](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md)  
  
-   [Specificare le opzioni dello schema](../../../relational-databases/replication/publish/specify-schema-options.md)  
  
-   [Replicare le modifiche dello schema](../../../relational-databases/replication/publish/replicate-schema-changes.md)  
  
-   [Gestire le colonne Identity](../../../relational-databases/replication/publish/manage-identity-columns.md)  
  
-   [Impostare il livello di compatibilità per le pubblicazioni di tipo merge](../../../relational-databases/replication/publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>Opzioni per gli snapshot  
  
-   [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Recapitare uno snapshot tramite FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)  
  
### <a name="filtering-data"></a>Filtro dei dati  
  
-   [Definire e modificare un filtro colonne](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)  
  
-   [Definire e modificare un filtro di riga statico](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)  
  
-   [Definire e modificare un filtro di riga con parametri per un articolo di merge](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Ottimizzare i filtri di riga con parametri](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md)  
  
-   [Definire e modificare un filtro di join tra articoli di merge](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>Opzioni per la replica transazionale  
  
-   [Impostare il metodo di propagazione per le modifiche ai dati negli articoli transazionali](../../../relational-databases/replication/publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>Opzioni per la replica di tipo merge  
  
-   [Definire una relazione tra record logici degli articoli di tabelle di merge](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [Specificare l'ordine di elaborazione degli articoli di tabelle di merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md)  
  
-   [Specificare il tipo solo download per un articolo di tabella di merge](../../../relational-databases/replication/publish/specify-that-a-merge-table-article-is-download-only.md)  
  
-   [Disattivare del rilevamento delle eliminazioni per gli articoli di merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [Specificare il livello di rilevamento e risoluzione dei conflitti per gli articoli di merge](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [Specificare un sistema di risoluzione dei conflitti dell'articolo di merge](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
-   [Specificare la risoluzione interattiva dei conflitti per articoli di merge](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>Creazione, modifica ed eliminazione di sottoscrizioni  
  
-   [Creare una sottoscrizione pull](../../../relational-databases/replication/create-a-pull-subscription.md)  
  
-   [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  
  
-   [Eliminare una sottoscrizione pull](../../../relational-databases/replication/delete-a-pull-subscription.md)  
  
-   [Creare una sottoscrizione push](../../../relational-databases/replication/create-a-push-subscription.md)  
  
-   [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md)  
  
-   [Eliminare una sottoscrizione push](../../../relational-databases/replication/delete-a-push-subscription.md)  
  
-   [Specificare le pianificazioni della sincronizzazione](../../../relational-databases/replication/specify-synchronization-schedules.md)  
  
-   [Creare una sottoscrizione aggiornabile di una pubblicazione transazionale](../../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md)
  
-   [Creare una sottoscrizione per un Sottoscrittore non SQL Server](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronizing-subscriptions"></a>Sincronizzazione delle sottoscrizioni  
  
-   [Creare e applicare lo snapshot iniziale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Creare uno snapshot per una pubblicazione di tipo merge con filtri con parametri](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Inizializzare una sottoscrizione transazionale da un backup &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Inizializzare manualmente una sottoscrizione](../../../relational-databases/replication/initialize-a-subscription-manually.md)  
  
-   [Sincronizzare una sottoscrizione pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Sincronizzare una sottoscrizione push](../../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
-   [Reinizializzare una sottoscrizione](../../../relational-databases/replication/reinitialize-a-subscription.md)  
  
-   [Eseguire script durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Implementare un gestore della logica di business per un articolo di merge](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Eseguire il debug di un gestore della logica di business &#40;programmazione della replica&#41;](../../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)  
  
-   [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [Implementare un sistema di risoluzione dei conflitti personalizzato per un articolo di tipo merge](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>Amministrazione di una topologia di replica  
  
-   [Usare i profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
-   [Convalidare i dati nel sottoscrittore](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
-   [Gestire le partizioni di una pubblicazione di tipo merge con filtri con parametri](../../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/bulk-load-data-into-tables-in-a-merge-publication.md)  
  
-   [Eseguire la pulizia dei metadati di merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/clean-up-merge-metadata-replication-transact-sql-programming.md)  
  
-   [Eseguire un aggiornamento fittizio per un articolo di merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)  
  
-   [Visualizzare comandi replicati e altre informazioni nel database di distribuzione &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Abilitare backup coordinati per la replica transazionale &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md)  
  
-   [Amministrare una topologia peer-to-peer &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [Mettere una topologia di replica in stato di inattività &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)  
  
-   [Configurare il processo del set di transazioni per un server di pubblicazione Oracle &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  
  
-   [Aggiornare gli script di replica &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>Monitoraggio di una topologia di replica  
  
-   [Consentire a utenti non amministratori di usare Monitoraggio replica](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
  
-   [Monitorare la replica a livello di programmazione](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
-   [Visualizzare comandi replicati e altre informazioni nel database di distribuzione &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Visualizzare le informazioni sui conflitti per le pubblicazioni di tipo merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/view-conflict-information-for-merge-publications.md)  
  
-   [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
