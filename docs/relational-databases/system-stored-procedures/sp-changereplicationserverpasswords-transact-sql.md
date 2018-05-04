---
title: sp_changereplicationserverpasswords (Transact-SQL) | Documenti Microsoft
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
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f95ea9768d9aaf6e599cb353f32fe6cfd19b4ee8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia le password archiviate per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso utilizzato dagli agenti di replica per la connessione al server in una topologia di replica. Di norma sarebbe necessario modificare la password per ogni singolo agente in esecuzione nel server, anche se tutti utilizzano lo stesso account o lo stesso account di accesso. Questa stored procedure consente di modificare la password per tutte le istanze di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un account di Windows specifico utilizzato da tutti gli agenti di replica in esecuzione in un server. Questa stored procedure viene eseguita in qualsiasi server della topologia di replica nel database master.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@login_type** =] *login_type*  
 Tipo di autenticazione per le credenziali specificate. *LOGIN_TYPE* viene **tinyint**, non prevede alcun valore predefinito.  
  
 **1** = autenticazione integrata di Windows  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione  
  
 [ **@login** =] **'***account di accesso***'**  
 Nome dell'account di Windows o dell'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da modificare. *account di accesso* viene **nvarchar(257)**, non prevede alcun valore predefinito  
  
 [ **@password** =] **'***password***'**  
 È possibile archiviare la nuova password per l'oggetto specificato *accesso*. *password* viene **sysname**, non prevede alcun valore predefinito.  
  
> [!NOTE]  
>  Dopo aver modificato una password per la replica è necessario arrestare e riavviare ogni agente che utilizza la password prima che la modifica abbia effetto per tale agente.  
  
 [ **@server** =] **'***server***'**  
 Connessione server per cui viene modificata la password archiviata. *server* viene **sysname**, e può essere uno dei valori seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|**Server di distribuzione**|Tutte le connessioni di agenti al server di distribuzione.|  
|**publisher**|Tutte le connessioni di agenti al server di pubblicazione.|  
|**subscriber**|Tutte le connessioni di agenti al Sottoscrittore.|  
|**%** (impostazione predefinita)|Tutte le connessioni di agenti a tutti i server di una topologia di replica.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changereplicationserverpasswords** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
