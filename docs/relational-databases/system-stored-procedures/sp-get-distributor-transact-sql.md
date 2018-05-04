---
title: sp_get_distributor (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 71be140eb309c36a9801f7d32b45123100704333
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spgetdistributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Determina se in un server è installato un server di distribuzione. Questa stored procedure viene eseguita in qualsiasi database del computer in cui viene cercato il server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Installato**|**int**|**0** = No. **1** = Sì|  
|**server di distribuzione**|**sysname**|Nome del server di distribuzione|  
|**database di distribuzione installato**|**int**|**0** = No. **1** = Sì|  
|**è la distribuzione server di pubblicazione**|**int**|**0** = No. **1** = Sì|  
|**con server di pubblicazione di distribuzione remoto**|**int**|**0** = No. **1** = Sì|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_get_distributor** viene utilizzata principalmente le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in snapshot, transazionale e di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può eseguire **sp_get_distributor**. Un set di risultati non NULL viene restituito quando la stored procedure viene eseguita dai membri del **db_owner** o **replmonitor** ruoli predefiniti del database nel database di distribuzione o i membri del  **db_owner** ruolo predefinito del database su almeno un database pubblicato. Un set di risultati non NULL viene restituito anche quando questa stored procedure viene eseguita dagli utenti nell'elenco di accesso alla pubblicazione (PAL) di almeno un database pubblicato o nell'elenco di accesso del database di distribuzione per un Server di pubblicazione non SQL, possono inoltre eseguire **sp _get_distributor**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Script di informazioni su database di distribuzione e server di pubblicazione](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
