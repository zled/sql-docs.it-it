---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Documenti Microsoft
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
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs:
- TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 86431229e26091e2fde6c3f81873523c5f09de68
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Elimina un elenco di parole non significative full-text dal database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!IMPORTANT]  
>  CREATE FULLTEXT STOPLIST è supportato solo per il livello di compatibilità 100 e superiore. Per i livelli di compatibilità 80 e 90, l'elenco di parole non significative di sistema viene sempre assegnato al database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP FULLTEXT STOPLIST stoplist_name  
;  
```  
  
## <a name="arguments"></a>Argomenti  
 *stoplist_name*  
 Nome dell'elenco di parole non significative full-text da eliminare dal database.  
  
## <a name="remarks"></a>Osservazioni  
 DROP FULLTEXT STOPLIST ha esito negativo se qualsiasi indice full-text fa riferimento all'elenco di parole non significative full-text da eliminare.  
  
## <a name="permissions"></a>Permissions  
 Per eliminare un elenco di parole non significative richiede l'autorizzazione DROP per tale elenco o l'appartenenza di **db_owner** o **db_ddladmin** ruoli predefiniti del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato un elenco di parole non significative full-text denominato `myStoplist`.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
