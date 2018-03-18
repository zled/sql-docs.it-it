---
title: Sinonimi dei tipi di dati (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07b4ada74ee54bf1c892e0938dd794e17ea4c0cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-synonyms-transact-sql"></a>Sinonimi dei tipi di dati (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

I sinonimi dei tipi di dati sono disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per compatibilità con ISO. Nella tabella seguente vengono elencati i sinonimi e i tipi di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui viene eseguito il mapping.
  
|Sinonimo|Tipo di dati di sistema di SQL Server|  
|---|---|
|**Binary varying**|**varbinary**|  
|**char varying**|**varchar**|  
|**character**|**char**|  
|**character**|**char(1)**|  
|**character(** *n* **)**|**char(n)**|  
|**character varying(** *n* **)**|**varchar(n)**|  
|**Dec**|**decimal**|  
|**Double precision**|**float**|  
|**float**[**(***n***)**] per *n* = 1-7|**real**|  
|**float**[**(***n***)**] per *n* = 8-15|**float**|  
|**integer**|**int**|  
|**national character(** *n* **)**|**nchar(n)**|  
|**national char(** *n* **)**|**nchar(n)**|  
|**national character varying(** *n* **)**|**nvarchar(n)**|  
|**national char varying(** *n* **)**|**nvarchar(n)**|  
|**national text**|**ntext**|  
|**timestamp**|rowversion|  
  
I sinonimi dei tipi di dati possono essere usati in alternativa al nome del tipo di dati di base corrispondente in istruzioni DDL (Data Definition Language), come CREATE TABLE, CREATE PROCEDURE o DECLARE *@variable*. I sinonimi non sono tuttavia visibili dopo la creazione dell'oggetto. In fase di creazione infatti all'oggetto viene assegnato il tipo di dati di base associato al sinonimo e la presenza del sinonimo nell'istruzione con cui è stato creato l'oggetto non viene registrata.
  
Agli oggetti che derivano dall'oggetto originale, ad esempio colonne del set di risultati o espressioni, viene assegnato il tipo di dati di base. Le successive funzioni per i metadati eseguite sull'oggetto originale e sugli oggetti derivati visualizzano il tipo di dati di base, non il sinonimo. Questo comportamento si verifica con le operazioni sui metadati, ad esempio **sp_help** e altre stored procedure di sistema, le viste degli schemi delle informazioni o le varie operazioni sui metadati API per l'accesso ai dati che visualizzano i tipi di dati della tabella o le colonne del set di risultati.
  
È possibile, ad esempio, creare una tabella specificando `national character varying`:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
Alla colonna `VarCharCol` viene in effetti assegnato il tipo di dati **nvarchar(10)**. Le successive funzioni per i metadati visualizzeranno la colonna come colonna di tipo **nvarchar(10)**. Le funzioni per i metadati non visualizzano mai le colonne come colonne di tipo **national character varying(10)**.
  
## <a name="see-also"></a>Vedere anche
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
