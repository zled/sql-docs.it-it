---
title: sp_unsetapprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f57eb690c679218d9bd8f639e3f3215652351f5b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026940"
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
 Specifica il cookie creato al momento dell'attivazione del ruolo applicazione. Il cookie viene creato da [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md). **varbinary(8000**.  
  
> [!NOTE]  
>  Il parametro **OUTPUT** del cookie per **sp_setapprole** è attualmente documentato come **varbinary(8000)** che rappresenta la lunghezza massima corretta. Tuttavia, l'implementazione corrente restituisce **varbinary(50)**. Le applicazioni devono continuare a riservare **varbinary(8000** in modo che l'applicazione continua a funzionare correttamente se il cookie di restituisce le dimensioni aumentano in una versione futura.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 Dopo un'applicazione l'attivazione di ruolo usando **sp_setapprole**, tale ruolo rimane attivo fino a quando l'utente si disconnette dal server o all'esecuzione **sp_unsetapprole**.  
  
 Per una panoramica dei ruoli applicazione, vedere [i ruoli applicazione](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **pubblica** e conoscere il cookie salvato quando è stato attivato il ruolo applicazione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>Attivazione di un ruolo applicazione con un cookie e ripristino del contesto precedente  
 Nell'esempio seguente viene attivato il ruolo applicazione `Sales11` con la password `fdsd896#gfdbfdkjgh700mM` e viene creato un cookie. L'esempio restituisce il nome dell'utente corrente e quindi Ripristina il contesto originale tramite l'esecuzione **sp_unsetapprole**.  
  
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
  
  
