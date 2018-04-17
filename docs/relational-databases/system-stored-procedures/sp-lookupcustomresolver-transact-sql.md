---
title: sp_lookupcustomresolver (Transact-SQL) | Documenti Microsoft
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
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad45f26fbd1c6b7f9488497333f5ba44a2b5fa8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni su un gestore della logica di business o il valore dell'identificatore di classe (CLSID) di un componente di un sistema di risoluzione personalizzato basato su COM che è registrato nel server di distribuzione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@article_resolver =** ] **'***article_resolver***'**  
 Specifica il nome della logica di business personalizzata di cui annullare la registrazione. *article_resolver* viene **nvarchar(255**, non prevede alcun valore predefinito. Se la logica di business in fase di rimozione è un componente COM, questo parametro è il nome descrittivo del componente. Se la logica di business è un assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, questo parametro è il nome dell'assembly.  
  
 [ **@resolver_clsid**=] **'***resolver_clsid***'** OUTPUT  
 Valore CLSID dell'oggetto COM associato al nome della logica di business personalizzata specificata nel *article_resolver* parametro. *resolver_clsid* viene **nvarchar(50**, con un valore predefinito è NULL.  
  
 [  **@is_dotnet_assembly=** ] **'***is_dotnet_assembly***'** OUTPUT  
 Specifica il tipo di logica di business personalizzata di cui è in corso la registrazione. *is_dotnet_assembly* viene **bit**, con un valore predefinito è 0. **1** indica che la logica di business personalizzata è un gestore della logica di business Assembly. **0** indica che si tratta di un componente COM.  
  
 [  **@dotnet_assembly_name=** ] **'***dotnet_assembly_name***'** OUTPUT  
 Nome dell'assembly che implementa il gestore della logica di business. *dotnet_assembly_name* viene **nvarchar(255**, con valore predefinito è NULL.  
  
 [  **@dotnet_class_name=** ] **'***dotnet_class_name***'** OUTPUT  
 Nome della classe che sostituisce <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> per implementare il gestore della logica di business. *dotnet_class_name* viene **nvarchar(255**, con valore predefinito è NULL.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con valore predefinito è NULL. Utilizzare questo parametro quando la stored procedure non viene chiamata dal server di pubblicazione. Se omesso, si presuppone che il server locale è il server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_lookupcustomresolver** viene utilizzata nella replica di tipo merge.  
  
 **sp_lookupcustomresolver** restituisce un valore NULL per *resolver_clsid* quando il componente non è registrato nel server di distribuzione e il valore "00000000-0000-0000-0000-000000000000" quando la registrazione appartiene a un Assembly di .NET framework registrato come gestore della logica di business.  
  
 **sp_lookupcustomresolver** viene chiamato da [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) convalidare specificato *article_resolver*.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **db_owner** ruolo predefinito del database nel database di pubblicazione possono eseguire **sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Eseguire una logica di Business durante la sincronizzazione di tipo Merge](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Specificare un Resolver di articolo di Merge](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
