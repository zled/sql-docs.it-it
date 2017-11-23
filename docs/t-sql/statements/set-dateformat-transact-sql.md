---
title: SET DATEFORMAT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
caps.latest.revision: "49"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3b1e233508eaedab627b57a3ce6938b90a9e196d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Imposta l'ordine delle parti della data mese, giorno e anno per l'interpretazione **data**, **smalldatetime**, **datetime**, **datetime2** e **datetimeoffset** stringhe di caratteri.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>Argomenti  
 *formato* | **@***format_var*  
 Ordine delle parti della data. I parametri validi sono **mdy**, **dmy**, **AMG**, **agm**, **myd**, e **dym**. Può essere un valore Unicode o un valore DBCS (Double Byte Character Set) convertito in Unicode. L'impostazione predefinita Valore predefinito in lingua inglese è **mdy**. Per il valore predefinito DATEFORMAT di tutte le lingue supportate, vedere [sp_helplanguage &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di DATEFORMAT **agm** non è supportato per **data**, **datetime2** e **datetimeoffset** tipi di dati.  
  
 L'effetto dell'impostazione DATEFORMAT sull'interpretazione di stringhe di caratteri potrebbe essere diverso per **datetime** e **smalldatetime** più i valori del parametro **data**, **datetime2** e **datetimeoffset** valori, a seconda del formato di stringa. Questa impostazione influisce sull'interpretazione di stringhe di caratteri nel momento in cui queste vengono convertite in valori di data per l'archiviazione nel database. Non influisce sulla visualizzazione di valori del tipo di dati date archiviati nel database o sul formato di archiviazione di questi.  
  
 Alcuni formati delle stringhe di caratteri, ad esempio ISO 8601, sono interpretati indipendentemente dall'impostazione DATEFORMAT.  
  
 L'opzione SET DATEFORMAT viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Opzione SET DATEFORMAT ignora la data implicita formattare l'impostazione di [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente sono utilizzate diverse stringhe relative alla data come input in sessioni con la stessa impostazione `DATEFORMAT`.  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

