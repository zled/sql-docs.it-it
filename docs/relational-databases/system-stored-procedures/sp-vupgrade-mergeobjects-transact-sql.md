---
title: sp_vupgrade_mergeobjects (Transact-SQL) | Documenti Microsoft
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
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 991c8f5d6e94724fec85370f354cd19bf6584ffe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spvupgrademergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rigenera stored procedure, viste e trigger specifici dell'articolo che vengono utilizzati per il rilevamento e l'applicazione delle modifiche dei dati per la replica di tipo merge. Eseguire questa stored procedure nelle situazioni seguenti:  
  
-   Se un oggetto necessario per la replica viene accidentalmente eliminato.  
  
-   Se si applica un aggiornamento, ad esempio un hotfix, che richiede la modifica di uno o più oggetti di replica. Eseguire la stored procedure in ogni nodo dopo l'applicazione dell'aggiornamento.  
  
 In caso di esecuzione di questa stored procedure non è necessaria la reinizializzazione delle sottoscrizioni. La stored procedure non è necessaria se si installa un Service Pack o un aggiornamento a una nuova versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@login=**] **'***account di accesso***'**  
 Account di accesso dell'amministratore di sistema da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *login* è di tipo **sysname** e il valore predefinito è NULL. Questo parametro non è obbligatorio se *security_mode* è impostato su **1**, ovvero l'autenticazione di Windows.  
  
 [  **@password=**] **'***password***'**  
 Password dell'amministratore di sistema da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *password* viene **sysname**, il valore predefinito è **'** (stringa vuota). Questo parametro non è obbligatorio se *security_mode* è impostato su **1**, ovvero l'autenticazione di Windows.  
  
 [  **@security_mode=**] **'***security_mode***'**  
 Modalità di sicurezza di accesso da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *security_mode* viene **bit** con valore predefinito è **1**. Se **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà utilizzata l'autenticazione. Se **1**, verrà utilizzata l'autenticazione di Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_vupgrade_mergeobjects** viene utilizzato solo per la replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Aggiornare database replicati](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
