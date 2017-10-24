---
title: Il tipo di rilascio (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4187c6bff08e5502f5edc6acd8d82334684a68d4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove un tipo di dati alias o un tipo CLR definito dall'utente dal database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale del tipo solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene il tipo di dati alias o il tipo definito dall'utente.  
  
 *TYPE_NAME*  
 Nome del tipo di dati alias o del tipo definito dall'utente che si desidera rimuovere.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione DROP TYPE non verrà eseguita nei casi seguenti:  
  
-   Nel database sono presenti tabelle che contengono colonne con il tipo di dati alias o il tipo definito dall'utente. Informazioni sull'alias o le colonne di tipo definito dall'utente possono essere ottenute eseguendo una query di [Columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) o [column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md) viste del catalogo.  
  
-   Sono presenti colonne calcolate, vincoli CHECK e viste e funzioni associate a schema le cui definizioni fanno riferimento al tipo di dati alias o definito dall'utente. Informazioni su tali riferimenti possono essere ottenute eseguendo una query di [Sys. sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) vista del catalogo.  
  
-   Nel database sono stati creati trigger, funzioni o stored procedure e tali routine utilizzano variabili e parametri con tipo di dati alias o definito dall'utente. Informazioni sui parametri di tipo definito dall'utente o alias possono essere ottenute eseguendo una query di [Sys. Parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) o [parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md) viste del catalogo.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione CONTROL per su *type_name* o l'autorizzazione ALTER per *schema_name*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si presuppone che il tipo denominato `ssn` sia già stato creato nel database corrente.  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

