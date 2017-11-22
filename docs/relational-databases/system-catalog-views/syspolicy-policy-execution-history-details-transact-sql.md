---
title: syspolicy_policy_execution_history_details (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_details
- syspolicy_policy_execution_history_details_TSQL
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_execution_history_details view
ms.assetid: 97ef6573-5e8b-4ba5-8ae0-7901e79a9683
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4bb2d7ba198275e14344be70df82e59153e341bf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicyexecutionhistorydetails-transact-sql"></a>syspolicy_policy_execution_history_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le espressioni di condizione eseguite, le destinazioni delle espressioni, il risultato di ciascuna esecuzione e le informazioni su eventuali errori. Nella tabella seguente sono descritte le colonne contenute nella vista syspolicy_execution_history_details.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|detail_id|**bigint**|Identificatore del record. Ogni record rappresenta il tentativo di valutare o applicare un'espressione della condizione nei criteri. Se applicato a più destinazioni, ogni condizione disporrà di un record di dettaglio per ciascuna destinazione.|  
|history_id|**bigint**|Identificatore dell'evento di cronologia. Ogni evento della cronologia rappresenta un tentativo di esecuzione dei criteri. Poiché una condizione può disporre di molte espressioni e molte destinazioni, un identificatore history_id può creare molti record di dettaglio. Utilizzare la colonna history_id per unire questa vista per la [syspolicy_policy_execution_history](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-transact-sql.md) visualizzazione.|  
|target_query_expression|**nvarchar(max)**|Destinazione del criterio e della vista syspolicy_policy_execution_history.|  
|execution_date|**datetime**|Data e ora in cui è stato creato il record di dettaglio.|  
|result|**bit**|Esito positivo o negativo della valutazione di questa destinazione e dell'espressione della condizione:<br /><br /> 0 (esito positivo) o 1 (esito negativo)|  
|result_detail|**nvarchar(max)**|Messaggio del risultato. Disponibile solo se fornito dal facet.|  
|exception_message|**nvarchar(max)**|Messaggio generato da un'eventuale eccezione.|  
|exception|**nvarchar(max)**|Descrizione dell'eventuale eccezione.|  
  
## <a name="remarks"></a>Osservazioni  
 Durante la risoluzione di problemi relativi alla gestione basata su criteri, eseguire una query sulla vista syspolicy_policy_execution_history_details per stabilire quali combinazioni di destinazione ed espressione di condizione hanno avuto esito negativo, in quali casi hanno avuto esito negativo e per analizzare gli errori correlati.  
  
 Nella query seguente la vista `syspolicy_policy_execution_history_details` viene combinata con le viste `syspolicy_policy_execution_history_details` e `syspolicy_policies` per visualizzare il nome dei criteri, il nome della condizione e le informazioni sugli errori.  
  
```  
SELECT Pol.name AS Policy,   
Cond.name AS Condition,   
PolHistDet.target_query_expression,   
PolHistDet.execution_date,   
PolHistDet.result,   
PolHistDet.result_detail,   
PolHistDet.exception_message,   
PolHistDet.exception   
FROM msdb.dbo.syspolicy_policies AS Pol  
JOIN msdb.dbo.syspolicy_conditions AS Cond  
    ON Pol.condition_id = Cond.condition_id  
JOIN msdb.dbo.syspolicy_policy_execution_history AS PolHist  
    ON Pol.policy_id = PolHist.policy_id  
JOIN msdb.dbo.syspolicy_policy_execution_history_details AS PolHistDet  
    ON PolHist.history_id = PolHistDet.history_id  
WHERE PolHistDet.result = 0 ;  
```  
  
## <a name="permissions"></a>Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Viste di Gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
