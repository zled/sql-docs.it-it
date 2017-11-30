---
title: Sys.dm db_uncontained_entities (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_uncontained_entities
- dm_db_uncontained_entities_TSQL
- sys.dm_db_uncontained_entities_TSQL
- dm_db_uncontained_entities
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_uncontained_entities dynamic management view
ms.assetid: f417efd4-8c71-4f81-bc9c-af13bb4b88ad
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f2786493aeb75402eae5d7e91458e97436f3435a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmdbuncontainedentities-transact-sql"></a>sys.dm_db_uncontained_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Mostra qualsiasi oggetto non contenuto utilizzato nel database. Gli oggetti non contenuti sono oggetti che superano il limite del database in un database indipendente. Questa vista è accessibile sia da un database indipendente che da un database non indipendente. Se db_uncontained_entities è vuoto, il database non utilizza entità non contenute.  
  
 Se un modulo supera il limite del database più di una volta, viene riportato solo il primo superamento individuato.  
  
||||  
|-|-|-|  
|**Nome colonna**|**Tipo**|**Description**|  
|*classe*|**int**|1 = Oggetto o colonna (include moduli, XP, viste, sinonimi e tabelle).<br /><br /> 4 = Entità di database<br /><br /> 5 = Assembly<br /><br /> 6 = Tipo<br /><br /> 7 = Indice (indice full-text)<br /><br /> 12 = Trigger DDL database<br /><br /> 19 = Route<br /><br /> 30 = Specifica del controllo|  
|*class_desc*|**nvarchar(120)**|Descrizione della classe dell'entità. Uno dei valori seguenti in base alla classe:<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **DATABASE_PRINCIPAL**<br /><br /> **ASSEMBLY**<br /><br /> **TYPE**<br /><br /> **INDEX**<br /><br /> **DATABASE_DDL_TRIGGER**<br /><br /> **ROUTE**<br /><br /> **AUDIT_SPECIFICATION**|  
|*major_id*|**int**|ID dell'entità.<br /><br /> Se *classe* = 1, allora object_id<br /><br /> Se *classe* = 4, quindi principal_id.<br /><br /> Se *classe* = 5, quindi assembly_id.<br /><br /> Se *classe* = 6, quindi user_type_id.<br /><br /> Se *classe* = 7, quindi index_id.<br /><br /> Se *classe* = 12, quindi OBJECT_ID.<br /><br /> Se *classe* = 19, Route_ID.<br /><br /> Se *classe* = 30, quindi sys. database_audit_specifications.databse_specification_id.|  
|*statement_line_number*|**int**|Se la classe è un modulo, restituisce il numero di riga in cui si trova l'utilizzo non contenuto.  In caso contrario, il valore è Null.|  
|*statement_ offset_begin*|**int**|Se la classe è un modulo, indica la posizione iniziale dell'utilizzo non contenuto partendo da 0. Il valore viene espresso in byte. In caso contrario, il valore restituito è Null.|  
|*statement_ offset_end*|**int**|Se la classe è un modulo, indica la posizione finale dell'utilizzo non contenuto partendo da 0. Il valore viene espresso in byte. Il valore -1 indica la fine del modulo. In caso contrario, il valore restituito è Null.|  
|*statement_type*|**nvarchar(512)**|Tipo di istruzione.|  
|*nome feature_*|**nvarchar(256)**|Restituisce il nome esterno dell'oggetto.|  
|*feature_type_name*|**nvarchar(256)**|Restituisce il tipo di funzionalità.|  
  
## <a name="remarks"></a>Osservazioni  
 Sys.dm db_uncontained_entities Mostra le entità che potenzialmente possono superare il limite del database. Restituirà le entità utente che possono utilizzare gli oggetti al di fuori del database.  
  
 I tipi di funzionalità seguenti vengono segnalati.  
  
-   Comportamento di indipendenza sconosciuto (SQL dinamico o risoluzione dei nomi posticipata)  
  
-   Comando DBCC  
  
-   Stored procedure di sistema  
  
-   Funzione scalare di sistema  
  
-   Funzione con valori di tabella di sistema  
  
-   Funzione predefinita di sistema  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 Sys.dm db_uncontained_entities restituisce solo gli oggetti per cui l'utente dispone di un tipo di autorizzazione. Per l'indipendenza del database, questa funzione deve essere utilizzata da un utente con privilegi elevati, ad esempio un membro di una valutazione completa di **sysadmin** ruolo predefinito del server o **db_owner** ruolo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una procedura denominata P1, quindi viene eseguita una query su `sys.dm_db_uncontained_entities`. Nella query viene segnalato che P1 utilizza **sys.endpoints** , che si trova all'esterno del database.  
  
```tsql  
CREATE DATABASE Test;  
GO  
  
USE Test;  
GO  
CREATE PROC P1  
AS   
SELECT * FROM sys.endpoints ;  
GO  
SELECT SO.name, UE.* FROM sys.dm_db_uncontained_entities AS UE  
LEFT JOIN sys.objects AS SO  
    ON UE.major_id = SO.object_id;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Database indipendenti](../../relational-databases/databases/contained-databases.md)  
  
  
