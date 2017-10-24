---
title: SETUSER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETUSER_TSQL
- SETUSER
dev_langs:
- TSQL
helpviewer_keywords:
- delegation [SQL Server]
- impersonation [SQL Server]
- SETUSER statement
- user impersonation [SQL Server]
ms.assetid: 7acfac5c-9ad6-4226-b874-7add36c4ea43
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab9805dda5f5b2b4199cb40ef3c28af1d5b4379f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="setuser-transact-sql"></a>SETUSER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente a un membro del **sysadmin** fissa ruolo del server o il proprietario di un database per rappresentare un altro utente.  
  
> [!IMPORTANT]  
>  SETUSER è disponibile solo per garantire la compatibilità con le versioni precedenti in quanto nelle future versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe non essere più supportata. È consigliabile utilizzare [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SETUSER [ 'username' [ WITH NORESET ] ]   
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *username* **'**  
 Nome di un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o di Windows nel database corrente che viene rappresentato. Quando *username* non viene specificato, l'identità originale dell'amministratore di sistema o proprietario del database che rappresenta l'utente viene reimpostato.  
  
 WITH NORESET  
 Specifica che le successive istruzioni SETUSER (senza specificata *username*) non ripristinano l'identità dell'utente all'amministratore di sistema o proprietario del database.  
  
## <a name="remarks"></a>Osservazioni  
 SETUSER può essere utilizzato da un membro del **sysadmin** fissa ruolo del server o il proprietario di un database di adottare l'identità di un altro utente per testare le autorizzazioni di altro utente. L'appartenenza al ruolo predefinito del database db_owner non è sufficiente.  
  
 Utilizzare l'istruzione SETUSER solo per utenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in quanto non è supportata per gli utenti di Windows. Dopo l'esecuzione di SETUSER per assumere l'identità di un altro utente, tutti gli oggetti che vengono creati sono di proprietà dell'utente rappresentato. Ad esempio, se il proprietario del database presuppone che l'identità dell'utente **Margaret** e crea una tabella denominata **ordini**, **ordini** tabella è di proprietà **Margaret** , non l'amministratore di sistema.  
  
 L'istruzione SETUSER rimane valida fino a quando non viene eseguita un'altra istruzione SETUSER o il database corrente viene modificato tramite l'istruzione USE.  
  
> [!NOTE]  
>  Se il proprietario del database o l'amministratore del sistema utilizza l'istruzione SETUSER WITH NORESET, per ristabilire le proprie autorizzazioni deve disconnettersi e quindi riconnettersi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **sysadmin** ruolo predefinito del server o deve essere il proprietario del database. L'appartenenza di **db_owner** ruolo predefinito del database non è sufficiente  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come il proprietario del database può adottare l'identità di un altro utente. L'utente `mary` ha creato una tabella denominata `computer_types`. Tramite l'istruzione SETUSER, il proprietario del database rappresenta `mary` per concedere all'utente `joe` l'accesso alla tabella `computer_types` e quindi ripristina la propria identità.  
  
```  
SETUSER 'mary';  
GO  
GRANT SELECT ON computer_types TO joe;  
GO  
--To revert to the original user  
SETUSER;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
  
  

