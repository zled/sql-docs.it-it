---
title: Sys.dm hadr_availability_replica_states (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_states
- sys.dm_hadr_availability_replica_states_TSQL
- sys.dm_hadr_availability_replica_states
- dm_hadr_availability_replica_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_replica_states dynamic management view
ms.assetid: d2e678bb-51e8-4a61-b223-5c0b8d08b8b1
caps.latest.revision: "65"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bf08e1c4aa40e78f9a6e3cb345aff501804d5736
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadravailabilityreplicastates-transact-sql"></a>sys.dm_hadr_availability_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni replica locale e una riga per ogni replica remota stesso sempre nel gruppo di disponibilità di una replica locale. Ogni riga contiene informazioni sullo stato di una determinata replica.  
  
> [!IMPORTANT]  
>  Per ottenere informazioni su ogni replica in un determinato gruppo di disponibilità, eseguire una query **hadr_availability_replica_states** nell'istanza del server che ospita la replica primaria. Se si eseguono query su questa DMV in un'istanza del server che ospita una replica secondaria di un gruppo di disponibilità, questa vista restituisce solo informazioni locali per il gruppo di disponibilità.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Identificatore univoco della replica.|  
|**group_id**|**uniqueidentifier**|Identificatore univoco del gruppo di disponibilità.|  
|**is_local**|**bit**|Se la replica è locale, uno di:<br /><br /> 0 = Indica una replica secondaria remota in un gruppo di disponibilità la cui replica primaria è ospitata dall'istanza del server locale. Questo valore si verifica solo sul percorso della replica primaria.<br /><br /> 1 = indica una replica locale. Sulle repliche secondarie, è l'unico valore disponibile per il gruppo di disponibilità a cui appartiene la replica.|  
|**ruolo**|**tinyint**|Corrente [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ruolo di una replica locale o una replica remota connessa, uno di:<br /><br /> 0 = Risoluzione<br /><br /> 1 = Primaria<br /><br /> 2 = Secondaria<br /><br /> Per informazioni sui ruoli di [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], vedere [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
|**ROLE_DESC**|**nvarchar(60)**|Descrizione di **ruolo**, uno di:<br /><br /> RESOLVING<br /><br /> PRIMARY<br /><br /> SECONDARY|  
|**operational_state**|**tinyint**|Stato operativo corrente della replica, uno di:<br /><br /> 0 = Failover in sospeso<br /><br /> 1 = in sospeso<br /><br /> 2 = Online<br /><br /> 3 = non in linea<br /><br /> 4 = operazione non riuscita<br /><br /> 5 = Non completato, nessun quorum<br /><br /> Null = La replica non è locale.<br /><br /> Per ulteriori informazioni, vedere [ruoli e stati operativi](#RolesAndOperationalStates), più avanti in questo argomento.|  
|**OPERATIONAL\_stato\_desc**|**nvarchar(60)**|Descrizione di **operativo\_stato**, uno di:<br /><br /> PENDING_FAILOVER<br /><br /> PENDING<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> FAILED<br /><br /> FAILED_NO_QUORUM<br /><br /> NULL|  
|**ripristino\_integrità**|**tinyint**|Rollup del **database\_stato** colonna del [Sys.dm hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) vista a gestione dinamica. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 0: in corso.  Almeno un database unito in join lo stato di un database diverso da ONLINE (**database\_stato** è non 0).<br /><br /> 1: online. Tutti i database aggiunti a un sono di un database online (**database_state** è 0).<br /><br /> NULL: **is_local** = 0|  
|**recovery_health_desc**|**nvarchar(60)**|Descrizione di **recovery_health**, uno di:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**sincronizzazione\_integrità**|**tinyint**|Riflette un rollup dello stato di sincronizzazione del database (**synchronization_state**) di tutti i database di disponibilità unita in join (noto anche come *repliche*) e la modalità di disponibilità del (replica modalità commit sincrono o asincrono). Il rollup rifletterà lo stato accumulato meno integro dei database nella replica. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 0: non integro.   Almeno un database di cui è stato creato un join si trova nello stato NOT SYNCHRONIZING.<br /><br /> 1: parzialmente integro. Alcune repliche non sono nello stato di sincronizzazione di destinazione: le repliche con commit sincrono devono trovarsi nello stato Sincronizzato, mentre le repliche con commit asincrono devono trovarsi nello stato Sincronizzazione in corso.<br /><br /> 2: integro. Tutte le repliche sono nello stato di sincronizzazione di destinazione: le repliche con commit sincrono si trovano nello stato Sincronizzato, mentre le repliche con commit asincrono si trovano nello stato Sincronizzazione in corso.|  
|**synchronization_health_desc**|**nvarchar(60)**|Descrizione di **synchronization_health**, uno di:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**connected_state**|**tinyint**|Se una replica secondaria è attualmente connessa alla replica primaria. I valori possibili sono indicati con le relative descrizioni.<br /><br /> 0: disconnesso. La risposta di una replica di disponibilità per lo stato DISCONNECTED dipende dal relativo ruolo: sulla replica primaria, se una replica secondaria è disconnessa, i database secondari contrassegnati come NOT SYNCHRONIZED sulla replica primaria, che è in attesa per la replica secondaria riconnettersi; In una replica secondaria, dopo avere rilevato che è disconnessa, la replica secondaria tenta di riconnettersi alla replica primaria.<br /><br /> 1: connesso.<br /><br /> Ogni replica primaria tiene traccia dello stato di connessione per ogni replica secondaria nello stesso gruppo di disponibilità. Le repliche secondarie tengono traccia dello stato di connessione della sola replica primaria.|  
|**connected_state_desc**|**nvarchar(60)**|Descrizione di **connection_state**, uno di:<br /><br /> DISCONNECTED<br /><br /> CONNECTED|  
|**last_connect_error_number**|**int**|Numero dell'ultimo errore di connessione.|  
|**last_connect_error_description**|**nvarchar (1024)**|Testo del **last_connect_error_number** messaggio.|  
|**last_connect_error_timestamp**|**datetime**|Data e ora di timestamp che indica il **last_connect_error_number** errore.|  
  
##  <a name="RolesAndOperationalStates"></a>Ruoli e stati operativi  
 Il ruolo, **ruolo**, riflette lo stato di una replica di disponibilità e lo stato operativo, **operational_state**, specifica se la replica è pronta a elaborare le richieste client per tutti i database della replica di disponibilità. Di seguito è riportato un riepilogo degli stati operativi possibili per ogni ruolo: risoluzione, primario e secondario.  
  
 **RISOLUZIONE:** quando una replica di disponibilità è il ruolo RESOLVING, gli stati operativi possibili sono illustrati nella tabella seguente.  
  
|Stato operativo|Description|  
|-----------------------|-----------------|  
|PENDING_FAILOVER|È in corso l'elaborazione di un comando di failover per il gruppo di disponibilità.|  
|OFFLINE|Tutti i dati di configurazione per la replica di disponibilità sono stati aggiornati sul cluster WSFC e anche nei metadati locali, ma attualmente nel gruppo di disponibilità non è presente alcuna replica primaria.|  
|FAILED|Errore di lettura nel tentativo di recuperare informazioni dal cluster WSFC.|  
|FAILED_NO_QUORUM|Il nodo WSFC locale non dispone di quorum. Si tratta di uno stato derivato.|  
  
 **PRIMARY:** se una replica di disponibilità esegue il ruolo primario, è attualmente la replica primaria. Gli stati operativi possibili sono come illustrato nella tabella seguente.  
  
|Stato operativo|Description|  
|-----------------------|-----------------|  
|PENDING|Si tratta di uno stato temporaneo, tuttavia una replica primaria può rimanere bloccata in questo stato se i thread di lavoro non elaborano le richieste.|  
|ONLINE|La risorsa del gruppo di disponibilità è online e tutti i thread di lavoro del database sono stati prelevati.|  
|FAILED|La replica di disponibilità non è in grado di leggere e/o scrivere dal cluster WSFC.|  
  
 **Database secondario:** se una replica di disponibilità esegue il ruolo secondario, è attualmente una replica secondaria. Gli stati operativi possibili sono come illustrato nella tabella seguente.  
  
|Stato operativo|Description|  
|-----------------------|-----------------|  
|ONLINE|La replica secondaria locale è connessa alla replica primaria.|  
|FAILED|La replica secondaria locale non è in grado di leggere e/o scrivere dal cluster WSFC.|  
|NULL|Su una replica primaria, questo valore viene restituito quando la riga è correlata a una replica secondaria.|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
