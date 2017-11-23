---
title: SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9660aa9492b25c106f1ee0bbe7c8fb9d2ed061ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="set-concatnullyieldsnull-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Determina se i risultati della concatenazione di valori Null vengono gestiti come valori Null o valori di stringa vuota.  
  
> [!IMPORTANT]  
>  In una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'opzione CONCAT_NULL_YIELDS_NULL sarà sempre impostata su ON e qualsiasi applicazione che la imposta in modo esplicito su OFF restituirà un errore. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET CONCAT_NULL_YIELDS_NULL è impostata su ON, la concatenazione di un valore Null con una stringa restituisce NULL. Ad esempio, `SELECT 'abc' + NULL` restituisce `NULL`. Quando l'opzione SET CONCAT_NULL_YIELDS_NULL è impostata su OFF, la concatenazione di un valore Null con una stringa restituisce la stringa stessa (il valore Null viene considerato una stringa vuota). Ad esempio, `SELECT 'abc' + NULL` restituisce `abc`.  
  
 Se l'opzione SET CONCAT_NULL_YIELDS_NULL viene omesso, l'impostazione del **CONCAT_NULL_YIELDS_NULL** si applica l'opzione di database.  
  
> [!NOTE]  
>  L'impostazione dell'opzione SET CONCAT_NULL_YIELDS_NULL è uguale all'impostazione di CONCAT_NULL_YIELDS_NULL di ALTER DATABASE.  
  
 L'opzione SET CONCAT_NULL_YIELDS_NULL viene impostata in fase di esecuzione, non in fase di analisi.  
  
 È necessario che l'opzione SET CONCAT_NULL_YIELDS_NULL sia impostata su ON durante la creazione o la modifica di indici in colonne calcolate o viste indicizzate. Se l'opzione SET CONCAT_NULL_YIELDS_NULL è impostata su OFF, qualsiasi istruzione CREATE, UPDATE, INSERT e DELETE eseguita in tabelle con indici su colonne calcolate o viste indicizzate avrà esito negativo. Per ulteriori informazioni sulle impostazioni dell'opzione SET necessarie con viste indicizzate e indici in colonne calcolate, vedere "Considerazioni quando si usa delle istruzioni SET" in [istruzioni SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 Quando l'opzione CONCAT_NULL_YIELDS_NULL è impostata su OFF, la concatenazione delle stringhe in più server non può verificarsi.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @CONCAT_NULL_YIELDS_NULL VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_NULL_YIELDS_NULL = 'ON';  
SELECT @CONCAT_NULL_YIELDS_NULL AS CONCAT_NULL_YIELDS_NULL;  
  
```  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di entrambe le impostazioni `SET CONCAT_NULL_YIELDS_NULL`.  
  
```  
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
