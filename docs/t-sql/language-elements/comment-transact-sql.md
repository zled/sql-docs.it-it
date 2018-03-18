---
title: -- (commento) (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2cae636f23fc166246b3cf6cb755fde570b3d19c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="---comment-transact-sql"></a>-- (commento) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Evidenzia il testo inserito dall'utente. I commenti possono essere inseriti su una riga distinta oppure nidificati alla fine di una riga di comando di [!INCLUDE[tsql](../../includes/tsql-md.md)] o in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nel server il commento non viene valutato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Argomenti  
 *text_of_comment*  
 Stringa di caratteri contenente il testo del commento.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare due trattini (--) per commenti su una sola riga o nidificati. I commenti inseriti con -- sono delimitati dal carattere di nuova riga. I commenti possono essere di qualsiasi lunghezza. Nella tabella seguente sono elencati i tasti di scelta rapida che è possibile utilizzare per impostare o meno il testo come commento.  
  
|Azione|Standard|  
|------------|--------------|  
|Impostare il testo selezionato come commento|CTRL+K, CTRL+C|  
|Rimuovere il commento dal testo selezionato|CTRL+K, CTRL + U|  
  
 Per altre informazioni sui tasti di scelta rapida, vedere [Tasti di scelta rapida di SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
 Per commenti su più righe, vedere [Barra asterisco &#40;blocco di commento&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
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
 [Elementi del linguaggio per il controllo di flusso &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  
