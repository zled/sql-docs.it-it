---
title: Usare gli oggetti prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7e5b353725cda984a65cbbbb35878c6d79ae4bb5
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698969"
---
# <a name="use-performance-objects"></a>Utilizzo degli oggetti prestazioni
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent include oggetti e contatori delle prestazioni che consentono di monitorare lo stato del servizio. Tramite gli oggetti prestazione è possibile utilizzare Performance Monitor, uno strumento Windows che consente di identificare le attività eseguite in background dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. È possibile ad esempio identificare il numero dei processi attivi attualmente in esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e individuare quelli bloccati.  
  
Per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installata in un computer sono presenti oggetti prestazione e contatori delle prestazioni del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Agli oggetti prestazione viene assegnato un nome in base all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rappresentata da ciascun oggetto.  
  
Nella tabella seguente viene illustrata la modalità di assegnazione dei nomi per gli oggetti prestazione del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:  
  
|Tipo di istanza|Nome oggetto|  
|-----------------|---------------|  
|Default|**SQLAgent:**_oggetto_:_contatore_|  
|Denominato|**SQLAgent$**<br /> **& #42; nome_istanza& #42; :**_oggetto_:_contatore_|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include gli oggetti prestazione seguenti per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Nome oggetto|Descrizione|  
|---------------|---------------|  
|[SQLAgent:Processi](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Informazioni sulle prestazioni relative a processi avviati, alle percentuali di processi completati e allo stato corrente|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Informazioni sullo stato relative ai passaggi di processo|  
|[SQLAgent:Avvisi](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informazioni sul numero di avvisi e notifiche|  
|[SQLAgent:Statistiche](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Informazioni generali sulle prestazioni|  
  
## <a name="see-also"></a>Vedere anche  
[Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
[Procedura: Avvio di Monitoraggio di sistema (Windows)](https://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
