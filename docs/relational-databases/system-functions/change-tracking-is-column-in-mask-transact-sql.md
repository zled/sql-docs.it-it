---
title: CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 31a10fd7cb677e0d86ba246f5272e66f1dafd6be
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Interpreta il valore SYS_CHANGE_COLUMNS restituito dalla funzione CHANGETABLE (CHANGES...). Consente a un'applicazione di determinare se la colonna specificata è inclusa nei valori restituiti per SYS_CHANGE_COLUMNS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Argomenti  
 *column_id*  
 ID della colonna sottoposta a verifica. La colonna ID può essere ottenuto utilizzando il [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) (funzione).  
  
 *change_columns*  
 I dati binari dalla colonna SYS_CHANGE_COLUMNS del [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) dati.  
  
## <a name="return-type"></a>Tipo restituito  
 **bit**  
  
## <a name="return-values"></a>Valori restituiti  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK restituisce i valori seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|La colonna specificata non è nel *change_columns* elenco.|  
|1|La colonna specificata è la *change_columns* elenco.|  
  
## <a name="remarks"></a>Osservazioni  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK non esegue alcun controllo per convalidare il *column_id* valore o che il *change_columns* parametro è stato ottenuto la tabella da cui il  *column_id* è stato ottenuto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene determinato se è stata aggiornata la colonna `Salary` della tabella `Employees`. Il `COLUMNPROPERTY` l'ID della funzione di `Salary` colonna. La variabile locale `@change_columns` deve essere impostata sui risultati di una query utilizzando CHANGETABLE come origine dati.  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di rilevamento delle modifiche &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
