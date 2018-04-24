---
title: Usare gli oggetti prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d5033120057e83f6fd155466a35188be04068ef6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-performance-objects"></a>Utilizzo degli oggetti prestazioni
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent include oggetti e contatori delle prestazioni che consentono di monitorare lo stato del servizio. Tramite gli oggetti prestazione è possibile utilizzare Performance Monitor, uno strumento Windows che consente di identificare le attività eseguite in background dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. È possibile ad esempio identificare il numero dei processi attivi attualmente in esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e individuare quelli bloccati.  
  
Per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] installata in un computer sono presenti oggetti prestazione e contatori delle prestazioni del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Agli oggetti prestazione viene assegnato un nome in base all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rappresentata da ciascun oggetto.  
  
Nella tabella seguente viene illustrata la modalità di assegnazione dei nomi per gli oggetti prestazione del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent:  
  
|Tipo di istanza|Nome oggetto|  
|-----------------|---------------|  
|Default|**SQLAgent:***oggetto*:*contatore*|  
|Denominato|**SQLAgent$**<br /> **&#42;nome_istanza&#42; :***oggetto*:*contatore*|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] include gli oggetti prestazione seguenti per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
|Nome oggetto|Description|  
|---------------|---------------|  
|[SQLAgent:Processi](http://msdn.microsoft.com/en-us/225b5e2d-4a78-4178-b2b6-b419df83c4aa)|Informazioni sulle prestazioni relative a processi avviati, alle percentuali di processi completati e allo stato corrente|  
|[SQLAgent:JobSteps](http://msdn.microsoft.com/en-us/44f9983c-1753-4fe0-8475-973aa2460b3a)|Informazioni sullo stato relative ai passaggi di processo|  
|[SQLAgent:Avvisi](http://msdn.microsoft.com/en-us/e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a)|Informazioni sul numero di avvisi e notifiche|  
|[SQLAgent:Statistiche](http://msdn.microsoft.com/en-us/ebe92bfa-0721-48aa-9ba6-e7904ad265a1)|Informazioni generali sulle prestazioni|  
  
## <a name="see-also"></a>Vedere anche  
[Monitoraggio e ottimizzazione delle prestazioni](http://msdn.microsoft.com/en-us/87f23f03-0f19-4b2e-bfae-efa378f7a0d4)  
[Procedura: Avvio di Monitoraggio di sistema (Windows)](http://msdn.microsoft.com/en-us/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
