---
title: DROP AGGREGATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AGGREGATE_TSQL
- DROP AGGREGATE
dev_langs: TSQL
helpviewer_keywords:
- aggregate functions [SQL Server], removing
- removing user-defined functions
- dropping user-defined functions
- user-defined functions [CLR integration]
- deleting user-defined functions
- DROP AGGREGATE statement
ms.assetid: 84ffc4e7-c451-4f1f-9a67-7fc3a120e53f
caps.latest.revision: "31"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f01299f0a5db2ed47975a964104e720cb7c8c52
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove una funzione di aggregazione definita dall'utente dal database corrente. Le funzioni di aggregazione definita dall'utente vengono create utilizzando [CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale l'aggregazione solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione di aggregazione definita dall'utente.  
  
 *aggregate_name*  
 Nome della funzione di aggregazione definita dall'utente che si desidera eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione DROP AGGREGATE non viene eseguita se sono presenti viste, funzioni o stored procedure create in base all'associazione a schemi che fanno riferimento alla funzione di aggregazione definita dall'utente che si desidera eliminare.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire l'istruzione DROP AGGREGATE, è necessario disporre almeno dell'autorizzazione ALTER per lo schema al quale appartiene la funzione di aggregazione definita dall'utente oppure dell'autorizzazione CONTROL per la funzione di aggregazione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la funzione di aggregazione `Concatenate` viene eliminata.  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [Creare funzioni di aggregazione definite dall'utente](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  
