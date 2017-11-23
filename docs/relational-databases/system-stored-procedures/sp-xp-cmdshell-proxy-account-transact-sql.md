---
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9e7ca09bec357a99e0b02ba17baf04eb6b31c392
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spxpcmdshellproxyaccount-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea una credenziale proxy per **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** è disabilitato per impostazione predefinita. Per abilitare **xp_cmdshell**, vedere [opzione di configurazione del Server xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 NULL  
 Specifica che la credenziale proxy deve essere eliminata.  
  
 *account_name*  
 Specifica un account di accesso di Windows da utilizzare come proxy.  
  
 *password*  
 Specifica la password dell'account di Windows.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 La credenziale proxy verrà chiamata **xp_cmdshell_proxy_account # # # #**.  
  
 Quando viene eseguita con l'opzione NULL, **sp_xp_cmdshell_proxy_account** Elimina la credenziale del proxy.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-the-proxy-credential"></a>A. Creazione delle credenziali proxy  
 Nell'esempio seguente viene illustrata la creazione di una credenziale proxy per un account di Windows denominato `ADVWKS\Max04` con la password `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. Rimozione delle credenziali proxy  
 Nell'esempio seguente la credenziale proxy viene rimossa dall'archivio delle credenziali.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [xp_cmdshell &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
