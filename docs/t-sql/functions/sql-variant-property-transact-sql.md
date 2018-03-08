---
title: SQL_VARIANT_PROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5947528f4e8959de1b8b4ee3679d4e3e058476d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sqlvariantproperty-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il tipo di dati di base e altre informazioni su un **sql_variant** valore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È un'espressione di tipo **sql_variant**.  
  
 *proprietà*  
 Contiene il nome del **sql_variant** proprietà per il quale sono necessario fornire informazioni. *proprietà* è **varchar (**128**)**, e può essere uno dei valori seguenti:  
  
|Valore|Description|Tipo di base di sql_variant restituito|  
|-----------|-----------------|----------------------------------------|  
|**BaseType**|Tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio:<br /><br /> **bigint**<br /><br /> **binary**<br /><br /> **char**<br /><br /> **data**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = Input non valido.|  
|**Precisione**|Numero di cifre del tipo di dati numerici di base:<br /><br /> **DateTime** = 23<br /><br /> **smalldatetime** = 16<br /><br /> **float** = 53<br /><br /> **reale** = 24<br /><br /> **decimale** (p, s) e **numerico** (p, s) = p<br /><br /> **Money** = 19<br /><br /> **smallmoney** = 10<br /><br /> **bigint** = 19<br /><br /> **int** = 10<br /><br /> **smallint** = 5<br /><br /> **tinyint** = 3<br /><br /> **bit** = 1<br /><br /> Tutti gli altri tipi = 0|**int**<br /><br /> NULL = Input non valido.|  
|**Scala**|Numero di cifre a destra del separatore decimale con tipo di base numerico:<br /><br /> **decimale** (p, s) e **numerico** (p, s) = s<br /><br /> **Money** e **smallmoney** = 4<br /><br /> **DateTime** = 3<br /><br /> Tutti gli altri tipi = 0|**int**<br /><br /> NULL = Input non valido.|  
|**TotalBytes**|Numero di byte necessari per l'archiviazione sia dei metadati che dei dati del valore. Tali informazioni saranno utili per verificare le dimensioni massime dei dati in un **sql_variant** colonna. Se il valore è maggiore di 900, la creazione dell'indice ha esito negativo.|**int**<br /><br /> NULL = Input non valido.|  
|**Confronto**|Rappresenta le regole di confronto dello specifico **sql_variant** valore.|**sysname**<br /><br /> NULL = Input non valido.|  
|**MaxLength**|Lunghezza massima del tipo di dati espressa in byte. Ad esempio, **MaxLength** di **nvarchar (**50**)** è 100, **MaxLength** di **int** è 4.|**int**<br /><br /> NULL = Input non valido.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **sql_variant**  
  
## <a name="examples"></a>Esempi  
### <a name="a-using-a-sqlvariant-in-a-table"></a>A. Utilizzo di tipo sql_variant in una tabella  
 L'esempio seguente recupera `SQL_VARIANT_PROPERTY` informazioni di `colA` valore `46279.1` in `colB`  = `1689`, dato che `tableA` è `colA` che è di tipo `sql_variant` e `colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Si noti che ognuno di questi tre valori è un **sql_variant**.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>B. Utilizzo di tipo sql_variant come una variabile   
 L'esempio seguente recupera `SQL_VARIANT_PROPERTY` informazioni su una variabile denominata @v1.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  

