---
title: Sys. availability_groups_cluster (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_cluster
- availability_groups_cluster
- availability_groups_cluster_TSQL
- sys.availability_groups_cluster_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: d0f4683f-cdf0-4227-8b68-720ffe58f158
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c06aa309da80d737bc422dd4f0726ed903cc24e1
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656512"
---
# <a name="sysavailabilitygroupscluster-transact-sql"></a>sys.availability_groups_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni gruppo di disponibilità Always On nel Windows Server Failover Clustering (WSFC). Ogni riga contiene i metadati dei gruppi di disponibilità del cluster WSFC.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificatore univoco (GUID) del gruppo di disponibilità.|  
|**name**|**sysname**|Nome del gruppo di disponibilità. Si tratta di un nome specificato dall'utente che deve essere univoco all'interno del cluster di failover di Windows Server (WSFC).|  
|**resource_id**|**nvarchar(40)**|ID della risorsa del cluster WSFC.|  
|**resource_group_id**|**nvarchar(40)**|ID del gruppo di risorse del cluster WSFC del gruppo di disponibilità.|  
|**failure_condition_level**|**int**|Livello della condizione di errore definito dall'utente al di sotto del quale deve essere attivato un failover automatico. Sono disponibili i valori interi seguenti:<br /><br /> 1: Specifica che deve essere avviato un failover automatico quando si verifica una delle operazioni seguenti: <br />-La [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio è inattivo.<br />-Il lease del gruppo di disponibilità per la connessione al cluster di failover WSFC scade poiché non viene ricevuto alcun Acknowledgement dall'istanza del server. Per altre informazioni, vedere [Funzionamento: timeout lease di SQL Server Always On](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).<br /><br /> 2: Specifica che deve essere avviato un failover automatico quando si verifica una delle operazioni seguenti:  <br />-L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non si connette al cluster e l'utente specificato dal **health_check_timeout** viene superata la soglia del gruppo di disponibilità. <br />-La replica di disponibilità è in stato di errore. <br />3: Specifica che deve essere avviato un failover automatico su critico [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errori interni, ad esempio SpinLock orfani, violazioni gravi l'accesso in scrittura o dumping eccessivo. Si tratta del valore predefinito. <br />4: Specifica che deve essere avviato un failover automatico in moderato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli errori interni, ad esempio una condizione di memoria insufficiente persistente nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pool di risorse interno.<br />5: Specifica che deve essere avviato un failover automatico in qualsiasi condizione di errore qualificata, tra cui:<br />-Esaurimento dei thread di lavoro del motore SQL. <br />-Rilevamento di un deadlock irrisolvibile.<br /><br /> I livelli delle condizioni di errore (1-5) vanno dal livello 1, meno restrittivo, al livello 5, più restrittivo. Un livello della condizione specifico include tutti i livelli meno restrittivi. Il livello della condizione più restrittivo, ovvero il livello 5, include pertanto i quattro livelli della condizione meno restrittivi (1-4), il livello 4 include i livelli 1-3 e così via.<br /><br /> Per modificare questo valore, usare l'opzione FAILURE_CONDITION_LEVEL del [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.|  
|**health_check_timeout**|**int**|Tempo di attesa (in millisecondi) per il [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) stored procedure per restituire le informazioni sull'integrità del server, prima che si presuppone che l'istanza del server sia lenta o bloccata di sistema. Il valore predefinito è 30000 millisecondi (30 secondi).<br /><br /> Per modificare questo valore, usare l'opzione HEALTH_CHECK_TIMEOUT del [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.|  
|**automated_backup_preference**|**tinyint**|Percorso preferito per l'esecuzione di backup nei database di disponibilità del gruppo di disponibilità. I valori validi sono:<br /><br /> 0: primario. I backup devono essere sempre eseguiti sulla replica primaria.<br />1: solo secondario. È preferibile eseguire i backup in una replica secondaria.<br />2: preferisco secondario. È preferibile eseguire i backup in una replica secondaria, ma nel caso in cui non sia disponibile alcuna replica secondaria per le operazioni di backup, è possibile eseguire i backup nella replica primaria. Questo è il comportamento predefinito.<br />3: tutte le repliche. Nessuna preferenza sull'utilizzo della replica primaria o di una replica secondaria per l'esecuzione dei backup.<br /><br /> Per altre informazioni, vedere [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**automated_backup_preference_desc**|**nvarchar(60)**|Descrizione della **automated_backup_preference**, uno di:<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> Nessuno|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW ANY DEFINITION nell'istanza del server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
