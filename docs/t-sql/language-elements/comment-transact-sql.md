---
title: -(Commento) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --_TSQL
- Comment
- --
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- remarks [SQL Server]
- -- (comment character)
- comments [SQL Server]
ms.assetid: 676ea8c2-52c1-4ef6-9354-320f1a091153
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a03aff79db25c07fc828145177e29196405a9264
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="---comment-transact-sql"></a>-- (commento) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Evidenzia il testo inserito dall'utente. I commenti possono essere inseriti su una riga distinta oppure nidificati alla fine di una riga di comando di [!INCLUDE[tsql](../../includes/tsql-md.md)] o in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nel server il commento non viene valutato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Argomenti  
 *text_of_comment*  
 Stringa di caratteri contenente il testo del commento.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare due trattini (--) per commenti su una sola riga o nidificati. I commenti inseriti con -- sono delimitati dal carattere di nuova riga. I commenti possono essere di qualsiasi lunghezza. Nella tabella seguente sono elencati i tasti di scelta rapida che è possibile utilizzare per impostare o meno il testo come commento.  
  
|Azione|Standard|  
|------------|--------------|  
|Impostare il testo selezionato come commento|CTRL+K, CTRL+C|  
|Rimuovere il commento dal testo selezionato|CTRL+K, CTRL + U|  
  
 Per ulteriori informazioni sui tasti di scelta rapida, vedere [SQL Server Management Studio tasti di scelta rapida](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
 Per commenti su più righe, vedere [barra stella commento &#40; Transact-SQL &#41; ](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono utilizzati i caratteri -- per l'inserimento di un commento.  
  
```  
-- Choose the AdventureWorks2012 database.  
USE AdventureWorks2012;  
GO  
-- Choose all columns and all rows from the Address table.  
SELECT *  
FROM Person.Address  
ORDER BY PostalCode ASC; -- We do not have to specify ASC because   
-- that is the default.  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Il controllo di flusso Language &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  

