---
title: Oggetto JobSteps di SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6d6953a342ab24540da33464962712ea43579f8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-agent-jobsteps-object"></a>Oggetto JobSteps di SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L'oggetto prestazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]JobSteps **di**  Agent contiene contatori delle prestazioni che forniscono informazioni relative ai passaggi di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Nella tabella seguente sono elencati i contatori inclusi nell'oggetto.  
  
 Nella tabella seguente sono inclusi i contatori **SQLAgent:Passaggi processi** .  
  
|Nome|Descrizione|  
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
 [Gestire passaggi di processo](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [Utilizzo degli oggetti prestazioni](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
