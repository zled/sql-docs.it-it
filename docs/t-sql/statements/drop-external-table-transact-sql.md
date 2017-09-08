---
title: ELIMINARE la tabella esterna (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e560c5341abd440f641a988751a6ca2875b9bbb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-table-transact-sql"></a>ELIMINARE la tabella esterna (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Rimuove una tabella esterna PolyBase da. Questa operazione non elimina i dati esterni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DROP EXTERNAL TABLE [ database_name . [schema_name ] . | schema_name . ] table_name   
[;]  
```  
  

## <a name="arguments"></a>Argomenti  
 [ *database_name* . [*schema_name*]. | *schema_name* . ] *table_name*  
 Il nome di uno di tre parti della tabella esterna da rimuovere. Il nome di tabella può includere facoltativamente, lo schema o il database e lo schema.  
  
## <a name="permissions"></a>Permissions  
  
-   Richiede **ALTER** autorizzazione per lo schema a cui appartiene la tabella.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Eliminazione di una tabella esterna rimuove tutti i metadati relativi alle tabelle. Non elimina i dati esterni.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-basic-syntax"></a>A. Utilizzando la sintassi di base  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>B. Eliminazione di una tabella esterna dal database corrente  
 L'esempio seguente rimuove il `ProductVendor1` tabella, i dati, indici e le visualizzazioni dipendenti dal database corrente.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>C. Eliminazione di una tabella da un altro database  
 Nell'esempio seguente viene eliminata la tabella `SalesPerson` nel database `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-basic-syntax"></a>D. Utilizzando la sintassi di base  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="e-dropping-an-external-table-from-the-current-database"></a>E. Eliminazione di una tabella esterna dal database corrente  
 L'esempio seguente rimuove il `ProductVendor1` tabella, i dati, indici e le visualizzazioni dipendenti dal database corrente.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="f-dropping-a-table-from-another-database"></a>F. Eliminazione di una tabella da un altro database  
 Nell'esempio seguente viene eliminata la tabella `SalesPerson` nel database `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  


