---
title: sp_unsetapprole (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 817a2c5e10069654725efeab656b7788c8ce2a1c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spunsetapprole-transact-sql"></a>sp_unsetapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Disattiva un ruolo applicazione e ripristina il contesto di sicurezza precedente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_unsetapprole @cookie   
```  
  
## <a name="arguments"></a>Argomenti  
 **@cookie**  
 Specifica il cookie creato al momento dell'attivazione del ruolo applicazione. Il cookie viene creato da [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md). **varbinary(8000)**.  
  
> [!NOTE]  
>  Il parametro **OUTPUT** del cookie per **sp_setapprole** è attualmente documentato come **varbinary(8000)** che rappresenta la lunghezza massima corretta. Tuttavia, l'implementazione corrente restituisce **varbinary(50)**. Le applicazioni devono continuare a riservare **varbinary (8000)** in modo che l'applicazione continua a funzionare correttamente se il cookie restituito dimensioni aumentano in una versione futura.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Dopo un'applicazione attivato utilizzando ruolo **sp_setapprole**, tale ruolo rimane attivo fino a quando l'utente si disconnette dal server o esegue **sp_unsetapprole**.  
  
 Per una panoramica dei ruoli applicazione, vedere [ruoli applicazione](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza **pubblica** e conoscere il cookie salvato quando è stato attivato il ruolo applicazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>Attivazione di un ruolo applicazione con un cookie e ripristino del contesto precedente  
 Nell'esempio seguente viene attivato il ruolo applicazione `Sales11` con la password `fdsd896#gfdbfdkjgh700mM` e viene creato un cookie. L'esempio restituisce il nome dell'utente corrente e quindi Ripristina il contesto originale tramite l'esecuzione di **sp_unsetapprole**.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
