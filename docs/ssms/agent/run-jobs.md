---
title: Eseguire processi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
- SQL Server Agent jobs, manually running
- multiserver job processing [SQL Server]
- jobs [SQL Server Agent], manually running
- manual job processing [SQL Server]
ms.assetid: cd445949-dc10-42fc-8785-4db74c9723ad
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5d65ab909d3683c27e9f99e084046a543cd546cf
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="run-jobs"></a>Esecuzione di processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Per gestire i processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], stored procedure [!INCLUDE[tsql](../../includes/tsql_md.md)] oppure oggetti SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Management Objects).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Viene illustrato come avviare l'esecuzione di un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Start a Job](../../ssms/agent/start-a-job.md)|  
|Viene illustrato come arrestare un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Stop a Job](../../ssms/agent/stop-a-job.md)|  
|Viene illustrato come disabilitare o abilitare un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Abilitare o disabilitare un processo](../../ssms/agent/disable-or-enable-a-job.md)|  
  
## <a name="see-also"></a>Vedere anche  
[sysdownloadlist](http://msdn.microsoft.com/en-us/71087a4c-e829-488e-aa7d-a9476e2b4779)  
  
