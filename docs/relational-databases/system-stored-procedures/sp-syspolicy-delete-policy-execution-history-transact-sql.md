---
title: sp_syspolicy_delete_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c505a71c0906e46719f92959c61858af5cacec8a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina la cronologia di esecuzione dei criteri nella gestione basata su criteri. È possibile utilizzare questa stored procedure per eliminare la cronologia di esecuzione per criteri specifici o per tutti i criteri, nonché per eliminare la cronologia di esecuzione precedente a una data specifica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@policy_id=** ] *policy_id*  
 Identificatore dei criteri per cui si desidera eliminare la cronologia di esecuzione. *policy_id* è **int**ed è obbligatorio. Può essere NULL.  
  
 [  **@oldest_date=** ] **'***oldest_date***'**  
 Data meno recente per la quale si desidera mantenere la cronologia di esecuzione dei criteri. Qualsiasi cronologia di esecuzione precedente a questa data viene eliminata. *oldest_date* è **datetime**ed è obbligatorio. Può essere NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire sp_syspolicy_delete_policy_execution_history nel contesto del database di sistema msdb.  
  
 Per ottenere valori per *policy_id*, e per visualizzare le date della cronologia di esecuzione, è possibile utilizzare la query seguente:  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 Il comportamento seguente è valido se si specifica NULL per uno o entrambi i valori:  
  
-   Per eliminare l'intera cronologia di esecuzione, specificare NULL per entrambi *policy_id* e per *oldest_date*.  
  
-   Per eliminare l'intera cronologia di esecuzione per criteri specifici, specificare un identificatore dei criteri *policy_id*, e specificare NULL come *oldest_date*.  
  
-   Per eliminare la cronologia di esecuzione di criteri per tutti i criteri prima di una data specifica, specificare NULL per *policy_id*e specificare una data per *oldest_date*.  
  
 Per archiviare la cronologia di esecuzione dei criteri, è possibile aprire il log Cronologia criteri in Esplora oggetti ed esportare la cronologia di esecuzione in un file. Per accedere il log cronologia criteri, espandere **Management**, fare doppio clic su **Gestione criteri di**, quindi fare clic su **Visualizza cronologia**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'appartenenza al ruolo predefinito del database PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Possibile elevazione di credenziali: gli utenti nel ruolo PolicyAdministratorRole possono creare trigger server e pianificare le esecuzioni di criteri che influiscono sul funzionamento dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Gli utenti con il ruolo PolicyAdministratorRole possono ad esempio creare criteri che impediscono la creazione della maggior parte degli oggetti nel [!INCLUDE[ssDE](../../includes/ssde-md.md)]. A causa di questa possibile elevazione di credenziali, il ruolo PolicyAdministratorRole deve essere concesso solo a utenti ritenuti attendibili per il controllo della configurazione del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminata la cronologia di esecuzione dei criteri precedente a una data specifica, per criteri con ID 7.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione basata su criteri di Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
