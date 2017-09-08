---
title: DROP ROUTE (Transact-SQL) | Documenti Microsoft
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
- DROP ROUTE
- DROP_ROUTE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping routes
- DROP ROUTE statement
- deleting routes
- routes [Service Broker], removing
- removing routes
ms.assetid: d8fab0bc-d54a-46ca-9437-552db7477d40
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 037753a9dc22077b2b36158458c1ea98bbe7e0f5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-route-transact-sql"></a>DROP ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una route e le informazioni a essa associate dalla tabella di routing del database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP ROUTE route_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *route_name*  
 Nome della route da eliminare. Non è possibile specificare i nomi del server, del database e dello schema.  
  
## <a name="remarks"></a>Osservazioni  
 La tabella di routing che archivia le route è una tabella di metadati che può essere letta tramite la vista del catalogo **Routes**. e aggiornata esclusivamente utilizzando le istruzioni CREATE ROUTE, ALTER ROUTE e DROP ROUTE.  
  
 È possibile eliminare una route indipendentemente dal fatto che sia utilizzata da eventuali conversazioni. Se, tuttavia, non esistono altre route al servizio remoto, i messaggi per tali conversazioni rimarranno nella coda di trasmissione finché non verrà creata una route al servizio remoto o fino al timeout della conversazione.  
  
## <a name="permissions"></a>Permissions  
 L'autorizzazione per la rimozione di una route viene assegnata per impostazione predefinita al proprietario della route, ai membri del ruolo predefinito del database db_ddladmin o db_owner e ai membri del ruolo predefinito del server sysadmin.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminata la route `ExpenseRoute`.  
  
```  
DROP ROUTE ExpenseRoute ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-route-transact-sql.md)   
 [CREATE ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/create-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Routes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md)  
  
  
