---
title: sp_helptracertokens (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_helptracertokens
- sp_helptracertokens_TSQL
helpviewer_keywords:
- sp_helptracertokens
ms.assetid: 61f27234-531d-4b37-8fa3-fe4c32e6f521
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aeead4e1604030851ef1e9a3474a83adb6cb06b2
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022839"
---
# <a name="sphelptracertokens-transact-sql"></a>sp_helptracertokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni token di traccia che è stato inserito in una pubblicazione per determinare la latenza. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helptracertokens [ @publication = ] 'publication'   
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione in cui sono stati inseriti i token di traccia. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro deve essere specificato solo per non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, con un valore predefinito NULL. Questo parametro viene ignorato se la stored procedure viene eseguita nel server di pubblicazione.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|Identifica un record di token di traccia.|  
|**publisher_commit**|**datetime**|Data e ora in cui è stato eseguito il commit del record del token nel database di pubblicazione del server di pubblicazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_helptracertokens** viene utilizzata nella replica transazionale.  
  
 **sp_helptracertokens** viene usato per ottenere gli ID dei token dello strumento di analisi quando si esegue [sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md).  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokens-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database nel database di pubblicazione, o **db_owner** predefiniti del database o  **replmonitor** nel database di distribuzione possono eseguire **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
