---
title: sp_grant_publication_access (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_grant_publication_access_TSQL
- sp_grant_publication_access
helpviewer_keywords: sp_grant_publication_access
ms.assetid: 17993952-def6-4a16-b1c1-323ec42967f8
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a961e086d738d1784884142f22ed6dd45928897
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spgrantpublicationaccess-transact-sql"></a>sp_grant_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un account di accesso all'elenco di accesso alla pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_grant_publication_access [ @publication = ] 'publication', [ @login = ] 'login'   
    [ , [ @reserved = ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione a cui si desidera accedere. **'***pubblicazione***'** è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@login** =] **'***accesso***'**  
 ID di accesso. **'***accesso***'** è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@reserved =**] **'***riservato***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_grant_publication_access** viene utilizzata in repliche snapshot, transazionali e di tipo merge.  
  
 È possibile chiamare questa stored procedure ripetutamente.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_grant_publication_access**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_publication_access &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
