---
title: PWDCOMPARE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6aadde33d6d1ee1404170197c32ab77ade2dbfad
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue l'hashing di una password e confronta l'hash con l'hash di una password esistente. È possibile utilizzare PWDCOMPARE per eseguire la ricerca di password di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vuote o di password comuni vulnerabili.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *clear_text_password* **'**  
 Password non crittografata. *clear_text_password* è **sysname** (**nvarchar (128)**).  
  
 *password_hash*  
 Hash di crittografia di una password. *password_hash* è **varbinary(128)**.  
  
 *Versione*  
 Parametro obsoleto che può essere impostato su 1 se *password_hash* rappresenta un valore da un account di accesso antecedente [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] che è stata eseguita la migrazione a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva ma mai stato convertito il [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] sistema. *versione* è **int**.  
  
> [!CAUTION]  
>  Questo parametro viene fornito per la compatibilità con le versioni precedenti, ma viene ignorato poiché ora i BLOB dell'hash della password contengono le descrizioni delle versioni. [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
 Restituisce 1 se l'hash di *clear_text_password* corrisponde la *password_hash* parametro e 0 in caso contrario.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione PWDCOMPARE non costituisce un rischio per la sicurezza degli hash delle password, in quanto lo stesso test può essere eseguito tentando di accedere con la password fornita come primo parametro.  
  
 **PWDCOMPARE** non può essere utilizzato con le password degli utenti del database indipendente. Non esiste un equivalente per i database indipendenti.  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT è disponibile per il ruolo public.  
  
 Per esaminare la colonna password_hash di sys.sql_logins, è richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. Identificazione degli account di accesso che non dispongono di password  
 Nell'esempio seguente vengono identificati gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che non dispongono di password.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>B. Ricerca di password comuni  
 Per eseguire la ricerca di password comuni che si desidera identificare e cambiare, specificare la password come primo parametro. Eseguire ad esempio l'istruzione seguente per eseguire la ricerca di una password specificata come `password`.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [PWDENCRYPT &#40; Transact-SQL &#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

