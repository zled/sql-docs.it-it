---
title: "Panoramica dei cmdlet di PowerShell per Gruppi di disponibilit&#224; Always On (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gruppi di disponibilità [SQL Server], cmdlet di PowerShell"
  - "Gruppi di disponibilità [SQL Server], informazioni"
  - "PowerShell [SQL Server], cmdlet"
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# Panoramica dei cmdlet di PowerShell per Gruppi di disponibilit&#224; Always On (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell è una shell della riga di comando basata su attività e un linguaggio di scripting progettato appositamente per l'amministrazione del sistema. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fornisce un set di cmdlet di PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] per distribuire, gestire e monitorare gruppi di disponibilità, repliche di disponibilità e database di disponibilità.  
  
> [!NOTE]  
>  Con l'inizio corretto di un'azione è possibile che venga completato un cmdlet di PowerShell. Ciò non implica che l'azione desiderata, ad esempio il failover di un gruppo di disponibilità, sia stata completata. Quando si genera lo script di una sequenza di azioni, può essere necessario controllare lo stato delle azioni e attenderne il completamento.  
  
 In questo argomento vengono presentati i cmdlet per i seguenti set di attività:  
  
-   [Configurazione di un'istanza del server per Gruppi di disponibilità Always On](#ConfiguringServerInstance)  
  
-   [Backup e ripristino dei database e dei log delle transazioni](#BnRcmdlets)  
  
-   [Creazione e gestione di un gruppo di disponibilità](#DeployManageAGs)  
  
-   [Creazione e gestione di un listener del gruppo di disponibilità](#AGlisteners)  
  
-   [Creazione e gestione di una replica di disponibilità](#DeployManageARs)  
  
-   [Aggiunta e gestione di un database di disponibilità](#DeployManageDbs)  
  
-   [Monitoraggio dello stato di integrità di un gruppo di disponibilità](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Per un elenco degli argomenti nella documentazione online di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] che illustrano come usare i cmdlet per eseguire attività [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere la sezione "Attività correlate" di [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="ConfiguringServerInstance"></a> Configurazione di un'istanza del server per Gruppi di disponibilità Always On  
  
|Cmdlet|Descrizione|Supportati in|  
|-------------|-----------------|------------------|  
|**Disable-SqlAlways On**|Disabilita la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] su un'istanza del server.|L'istanza del server è specificata dal parametro **Path**, **InputObject**o **Name** . (L'edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve supportare [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]).|  
|**Enable-SqlAlways On**|Abilita [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] su un'istanza di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] che supporta la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Per informazioni sul supporto per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md).|Qualsiasi edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].|  
|**New-SqlHadrEndPoint**|Crea un nuovo endpoint del mirroring del database in un'istanza del server. Questo endpoint è richiesto per lo spostamento di dati tra il database primario e quelli secondari.|Qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|**Set-SqlHadrEndpoint**|Modifica le proprietà di un endpoint del mirroring del database esistente, ad esempio il nome, lo stato o le proprietà di autenticazione.|Istanza del server che supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] e in cui non è presente un endpoint del mirroring del database|  
  
##  <a name="BnRcmdlets"></a> Backup e ripristino dei database e dei log delle transazioni  
  
|Cmdlet|Descrizione|Supportati in|  
|-------------|-----------------|------------------|  
|**Backup-SqlDatabase**|Crea un backup dei dati o del log.|Qualsiasi database online (per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], un database nell'istanza del server che ospita la replica primaria)|  
|**Restore-SqlDatabase**|Ripristina un backup.|Qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], un'istanza del server che ospita una replica secondaria)<br /><br /> **\*\* Importante \*\*** Quando si prepara un database secondario, è necessario usare il parametro **-NoRecovery** in ogni comando **Restore-SqlDatabase**.|  
  
 Per informazioni sull'uso di questi cmdlet per preparare un database secondario, vedere [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="DeployManageAGs"></a> Creazione e gestione di un gruppo di disponibilità  
  
|Cmdlet|Descrizione|Supportati in|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityGroup**|Crea un nuovo gruppo di disponibilità.|Istanza del server per ospitare la replica primaria|  
|**Remove-SqlAvailabilityGroup**|Elimina un gruppo di disponibilità.|Istanza del server abilitata per HADR|  
|**Set-SqlAvailabilityGroup**|Imposta le proprietà di un gruppo di disponibilità; porta un gruppo di disponibilità online/offline|Istanza del server che ospita la replica primaria|  
|**Switch-SqlAvailabilityGroup**|Inizia una delle seguenti modalità di failover:<br /><br /> Failover forzato di un gruppo di disponibilità (con possibile perdita di dati).<br /><br /> Failover manuale di un gruppo di disponibilità.|Istanza del server che ospita la replica secondaria di destinazione|  
  
##  <a name="AGlisteners"></a> Creazione e gestione di un listener del gruppo di disponibilità  
  
|Cmdlet|Descrizione|Supportati in|  
|------------|-----------------|------------------|  
|**New-SqlAvailabilityGroupListener**|Crea un nuovo listener del gruppo di disponibilità e lo collega a un gruppo di disponibilità esistente.|Istanza del server che ospita la replica primaria|  
|**Set-SqlAvailabilityGroupListener**|Modifica l'impostazione della porta su un listener del gruppo di disponibilità esistente.|Istanza del server che ospita la replica primaria|  
|**Add-SqlAvailabilityGroupListenerStaticIp**|Aggiunge un indirizzo IP statico a una configurazione del listener del gruppo di disponibilità esistente. L'indirizzo IP può essere un indirizzo IPv4 con subnet o un indirizzo IPv6.|Istanza del server che ospita la replica primaria|  
  
##  <a name="DeployManageARs"></a> Creazione e gestione di una replica di disponibilità  
  
|Cmdlet|Descrizione|Supportati in|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Crea una nuova replica di disponibilità È possibile usare il parametro **-AsTemplate** per creare un oggetto della replica di disponibilità in memoria per ogni nuova replica di disponibilità.|Istanza del server che ospita la replica primaria|  
|**Join-SqlAvailabilityGroup**|Viene creato un join della replica secondaria al gruppo di disponibilità.|Istanza del server che ospita la replica secondaria|  
|**Remove-SqlAvailabilityReplica**|Elimina una replica di disponibilità.|Istanza del server che ospita la replica primaria|  
|**Set-SqlAvailabilityReplica**|Imposta le proprietà di una replica di disponibilità.|Istanza del server che ospita la replica primaria|  
  
##  <a name="DeployManageDbs"></a> Aggiunta e gestione di un database di disponibilità  
  
|Cmdlet|Descrizione|Supportati in|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Nella replica primaria viene aggiunto un database a un gruppo di disponibilità.<br /><br /> In una replica secondaria viene creato un join di un database secondario a un gruppo di disponibilità.|Qualsiasi istanza del server che ospita una replica di disponibilità (il comportamento è diverso per le repliche primarie e per quelle secondarie)|  
|**Remove-SqlAvailabilityDatabase**|Nella replica primaria il database viene rimosso dal gruppo di disponibilità.<br /><br /> In una replica secondaria il database secondario locale viene rimosso dalla replica secondaria locale.|Qualsiasi istanza del server che ospita una replica di disponibilità (il comportamento è diverso per le repliche primarie e per quelle secondarie)|  
|**Resume-SqlAvailabilityDatabase**|Riprende lo spostamento dati per un database di disponibilità sospeso.|L'istanza del server in cui si trova il database è stata sospesa.|  
|**Suspend-SqlAvailabilityDatabase**|Sospende lo spostamento dati per un database di disponibilità.|Qualsiasi istanza del server che ospita una replica di disponibilità.|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoraggio dello stato dei gruppi disponibilità  
 Con i cmdlet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] seguenti è possibile monitorare lo stato di un gruppo di disponibilità, nonché delle repliche e dei database relativi.  
  
> [!IMPORTANT]  
>  È necessario disporre delle autorizzazioni CONNECT, VIEW SERVER STATE e VIEW ANY DEFINITION per eseguire questi cmdlet.  
  
|Cmdlet|Descrizione|Supportati in|  
|------------|-----------------|------------------|  
|**Test-SqlAvailabilityGroup**|Valuta l'integrità di un gruppo di disponibilità valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
|**Test-SqlAvailabilityReplica**|Valuta l'integrità delle repliche di disponibilità valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
|**Test-SqlDatabaseReplicaState**|Valuta l'integrità di un database di disponibilità su tutte le repliche di disponibilità aggiunte valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
  
 * Per visualizzare informazioni su tutte le repliche di disponibilità in un gruppo di disponibilità, usare l'istanza del server che ospita la replica primaria.  
  
 Per altre informazioni, vedere [Usare i criteri Always On per visualizzare l'integrità di un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## Vedere anche  
 [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Visualizzazione della Guida di SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
  