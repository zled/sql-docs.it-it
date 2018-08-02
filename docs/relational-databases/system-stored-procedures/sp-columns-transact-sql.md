---
title: sp_columns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 10/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_columns_TSQL
- sp_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns
ms.assetid: 2dec79cf-2baf-4c0f-8cbb-afb1a8654e1e
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 784811775a3364544e67d6591de203b091ab5402
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240471"
---
# <a name="spcolumns-transact-sql"></a>sp_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Vengono restituite le informazioni di colonna per gli oggetti specificati per cui è possibile eseguire una query nell'ambiente corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_columns [ @table_name = ] object  
     [ , [ @table_owner = ] owner ]   
     [ , [ @table_qualifier = ] qualifier ]   
     [ , [ @column_name = ] column ]   
     [ , [ @ODBCVer = ] ODBCVer ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@table_name=**] *oggetto*  
 Nome dell'oggetto utilizzato per restituire informazioni sul catalogo. *oggetto* può essere una tabella, vista o un altro oggetto che dispone di colonne, ad esempio le funzioni con valori di tabella. *oggetto* viene **nvarchar (384)**, non prevede alcun valore predefinito. La ricerca con caratteri jolly è supportata.  
  
 [ **@table_owner****=**] *owner*  
 Proprietario dell'oggetto utilizzato per restituire informazioni sul catalogo. *proprietario* viene **nvarchar (384)**, con un valore predefinito è NULL. La ricerca con caratteri jolly è supportata. Se *proprietario* viene omesso, si applicano le regole di visibilità oggetto predefinite del sistema DBMS sottostante.  
  
 Se l'utente corrente è il proprietario di un oggetto con il nome specificato, vengono restituite le colonne di tale oggetto. Se *proprietario* viene omesso e l'utente corrente non dispone di un oggetto con l'oggetto specificato *oggetto*, **sp_columns** Cerca un oggetto con l'oggetto specificato  *oggetto* il proprietario del database. Se viene individuato, vengono restituite le colonne di tale oggetto.  
  
 [  **@table_qualifier* * * =**] *qualificatore*  
 Nome del qualificatore dell'oggetto. *qualificatore* viene **sysname**, con un valore predefinito è NULL. Vari prodotti DBMS supportano nomi per gli oggetti in tre parti (*qualificatore ***.*** proprietario ***.*** nome*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. In alcuni prodotti rappresenta il nome del server dell'ambiente di database dell'oggetto.  
  
 [  **@column_name=**] *colonna*  
 Colonna singola utilizzata quando si desidera recuperare una sola colonna di informazioni di catalogo. *colonna* viene **nvarchar (384)**, con un valore predefinito è NULL. Se *colonna* viene omesso, vengono restituite tutte le colonne. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], *colonna* rappresenta il nome di colonna elencato nella **syscolumns** tabella. La ricerca con caratteri jolly è supportata. Per ottenere la massima interoperabilità, è consigliabile che nel client di gateway siano utilizzati solo i caratteri jolly standard di SQL-92, ovvero i caratteri % e _.  
  
 [ **@ODBCVer=**] *ODBCVer*  
 Versione di ODBC utilizzata. *ODBCVer* viene **int**, con un valore predefinito è 2. che indica ODBC versione 2. I valori validi sono 2 e 3. Per le differenze di comportamento tra le versioni 2 e 3, vedere ODBC **SQLColumns** specifica.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
 Il **sp_columns** è equivalente alla stored procedure di catalogo **SQLColumns** in ODBC. I risultati restituiti vengono ordinati in base **TABLE_QUALIFIER**, **TABLE_OWNER**, e **TABLE_NAME**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Nome del qualificatore dell'oggetto. Questo campo può essere NULL.|  
|**TABLE_OWNER**|**sysname**|Nome del proprietario dell'oggetto. Questo campo restituisce sempre un valore.|  
|**TABLE_NAME**|**sysname**|Nome dell'oggetto. Questo campo restituisce sempre un valore.|  
|**COLUMN_NAME**|**sysname**|Nome della colonna, per ogni colonna del **TABLE_NAME** restituito. Questo campo restituisce sempre un valore.|  
|**DATA_TYPE**|**smallint**|Codice integer per il tipo di dati ODBC. Se si tratta di un tipo di dati di cui non è possibile eseguire il mapping a un tipo ODBC, il valore è NULL. Cui viene restituito il nome del tipo di dati nativi di **TYPE_NAME** colonna.|  
|**TYPE_NAME**|**sysname**|Stringa che rappresenta un tipo di dati. Il DBMS sottostante utilizza questo nome del tipo di dati.|  
|**PRECISION**|**int**|Numero di cifre significative. Il valore restituito per il **precisione** colonna è in base 10.|  
|**LENGTH**|**int**|Dimensioni di trasferimento dei dati. <sup>1</sup>|  
|**SCALA**|**smallint**|Numero di cifre a destra del separatore decimale.|  
|**RADIX**|**smallint**|Base per i tipi di dati numerici.|  
|**AMMETTE VALORI NULL**|**smallint**|Specifica se i valori Null sono supportati.<br /><br /> 1 = I valori Null sono supportati.<br /><br /> 0 = I valori Null non sono supportati (NOT NULL).|  
|**SEZIONE OSSERVAZIONI**|**varchar(254)**|In questo campo viene sempre restituito NULL.|  
|**COLUMN_DEF**|**nvarchar(4000)**|Valore predefinito della colonna.|  
|**SQL_DATA_TYPE**|**smallint**|Valore del tipo di dati SQL visualizzato nel campo TYPE del descrittore. Questa colonna corrisponde alla **DATA_TYPE** colonna, tranne che per il **datetime** e SQL-92 **intervallo** tipi di dati. In questa colonna viene sempre restituito un valore.|  
|**SQL_DATETIME_SUB**|**smallint**|Codice di sottotipo per **datetime** e SQL-92 **intervallo** tipi di dati. Per gli altri tipi di dati in questa colonna viene restituito NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Lunghezza massima, espressa in byte, di una colonna di tipo carattere o integer. Per tutti gli altri tipi di dati in questa colonna viene restituito NULL.|  
|**ORDINAL_POSITION**|**int**|Posizione ordinale della colonna nell'oggetto. La prima colonna nell'oggetto è 1. In questa colonna viene sempre restituito un valore.|  
|**IS_NULLABLE**|**varchar(254)**|Supporto di valori Null della colonna dell'oggetto. Per determinare il supporto di valori Null vengono seguite le regole ISO. In un sistema DBMS conforme a ISO SQL non vengono restituite stringhe vuote.<br /><br /> YES = La colonna ammette valori Null.<br /><br /> NO = La colonna non ammette valori Null.<br /><br /> Quando non è noto se i valori Null sono supportati, in questa colonna viene restituita una stringa di lunghezza zero.<br /><br /> Il valore restituito per questa colonna è diverso dal valore restituito per il **NULLABLE** colonna.|  
|**SS_DATA_TYPE**|**tinyint**|Tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato dalle stored procedure estese. Per altre informazioni, vedere [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
  
 <sup>1</sup> per altre informazioni, vedere la documentazione di Microsoft ODBC.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede le autorizzazioni SELECT e VIEW DEFINITION per lo schema.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_columns** soddisfa i requisiti per gli identificatori delimitati. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulle colonne della tabella specificata.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_columns @table_name = N'Department',  
   @table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente vengono restituite informazioni sulle colonne della tabella specificata.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_columns @table_name = N'DimEmployee',  
   @table_owner = N'dbo';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-transact-sql.md)   
 [Stored procedure di catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  


