---
title: sp_changereplicationserverpasswords (Transact-SQL) | Microsoft Docs
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
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 4ae1883006db7eaffe1e10ffcee2c36619f66c73
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029962"
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le password archiviate per il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso utilizzato dagli agenti di replica durante la connessione al server in una topologia di replica. Di norma sarebbe necessario modificare la password per ogni singolo agente in esecuzione nel server, anche se tutti utilizzano lo stesso account o lo stesso account di accesso. Questa stored procedure consente di modificare la password per tutte le istanze di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un account di Windows specifico utilizzato da tutti gli agenti di replica in esecuzione in un server. Questa stored procedure viene eseguita in qualsiasi server della topologia di replica nel database master.  
  
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
 Nuova password da archiviare per l'oggetto specificato *account di accesso*. *la password* viene **sysname**, non prevede alcun valore predefinito.  
  
> [!NOTE]  
>  Dopo aver modificato una password per la replica è necessario arrestare e riavviare ogni agente che utilizza la password prima che la modifica abbia effetto per tale agente.  
  
 [ **@server** =] **'***server***'**  
 Connessione server per cui viene modificata la password archiviata. *server* viene **sysname**, i possibili valori sono i seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|**server di distribuzione**|Tutte le connessioni di agenti al server di distribuzione.|  
|**publisher**|Tutte le connessioni di agenti al server di pubblicazione.|  
|**subscriber**|Tutte le connessioni di agenti al Sottoscrittore.|  
|**%** (impostazione predefinita)|Tutte le connessioni di agenti a tutti i server di una topologia di replica.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_changereplicationserverpasswords** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le impostazioni di sicurezza della replica](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
