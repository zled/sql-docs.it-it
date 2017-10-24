---
title: TYPE_NAME (Transact-SQL) | Documenti Microsoft
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
- TYPE_NAME_TSQL
- TYPE_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- names [SQL Server], data types
- unqualified type names
- type names [SQL Server]
- data types [SQL Server], names
- TYPE_NAME function
ms.assetid: e4075a2e-5f70-440f-986b-9ec8434e07c1
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3d60bec3a21bb5b1127b0f18977d3485979f20b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="typename-transact-sql"></a>TYPE_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il nome non qualificato di un tipo con l'ID specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
TYPE_NAME ( type_id )   
```  
  
## <a name="arguments"></a>Argomenti  
 *type_id*  
 ID del tipo che verrà utilizzato. *type_id* è un **int**, e può fare riferimento a un tipo in qualsiasi schema a cui il chiamante dispone dell'autorizzazione di accesso.  
  
## <a name="return-types"></a>Tipi restituiti  
 **sysname**  
  
## <a name="exceptions"></a>Eccezioni  
 Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come TYPE_NAME possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Osservazioni  
 TYPE_NAME restituisce NULL quando *type_id* non è valido o quando il chiamante non dispone di autorizzazioni sufficienti per fare riferimento al tipo.  
  
 La funzione TYPE_NAME può essere utilizzata sia con tipi di dati di sistema che con tipi di dati definiti dall'utente. Il nome restituito è sempre non qualificato, indipendentemente dallo schema in cui il tipo è contenuto, Ciò significa che il nome non è il *schema***.** biz:,  
  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione. Per ulteriori informazioni, vedere [espressioni &#40; Transact-SQL &#41; ](../../t-sql/language-elements/expressions-transact-sql.md) e [in &#40; Transact-SQL &#41; ](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti il nome dell'oggetto, il nome della colonna e il nome del tipo per ogni colonna della tabella `Vendor` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT o.name AS obj_name, c.name AS col_name,  
       TYPE_NAME(c.user_type_id) AS type_name  
FROM sys.objects AS o   
JOIN sys.columns AS c  ON o.object_id = c.object_id  
WHERE o.name = 'Vendor'  
ORDER BY col_name;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
obj_name        col_name                  type_name
--------------- ------------------------ --------------
Vendor          AccountNumber            AccountNumber
Vendor          ActiveFlag               Flag
Vendor          BusinessEntityID         int
Vendor          CreditRating             tinyint
Vendor          ModifiedDate             datetime
Vendor          Name                     Name
Vendor          PreferredVendorStatus    Flag
Vendor          PurchasingWebServiceURL  nvarchar

(8 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente viene restituito il `TYPE ID` per il tipo di dati con id `1`.  
  
```  
SELECT TYPE_NAME(36) AS Type36, TYPE_NAME(239) AS Type239;  
GO  
```  
  
 Per un elenco di tipi, eseguire una query Sys. Types.  
  
```  
SELECT * FROM sys.types;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [TYPE_ID &#40; Transact-SQL &#41;](../../t-sql/functions/type-id-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
  
  


