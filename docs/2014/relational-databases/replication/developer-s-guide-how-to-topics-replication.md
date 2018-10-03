---
title: 'Guida per gli sviluppatori: Procedure (replica) | Microsoft Docs'
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- replication
ms.topic: reference
ms.assetid: c6c15ae6-da52-4638-93d3-61c7242e8a0b
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2a35601af505e440eb986c7576c0c1c258421476
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177261"
---
# <a name="developer39s-guide-how-to-topics-replication"></a>Guida per gli sviluppatori: Procedure (replica)
  In questo argomento sono disponibili i collegamenti alle informazioni sull'esecuzione a livello di codice di attività correlate alla replica.  
  
## <a name="securing-a-replication-topology"></a>Protezione di una topologia di replica  
  
-   [Visualizzare e modificare le impostazioni di sicurezza della replica](security/view-and-modify-replication-security-settings.md)  
  
-   [Gestire gli account nell'elenco di accesso alla pubblicazione](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="configuring-modifying-and-disabling-publishing-and-distribution-replication"></a>Configurazione, modifica e disabilitazione della pubblicazione e della distribuzione (replica)  
  
-   [Configurare la pubblicazione e la distribuzione](configure-publishing-and-distribution.md)  
  
-   [Visualizzare e modificare le proprietà della pubblicazione](publish/view-and-modify-publication-properties.md)  
  
-   [Disabilitare la pubblicazione e la distribuzione](disable-publishing-and-distribution.md)  
  
## <a name="creating-modifying-and-deleting-publications-and-articles"></a>Creazione, modifica ed eliminazione di pubblicazioni e articoli  
  
-   [Create a Publication](publish/create-a-publication.md)  
  
-   [Define an Article](publish/define-an-article.md)  
  
-   [Visualizzare e modificare le proprietà della pubblicazione](publish/view-and-modify-publication-properties.md)  
  
-   [Visualizzare e modificare le proprietà degli articoli](publish/view-and-modify-article-properties.md)  
  
-   [Eliminare una pubblicazione](publish/delete-a-publication.md)  
  
-   [Eliminare un articolo](publish/delete-an-article.md)  
  
-   [Creare una pubblicazione da un database Oracle](publish/create-a-publication-from-an-oracle-database.md)  
  
-   [Impostare il periodo di scadenza per le sottoscrizioni](publish/set-the-expiration-period-for-subscriptions.md)  
  
-   [Specificare le opzioni dello schema](publish/specify-schema-options.md)  
  
-   [Replicare le modifiche dello schema](publish/replicate-schema-changes.md)  
  
-   [Gestire le colonne Identity](publish/manage-identity-columns.md)  
  
-   [Impostare il livello di compatibilità per le pubblicazioni di tipo merge](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>Opzioni per gli snapshot  
  
-   [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Recapitare uno snapshot tramite FTP](publish/deliver-a-snapshot-through-ftp.md)  
  
### <a name="filtering-data"></a>Filtro dei dati  
  
-   [Definire e modificare un filtro colonne](publish/define-and-modify-a-column-filter.md)  
  
-   [Definire e modificare un filtro di riga statico](publish/define-and-modify-a-static-row-filter.md)  
  
-   [Definire e modificare un filtro di riga con parametri per un articolo di merge](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Ottimizzare i filtri di riga con parametri](merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [Definire e modificare un filtro di join tra articoli di merge](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>Opzioni per la replica transazionale  
  
-   [Impostare il metodo di propagazione per le modifiche ai dati negli articoli transazionali](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>Opzioni per la replica di tipo merge  
  
-   [Definire una relazione tra record logici degli articoli di tabelle di merge](publish/define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [Specificare l'ordine di elaborazione degli articoli di tabelle di merge &#40;programmazione Transact-SQL della replica&#41;](publish/specify-the-processing-order-of-merge-table-articles.md)  
  
-   [Specificare il tipo solo download per un articolo di tabella di merge](publish/specify-that-a-merge-table-article-is-download-only.md)  
  
-   [Disattivare del rilevamento delle eliminazioni per gli articoli di merge &#40;programmazione Transact-SQL della replica&#41;](publish/specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [Specificare il livello di rilevamento e risoluzione dei conflitti per gli articoli di merge](publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [Specificare un sistema di risoluzione dei conflitti dell'articolo di merge](publish/specify-a-merge-article-resolver.md)  
  
-   [Specificare la risoluzione interattiva dei conflitti per articoli di merge](publish/specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="creating-modifying-and-deleting-subscriptions"></a>Creazione, modifica ed eliminazione di sottoscrizioni  
  
-   [Creare una sottoscrizione pull](create-a-pull-subscription.md)  
  
-   [Visualizzare e modificare le proprietà delle sottoscrizioni pull](view-and-modify-pull-subscription-properties.md)  
  
-   [Eliminare una sottoscrizione pull](delete-a-pull-subscription.md)  
  
-   [Creare una sottoscrizione push](create-a-push-subscription.md)  
  
-   [Visualizzare e modificare le proprietà delle sottoscrizioni push](view-and-modify-push-subscription-properties.md)  
  
-   [Eliminare una sottoscrizione push](delete-a-push-subscription.md)  
  
-   [Specificare le pianificazioni della sincronizzazione](specify-synchronization-schedules.md)  
  
-   [Creare una sottoscrizione aggiornabile di una pubblicazione transazionale](create-updatable-subscription-transactional-publication-transact-sql.md)  
  
-   [Creare una sottoscrizione per un Sottoscrittore non SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronizing-subscriptions"></a>Sincronizzazione delle sottoscrizioni  
  
-   [Creazione e applicazione dello snapshot iniziale](create-and-apply-the-initial-snapshot.md)  
  
-   [Creare uno snapshot per una pubblicazione di tipo merge con filtri con parametri](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Inizializzare una sottoscrizione transazionale da un backup &#40;programmazione Transact-SQL della replica&#41;](initialize-a-transactional-subscription-from-a-backup.md)  
  
-   [Inizializzare manualmente una sottoscrizione](initialize-a-subscription-manually.md)  
  
-   [Sincronizzazione di una sottoscrizione pull](synchronize-a-pull-subscription.md)  
  
-   [Sincronizzazione di una sottoscrizione push](synchronize-a-push-subscription.md)  
  
-   [Reinizializzare una sottoscrizione](reinitialize-a-subscription.md)  
  
-   [Eseguire script durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)  
  
-   [Implementare un gestore della logica di business per un articolo di merge](implement-a-business-logic-handler-for-a-merge-article.md)  
  
-   [Eseguire il debug di un gestore della logica di business &#40;programmazione della replica&#41;](debug-a-business-logic-handler-replication-programming.md)  
  
-   [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](control-behavior-of-triggers-and-constraints-in-synchronization.md)  
  
-   [Implementare un sistema di risoluzione dei conflitti personalizzato per un articolo di tipo merge](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administering-a-replication-topology"></a>Amministrazione di una topologia di replica  
  
-   [Usare i profili agenti di replica](agents/replication-agent-profiles.md)  
  
-   [Convalidare i dati nel sottoscrittore](validate-data-at-the-subscriber.md)  
  
-   [Gestire le partizioni di una pubblicazione di tipo merge con filtri con parametri](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
-   [Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo merge &#40;programmazione Transact-SQL della replica&#41;](bulk-load-data-into-tables-in-a-merge-publication.md)  
  
-   [Eseguire la pulizia dei metadati di merge &#40;programmazione Transact-SQL della replica&#41;](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)  
  
-   [Eseguire un aggiornamento fittizio per un articolo di merge &#40;programmazione Transact-SQL della replica&#41;](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)  
  
-   [Visualizzare comandi replicati e altre informazioni nel database di distribuzione &#40;programmazione Transact-SQL della replica&#41;](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Abilitare backup coordinati per la replica transazionale &#40;programmazione Transact-SQL della replica&#41;](administration/enable-coordinated-backups-for-transactional-replication.md)  
  
-   [Amministrare una topologia peer-to-peer &#40;programmazione Transact-SQL della replica&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)  
  
-   [Mettere una topologia di replica in stato di inattività &#40;programmazione Transact-SQL della replica&#41;](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)  
  
-   [Configurare il processo del set di transazioni per un server di pubblicazione Oracle &#40;programmazione Transact-SQL della replica&#41;](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  
  
-   [Aggiornare gli script di replica &#40;programmazione Transact-SQL della replica&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitoring-a-replication-topology"></a>Monitoraggio di una topologia di replica  
  
-   [Consentire a utenti non amministratori di usare Monitoraggio replica](monitor/allow-non-administrators-to-use-replication-monitor.md)  
  
-   [Monitorare la replica a livello di programmazione](monitor/monitoring-replication-overview.md)  
  
-   [Visualizzare comandi replicati e altre informazioni nel database di distribuzione &#40;programmazione Transact-SQL della replica&#41;](monitor/view-replicated-commands-and-information-in-distribution-database.md)  
  
-   [Visualizzare le informazioni sui conflitti per le pubblicazioni di tipo merge &#40;programmazione Transact-SQL della replica&#41;](view-conflict-information-for-merge-publications.md)  
  
-   [Misurare la latenza e convalidare le connessioni per la replica transazionale](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
