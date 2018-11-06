---
title: Oggetto JobSteps di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fab5edc3dc09c29217cbe17b61bf5c180fee13c9
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030008"
---
# <a name="sql-server-agent-jobsteps-object"></a>Oggetto JobSteps di SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JobSteps **di** Agent contiene contatori delle prestazioni che forniscono informazioni relative ai passaggi di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Nella tabella seguente sono elencati i contatori inclusi nell'oggetto.  
  
 Nella tabella seguente sono inclusi i contatori **SQLAgent:Passaggi processi** .  
  
|nome|Descrizione|  
|----------|-----------------|  
|**Passaggi attivi**|In questo contatore viene visualizzato il numero di passaggi del processo attualmente in esecuzione.|  
|**Passaggi in coda**|In questo contatore viene visualizzato il numero di passaggi del processo pronti per l'esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, ma la cui esecuzione non è ancora stata avviata.|  
|**Totale tentativi passaggio**|In questo contatore viene visualizzato il numero totale di tentativi di esecuzione di un passaggio del processo in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal momento dell'ultimo riavvio del server.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Istanza|Descrizione|  
|--------------|-----------------|  
|**_Total**|Informazioni su tutti i passaggi del processo.|  
|**ActiveScripting**|Informazioni per i passaggi del processo che utilizzano il sottosistema **ActiveScripting** .|  
|**ANALYSISCOMMAND**|Informazioni per i passaggi del processo che utilizzano il sottosistema ANALYSISCOMMAND.|  
|**ANALYSISQUERY**|Informazioni per i passaggi del processo che utilizzano il sottosistema ANALYSISQUERY.|  
|**CmdExec**|Informazioni per i passaggi del processo che utilizzano il sottosistema **CmdExec** .|  
|**Distribuzione**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Distribution** .|  
|**Dts**|Informazioni per i passaggi del processo che utilizzano il sottosistema [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|**LogReader**|Informazioni per i passaggi del processo che utilizzano il sottosistema **LogReader** .|  
|**Merge**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Merge** .|  
|**PowerShell**|Informazioni per i passaggi del processo che utilizzano il sottosistema **PowerShell** .|  
|**QueueReader**|Informazioni per i passaggi del processo che utilizzano il sottosistema **QueueReader** .|  
|**Snapshot**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Snapshot** .|  
|**TSQL**|Informazioni per i passaggi del processo che comportano l'esecuzione di [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)   
 [Utilizzo degli oggetti prestazioni](../../ssms/agent/use-performance-objects.md)   
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
