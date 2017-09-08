---
title: DROP SCHEMA (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SCHEMA
- DROP_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting schemas
- schemas [SQL Server], removing
- DROP SCHEMA statement
- dropping schemas
- removing schemas
ms.assetid: 874aa29e-c8ad-41e4-a672-900fdc58f1f6
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 584aea443e3263f44367ede24d7a59b8564e92c1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-schema-transact-sql"></a>DROP SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove uno schema dal database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP SCHEMA  [ IF EXISTS ] schema_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP SCHEMA schema_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale lo schema solo se esiste già.  
  
 *schema_name*  
 Nome con il quale è noto lo schema all'interno del database.  
  
## <a name="remarks"></a>Osservazioni  
 Lo schema da rimuovere non deve contenere oggetti, in caso contrario l'istruzione DROP avrà esito negativo.  
  
 Informazioni sugli schemi sono visibili nella [Schemas](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md) vista del catalogo.  
  
 **Attenzione**[!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per lo schema o l'autorizzazione ALTER ANY SCHEMA per il database.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente inizia con una singola istruzione `CREATE SCHEMA`. Tale istruzione crea lo schema `Sprockets` di proprietà di `Krishna` e la tabella `Sprockets.NineProngs`, quindi concede l'autorizzazione `SELECT` ad `Anibal` e nega l'autorizzazione `SELECT` a `Hung-Fu`.  
  
```  
CREATE SCHEMA Sprockets AUTHORIZATION Krishna   
    CREATE TABLE NineProngs (source int, cost int, partnumber int)  
    GRANT SELECT TO Anibal   
    DENY SELECT TO Hung-Fu;  
GO  
```  
  
 Le istruzioni seguenti rimuovono lo schema. Si noti che è prima necessario rimuovere la tabella contenuta nello schema.  
  
```  
DROP TABLE Sprockets.NineProngs;  
DROP SCHEMA Sprockets;  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE dello SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [L'autorizzazione ALTER SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/alter-schema-transact-sql.md)   
 [DROP SCHEMA (Transact-SQL)](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  

