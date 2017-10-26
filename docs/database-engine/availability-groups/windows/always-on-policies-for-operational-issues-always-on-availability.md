---
title: "Criteri Always On per problemi operativi con gruppi di disponibilità Always On | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c8256ee37c22d96961c78b5c5a057c0e60b81269
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="always-on-policies-for-operational-issues---always-on-availability"></a>Criteri Always On per problemi operativi con gruppi di disponibilità Always On
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Il modello di integrità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] consente di valutare un set di criteri di gestione basata su criteri (PBM, Policy Based Management) predefiniti. Questi criteri possono essere utilizzati per la visualizzazione dell'integrità di un gruppo di disponibilità, nonché delle repliche e dei database di disponibilità relativi in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'argomento:**  
  
-   [Termini e definizioni](#TermsAndDefinitions)  
  
-   [Criteri predefiniti e problemi](#Always OnPBM)  
  
-   [Dashboard Always On](#Dashboard)  
  
-   [Estensione del modello di integrità Always On](#ExtendHealthModel)  
  
-   [Attività correlate](#RelatedTasks)  
  
-   [Contenuto correlato](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> Termini e definizioni  
 Criteri predefiniti Always On  
 Set di criteri predefiniti che consentono a un amministratore del database di verificare la conformità di un gruppo di disponibilità e delle relative repliche di disponibilità, nonché dei database, con gli stati definiti dai criteri Always On.  
  
 [Gruppi di disponibilità AlwaysOn](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
 Soluzione di disponibilità elevata e ripristino di emergenza che offre un'alternativa di livello enterprise al mirroring del database.  
  
 gruppo di disponibilità  
 Contenitore per un set discreto di database utente, noti come *database di disponibilità*, su cui si verifica il failover.  
  
 replica di disponibilità  
 Creazione di un'istanza di un gruppo di disponibilità ospitata da un'istanza specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e che mantiene una copia locale di ogni database di disponibilità che appartiene al gruppo di disponibilità. Sono disponibili due tipi di replica di disponibilità: una *replica primaria* e da una a quattro *repliche secondarie*. Le istanze del server che ospitano le repliche di disponibilità per un determinato gruppo di disponibilità devono risiedere in nodi diversi di un solo cluster WSFC (Windows Server Failover Clustering).  
  
 database di disponibilità  
 Database che appartiene a un gruppo di disponibilità. Per ogni database di disponibilità, il gruppo di disponibilità gestisce una sola copia di lettura e scrittura (il *database primario*) e da una a quattro copie di sola lettura (*database secondari*).  
  
 Dashboard Always On  
 Un dashboard [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] fornisce una vista immediata dell'integrità di un gruppo di disponibilità. Per altre informazioni, vedere [Dashboard Always On](#Dashboard)di seguito in questo argomento.  
  
##  <a name="Always OnPBM"></a> Criteri predefiniti e problemi  
 Nella tabella seguente sono riepilogati i criteri predefiniti.  
  
|Nome criteri|Problema|Categoria**\***|Facet|  
|-----------------|-----------|--------------------|-----------|  
|Stato del cluster WSFC|[Il servizio cluster WSFC è offline](../../../database-engine/availability-groups/windows/wsfc-cluster-service-is-offline.md).|Critico|Istanza di SQL Server|  
|Stato online del gruppo di disponibilità|[Il gruppo di disponibilità è offline](../../../database-engine/availability-groups/windows/availability-group-is-offline.md).|Critico|gruppo di disponibilità|  
|Conformità del gruppo di disponibilità al failover automatico|[Il gruppo di disponibilità non è pronto per il failover automatico](../../../database-engine/availability-groups/windows/availability-group-is-not-ready-for-automatic-failover.md).|Critico|gruppo di disponibilità|  
|Stato di sincronizzazione dei dati delle repliche di disponibilità|[Alcune repliche di disponibilità non prevedono la sincronizzazione dei dati.](../../../database-engine/availability-groups/windows/some-availability-replicas-are-not-synchronizing-data.md).|Avviso|gruppo di disponibilità|  
|Stato di sincronizzazione dei dati delle repliche sincrone|[Alcune repliche sincrone non sono sincronizzate](../../../database-engine/availability-groups/windows/some-synchronous-replicas-are-not-synchronized.md).|Avviso|gruppo di disponibilità|  
|Stato del ruolo delle repliche di disponibilità|[Alcune repliche di disponibilità non presentano un ruolo integro](../../../database-engine/availability-groups/windows/some-availability-replicas-do-not-have-a-healthy-role.md).|Avviso|gruppo di disponibilità|  
|Stato di connessione delle repliche di disponibilità|[Alcune repliche di disponibilità sono disconnesse](../../../database-engine/availability-groups/windows/some-availability-replicas-are-disconnected.md).|Avviso|gruppo di disponibilità|  
|Stato del ruolo della replica di disponibilità|[La replica di disponibilità non presenta un ruolo integro](../../../database-engine/availability-groups/windows/availability-replica-does-not-have-a-healthy-role.md).|Critico|replica di disponibilità|  
|Stato di connessione della replica di disponibilità|[La replica di disponibilità è disconnessa](../../../database-engine/availability-groups/windows/availability-replica-is-disconnected.md).|Critico|replica di disponibilità|  
|Stato di join della replica di disponibilità|[La replica di disponibilità non è unita in join](../../../database-engine/availability-groups/windows/availability-replica-is-not-joined.md).|Avviso|replica di disponibilità|  
|Stato di sincronizzazione dei dati delle repliche di disponibilità|[Lo stato di sincronizzazione dei dati di alcuni database di disponibilità non è integro](../../../database-engine/availability-groups/windows/data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Avviso|replica di disponibilità|  
|Stato di sospensione del database di disponibilità|[Database di disponibilità sospeso](../../../database-engine/availability-groups/windows/availability-database-is-suspended.md).|Avviso|database di disponibilità|  
|Stato di join del database di disponibilità|[Il database secondario non è unito in join](../../../database-engine/availability-groups/windows/secondary-database-is-not-joined.md).|Avviso|database di disponibilità|  
|Stato di sincronizzazione dei dati del database di disponibilità|[Lo stato di sincronizzazione dei dati del database di disponibilità non è integro](../../../database-engine/availability-groups/windows/data-synchronization-state-of-availability-database-is-not-healthy.md).|Avviso|database di disponibilità|  
  
> [!IMPORTANT]  
>  **\*** Per i criteri Always On, i nomi delle categorie vengono usati come ID. La modifica del nome di una categoria Always On causa l'interruzione della funzionalità di valutazione dell'integrità. Evitare quindi di modificare i nomi di categorie Always On.  
  
##  <a name="Dashboard"></a> Dashboard Always On  
 Il dashboard Always On fornisce una vista immediata dell'integrità di un gruppo di disponibilità. Nel dashboard Always On sono incluse le nuove funzionalità seguenti:  
  
-   Consente di visualizzare facilmente i dettagli relativi a un gruppo di disponibilità specificato, le repliche di disponibilità e i database corrispondenti.  
  
-   Fornisce indicatori visivi degli stati chiave per velocizzare la scelta di decisioni operative da parte degli amministratori del database.  
  
-   Fornisce punti di avvio per scenari per la risoluzione di problemi.  
  
-   Per un determinato problema operativo popola la finestra di dialogo **Risultato di valutazione criteri** con informazioni relative alle violazioni dei criteri di integrità Always On specifiche e con collegamenti a informazioni della Guida sulle possibili correzioni.  
  
-   Fornisce un visualizzatore di eventi estesi relativi all'integrità per mostrare gli eventi precedenti per i problemi specifici di Always On.  
  
-   Se il failover sul gruppo di disponibilità costituisce una possibile risoluzione per un problema, fornisce un punto di avvio per i collegamenti alla[Procedura guidata Failover del gruppo di disponibilità](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md). Questa procedura guida un amministratore del database attraverso il processo di failover manuale.  
  
##  <a name="ExtendHealthModel"></a> Estensione del modello di integrità Always On  
 L'estensione del modello di integrità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] riguarda semplicemente la creazione di propri criteri definiti dall'utente e l'inserimento in determinate categorie in base al tipo di oggetto di cui si sta eseguendo il monitoraggio.  Dopo aver modificato alcune impostazioni, il dashboard Always On valuterà automaticamente i criteri definiti dall'utente, oltre ai criteri predefiniti Always On.  
  
 I criteri definiti dall'utente possono usare qualsiasi facet della gestione basata su criteri disponibile, inclusi quelli usati dai criteri predefiniti Always On. Vedere [Criteri predefiniti e problemi](#Always OnPBM), precedentemente in questo argomento. Il facet Server fornisce le proprietà seguenti per il monitoraggio dell'integrità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] : (**IsHadrEnabled** e **HadrManagerStatus**). Fornisce anche le proprietà dei seguenti criteri per il monitoraggio della configurazione del cluster WSFC: **ClusterQuorumType**e **ClusterQuorumState**.  
  
 Per altre informazioni, vedere [The Always On Health Model Part 2 -- Extending the Health Model](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx) (Seconda parte del modello di integrità Always On riguardante l'estensione del modello di integrità) (blog del team di SQL Server Always On).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Usare i criteri Always On per visualizzare l'integrità di un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Ripristino di emergenza WSFC tramite quorum forzato &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Forzare l'avvio di un cluster WSFC senza un quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Eseguire un failover manuale forzato di un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Risolvere i problemi relativi a una operazione di aggiunta file non riuscita &#40;Gruppi di disponibilità Always On&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   [The Always On Health Model Part 1 -- Health Model Architecture (Prima parte del modello di integrità Always On riguardante l'architettura del modello di integrità)](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx)  
  
-   [The Always On Health Model Part 2 -- Extending the Health Model](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always On-health-model.aspx)  
  
-   [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery (Guida alle soluzioni Always On di Microsoft SQL Server per la disponibilità elevata e il ripristino di emergenza)](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Vedere anche  
 [Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Amministrazione di un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/administration-of-an-availability-group-sql-server.md)   
 [Monitoraggio di Gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  

