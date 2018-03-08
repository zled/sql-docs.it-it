---
title: sysssislog (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
caps.latest.revision: 
author: spelluru
ms.author: spelluru
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 479c6158f7c26cde133fae66164dda89b9a39888
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni voce di log generata da pacchetti o dalle loro attività o contenitori in fase di esecuzione. Questa tabella viene creata nel database msdb al momento dell'installazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Se si configura la registrazione nei log in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diverso, viene creata una tabella sysssislog con questo formato nel database specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scrive le voci di registrazione in questa tabella **solo** quando i pacchetti utilizzano il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di log.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Identificatore univoco della voce del log.|  
|evento|**sysname**|Nome dell'evento che ha generato la voce del log.|  
|computer|**nvarchar**|Computer in cui era in esecuzione il pacchetto al momento della generazione della voce del log.|  
|operatore|**nvarchar**|Nome utente della persona che ha eseguito il pacchetto che ha generato la voce del log.|  
|origine|**nvarchar**|Nome del file eseguibile nel pacchetto che ha generato la voce del log.|  
|sourceid|**uniqueidentifier**|GUID del file eseguibile nel pacchetto che ha generato la voce del log.|  
|executionid|**uniqueidentifier**|GUID dell'istanza di esecuzione del file eseguibile che ha generato la voce del log.|  
|starttime|**datetime**|Ora di inizio dell'esecuzione del pacchetto.|  
|endtime|**datetime**|Ora del completamento del pacchetto.<br /><br /> Questa funzionalità non è implementata. Il valore nella colonna endtime è sempre uguale al valore nella colonna starttime.|  
|datacode|**int**|Valore intero facoltativo che in genere indica il risultato dell'esecuzione del contenitore o dell'attività:|  
|databytes|**image**|Matrice di byte facoltativa che contiene informazioni aggiuntive.|  
|message|**nvarchar**|Descrizione dell'evento e delle informazioni associate all'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
