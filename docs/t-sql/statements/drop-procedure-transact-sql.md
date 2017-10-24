---
title: DROP PROCEDURE (Transact-SQL) | Documenti Microsoft
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
- DROP PROCEDURE
- DROP_PROCEDURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing stored procedures
- dropping procedure groups
- deleting stored procedures
- deleting procedure groups
- DROP PROCEDURE statement
- dropping stored procedures
- stored procedures [SQL Server], removing
- removing procedure groups
ms.assetid: 1c2d7235-7b9b-4336-8f17-429e7d82c2c3
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b386dfca28622eb95eec500d909aa7190d081493
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-procedure-transact-sql"></a>DROP PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove una o più stored procedure o gruppi di stored procedure dal database corrente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP { PROC | PROCEDURE } [ IF EXISTS ] { [ schema_name. ] procedure } [ ,...n ]  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP { PROC | PROCEDURE } { [ schema_name. ] procedure_name }  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale la procedura solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la procedura. Non è possibile specificare un nome di server o di database.  
  
 *procedure*  
 Nome della stored procedure o del gruppo di stored procedure da rimuovere. Non è possibile eliminare singole procedure all'interno di un gruppo di procedure numerate. In questo caso, viene eliminato l'intero gruppo.  
  
## <a name="best-practices"></a>Procedure consigliate  
 Prima di rimuovere qualsiasi stored procedure, verificare la presenza di eventuali oggetti dipendenti e modificare tali oggetti di conseguenza, L'eliminazione di una stored procedure può causare errori in oggetti e script dipendenti, se tali oggetti non vengono aggiornati. Per ulteriori informazioni, vedere [visualizzare le dipendenze di una Stored Procedure](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)  
  
## <a name="metadata"></a>Metadati  
 Per visualizzare un elenco di procedure esistenti, eseguire una query di **Sys. Objects** vista del catalogo. Per visualizzare la definizione della routine, eseguire una query di **Sys. sql_modules** vista del catalogo.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 Richiede **controllo** autorizzazione per la procedura, o **ALTER** l'autorizzazione per lo schema a cui appartiene la stored procedure o l'appartenenza di **db_ddladmin** ruolo predefinito del server .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si rimuove la stored procedure `dbo.uspMyProc` nel database corrente.  
  
```  
DROP PROCEDURE dbo.uspMyProc;  
GO  
```  
  
 Nell'esempio seguente vengono rimosse varie stored procedure dal database corrente.  
  
```  
DROP PROCEDURE dbo.uspGetSalesbyMonth, dbo.uspUpdateSalesQuotes, dbo.uspGetSalesByYear;  
```  
  
 L'esempio seguente rimuove il `dbo.uspMyProc` stored procedure se esiste, ma non viene generato un errore se la procedura non esiste. Questa sintassi è stata introdotta in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
DROP PROCEDURE IF EXISTS dbo.uspMyProc;  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Sys. Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Eliminare una stored procedure](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)  
  
  



