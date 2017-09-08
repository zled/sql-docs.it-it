---
title: USER_ID (Transact-SQL) | Documenti Microsoft
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
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a40853c10e17969c78ef88e4b75995e77b8a1bac
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il numero di identificazione per un utente del database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *utente*  
 Nome utente da utilizzare. *utente* è **nchar**. Se un **char** è specificato il valore, viene convertito implicitamente in **nchar**. È necessario utilizzare le parentesi.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 Quando *utente* viene omesso, viene utilizzato l'utente corrente. Se il parametro contiene la parola NULL, restituirà NULL. Se viene chiamata dopo EXECUTE AS, la funzione USER_ID restituirà l'ID del contesto rappresentato.  
  
 Se un'entità di Windows di cui non è stato eseguito il mapping a uno specifico utente del database accede a un database tramite l'appartenenza a un gruppo, USER_ID restituisce 0 (ID del ruolo public). Se tale entità crea un oggetto senza specificare uno schema, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creerà un utente e uno schema impliciti di cui viene eseguito il mapping all'entità di Windows. L'utente creato in questo modo non può essere utilizzato per connettersi al database. Le chiamate alla funzione USER_ID da parte di un'entità di Windows di cui è eseguito il mapping a un utente implicito restituiranno l'ID dell'utente implicito.  
  
 È possibile utilizzare USER_ID in un elenco di selezione, in una clausola WHERE e in tutti i casi in cui è consentita un'espressione. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero di identificazione per l'utente di `AdventureWorks2012` `Harold`.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [USER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40; Transact-SQL &#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
