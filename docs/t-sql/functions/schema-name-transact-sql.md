---
title: SCHEMA_NAME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e507e5a406cb78645489adbab13d16cf513b2448
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il nome dello schema associato a un ID di schema.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>Argomenti  
  
|Nome|Definizione|  
|----------|----------------|  
|*schema_id*|ID dello schema. *schema_id* è un **int**. Se *schema_id* non è definito, SCHEMA_NAME restituirà il nome dello schema predefinito del chiamante.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **sysname**  
  
 Restituisce NULL quando *schema_id* non è un ID valido.  
  
## <a name="remarks"></a>Osservazioni  
 SCHEMA_NAME restituisce i nomi degli schemi di sistema e degli schemi definiti dall'utente. SCHEMA_NAME può essere chiamato in un elenco di selezione, in una clausola WHERE e dovunque è consentita un'espressione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. Visualizzazione del nome dello schema predefinito del chiamante  
  
```  
SELECT SCHEMA_NAME();  
GO  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. Visualizzazione del nome di uno schema tramite l'utilizzo di un ID  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SCHEMA_NAME(5);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-name-of-the-default-schema-of-the-caller"></a>C. Visualizzazione del nome dello schema predefinito del chiamante  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="d-returning-the-name-of-a-schema-by-using-an-id"></a>D. Visualizzazione del nome di uno schema tramite l'utilizzo di un ID  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID &#40; Transact-SQL &#41;](../../t-sql/functions/schema-id-transact-sql.md)   
 [Schemas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


