---
title: SESSION_ID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2a0d500a-f6c8-490f-9abd-3ae824986404
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9089c21109d6eedb1cdae0082e1530e8d77d9dde
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Restituisce l'ID dell'oggetto corrente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] sessione.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **nvarchar(32)** valore.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 L'ID di sessione viene assegnato a ogni connessione utente quando viene stabilita la connessione. Mantenuto per la durata della connessione. Al termine della connessione, l'ID di sessione viene rilasciato.  
  
 L'ID di sessione inizia con i caratteri alfabetici 'SID'. Questi tra maiuscole e minuscole e deve essere in maiuscolo quando viene usato l'ID di sessione [!INCLUDE[DWsql](../../includes/dwsql-md.md)] comandi.  
  
 È possibile eseguire una query la visualizzazione [sys.dm_pdw_exec_sessions](http://msdn.microsoft.com/en-us/5b656c55-427f-4306-8bd9-9d7987c203d9) per recuperare le stesse informazioni di questa funzione.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce l'ID di sessione corrente.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Db_name &#40; Transact-SQL &#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSIONE &#40; SQL Data Warehouse &#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  

