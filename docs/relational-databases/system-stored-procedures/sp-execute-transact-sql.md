---
title: sp_execute (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_execute
- sp_cursor_execute_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_execute
ms.assetid: 2009acd3-0d92-435a-a8fb-057e50dc7146
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2b40bd51a730cf902068aa0ba8bc40411f002f3b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spexecute-transact-sql"></a>sp_execute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Esegue una [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione utilizzando un handle specificato e il valore del parametro facoltativo. è possibile richiamare sp_execute specificando ID = 12 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_execute handle OUTPUT  
    [,bound_param  ]  [,...n ]  ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *handle*  
 È il *gestire* valore restituito da sp_prepare. *gestire* è un parametro obbligatorio che richiede **int** valore di input.  
  
 *bound_param*  
 Indica l'utilizzo di parametri aggiuntivi. *bound_param* è un parametro obbligatorio che richiede valori di input di qualsiasi tipo di dati per definire i parametri aggiuntivi per la procedura.  
  
> [!NOTE]  
>  *bound_param* deve corrispondere alle dichiarazioni di sp_prepare*params* valore e può essere nel formato  *@name = valore* o *valore*.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)  
  
  
