---
title: sp_syspolicy_set_log_on_success (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_log_on_success_TSQL
- sp_syspolicy_set_log_on_success
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_set_log_on_success
ms.assetid: 6b33383b-5949-488a-a911-59299a270f46
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3a24dbe06ef91bb46b5fb81dbd3cc59709a767e8
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025062"
---
# <a name="spsyspolicysetlogonsuccess-transact-sql"></a>sp_syspolicy_set_log_on_success (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Specifica se vengono registrate le valutazioni di criteri riuscite nel log Cronologia criteri per la gestione basata su criteri.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syspolicy_set_log_on_success [ @value = ] value  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@value=** ] *valore*  
 Determina se le valutazioni di criteri riuscite vengono registrate. *valore* viene **sqlvariant**, e può essere uno dei valori seguenti:  
  
-   0 o 'false' = Le valutazioni di criteri riuscite non vengono registrate.  
  
-   1 o 'true' = Le valutazioni di criteri riuscite vengono registrate.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 È necessario eseguire sp_syspolicy_set_log_on_success nel contesto del database di sistema msdb.  
  
 Quando *valore* è impostato su 0 o 'false', solo non è stato possibile vengono registrate le valutazioni di criteri.  
  
## <a name="permissions"></a>Permissions  
 È necessaria l'appartenenza al ruolo predefinito del database PolicyAdministratorRole.  
  
> **IMPORTANTE** Possibile elevazione di credenziali: gli utenti nel ruolo PolicyAdministratorRole possono creare trigger server e pianificare le esecuzioni di criteri che influiscono sul funzionamento dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Gli utenti con il ruolo PolicyAdministratorRole possono ad esempio creare criteri che impediscono la creazione della maggior parte degli oggetti nel [!INCLUDE[ssDE](../../includes/ssde-md.md)]. A causa di questa possibile elevazione di credenziali, il ruolo PolicyAdministratorRole deve essere concesso solo a utenti ritenuti attendibili per il controllo della configurazione del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene abilitata la registrazione delle valutazioni di criteri riuscite.  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_log_on_success @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure della gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
