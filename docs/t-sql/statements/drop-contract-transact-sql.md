---
title: CONTRATTO DROP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_CONTRACT_TSQL
- DROP CONTRACT
dev_langs:
- TSQL
helpviewer_keywords:
- dropping contracts
- removing contracts
- deleting contracts
- contracts [Service Broker], dropping
- DROP CONTRACT statement
ms.assetid: fdd0f81e-3c22-4cdf-9416-b4977a6ac3b6
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 58c76223cf592bc90b4c9cb831f93af943e59154
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-contract-transact-sql"></a>DROP CONTRACT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un contratto esistente da un database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP CONTRACT contract_name   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *contract_name*  
 Nome del contratto da eliminare. Non è possibile specificare i nomi del server, del database e dello schema.  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile eliminare un contratto se esistono servizi o priorità di conversazione che fanno riferimento a esso.  
  
 Quando si elimina un contratto, tramite [!INCLUDE[ssSB](../../includes/sssb-md.md)] viene interrotta qualsiasi conversazione esistente che utilizza tale contratto e viene generato un errore.  
  
## <a name="permissions"></a>Permissions  
 L'autorizzazione per eliminare un contratto viene assegnata per impostazione predefinita al proprietario del contratto, ai membri del ruolo predefinito del database db_ddladmin o db_owner e ai membri del ruolo predefinito del server sysadmin.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il contratto `//Adventure-Works.com/Expenses/ExpenseSubmission` viene rimosso dal database.  
  
```  
DROP CONTRACT   
    [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [ALTER SERVICE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-transact-sql.md)   
 [Crea contratto &#40; Transact-SQL &#41;](../../t-sql/statements/create-contract-transact-sql.md)   
 [DROP BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [ELIMINARE servizio &#40; Transact-SQL &#41;](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
