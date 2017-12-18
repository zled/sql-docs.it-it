---
title: Eliminare processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 943a5b2722ee0c4d61ce37629d00e73159fa0109
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="delete-jobs"></a>eliminare processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Un processo è una serie specificata di operazioni eseguite in sequenza tramite SQL Server Agent. Per impostazione predefinita, i processi non vengono eliminati al termine dell'esecuzione. È possibile eliminare uno o più processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, indipendentemente dall'esito positivo o negativo del processo. È inoltre possibile configurare [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per eliminare automaticamente determinati processi in caso di esito positivo, esito negativo o completamento.  
  
Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono eseguire la stored procedure di sistema [sp_delete_job (Transact-SQL)](http://msdn.microsoft.com/en-us/b85db6e4-623c-41f1-9643-07e5ea38db09) per eliminare un processo. Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
I membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_delete_job** per l'eliminazione di qualsiasi processo. Se un utente non è un membro del ruolo predefinito del server **sysadmin** , può eliminare solo i processi di sua proprietà.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Description**|**Argomento**|  
|Informazioni su come eliminare uno o più processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Eliminare uno o più processi](../../ssms/agent/delete-one-or-more-jobs.md)|  
|Informazioni su come configurare [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per eliminare automaticamente determinati processi in caso di esito positivo, esito negativo o completamento.|[Automatically Delete a Job](../../ssms/agent/automatically-delete-a-job.md)|  
  
