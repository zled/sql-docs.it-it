---
title: syspolicy_system_health_state (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e546ff0c3025812239aec6dbd1f466d9fc40c560
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza una riga per ogni combinazione di criteri di gestione basata su criteri ed espressione della query di destinazione. Utilizzare la vista syspolicy_system_health_state per controllare a livello di programmazione lo stato di integrità criteri del server. Nella tabella seguente sono descritte le colonne contenute nella vista syspolicy_system_health_state.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Identificatore del record di stato di integrità criteri.|  
|policy_id|**int**|Identificatore dei criteri.|  
|last_run_date|**datetime**|Data e ora dell'ultima esecuzione dei criteri.|  
|target_query_expression_with_id|**nvarchar(400)**|Espressione di destinazione, con valori assegnati a variabili di identità che definiscono la destinazione rispetto alla quale vengono valutati i criteri.|  
|target_query_expression|**nvarchar(max)**|Espressione tramite cui viene definita la destinazione rispetto alla quale vengono valutati i criteri.|  
|result|**bit**|Stato di integrità di questa destinazione in relazione ai criteri:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
  
## <a name="remarks"></a>Osservazioni  
 Nella vista syspolicy_system_health_state viene visualizzato lo stato di integrità più recente dell'espressione della query di destinazione per i criteri attivi (abilitati). Nella pagina Esplora oggetti e Dettagli Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vengono aggregati gli stati di integrità criteri di questa vista per mostrare lo stato di integrità critica.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Viste di Gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
