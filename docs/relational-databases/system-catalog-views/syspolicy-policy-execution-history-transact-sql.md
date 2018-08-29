---
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7db5a20395ec6e0e41d70d6b2dbb04dee991a0c1
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021395"
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza l'ora in cui i criteri sono stati eseguiti, il risultato di ogni esecuzione e le informazioni su eventuali errori. Nella tabella seguente sono descritte le colonne contenute nella vista syspolicy_policy_execution_history.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificatore del record. Ogni record indica i criteri e l'ora in cui è stato avviato.|  
|policy_id|**int**|Identificatore dei criteri.|  
|start_date|**datetime**|Data e ora in cui è stato effettuato un tentativo di esecuzione di questi criteri.|  
|end_date|**datetime**|Ora in cui è terminata l'esecuzione di questi criteri.|  
|result|**bit**|Esito positivo o negativo dei criteri. 0 = esito negativo, 1 = esito positivo.|  
|exception_message|**nvarchar(max)**|Messaggio generato da un'eventuale eccezione.|  
|exception|**nvarchar(max)**|Descrizione dell'eventuale eccezione.|  
  
## <a name="remarks"></a>Note  
 Il [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) vista contiene informazioni dettagliate correlate sulle destinazioni dei criteri e le espressioni di condizione testate.  
  
## <a name="permissions"></a>Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Viste di Gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
