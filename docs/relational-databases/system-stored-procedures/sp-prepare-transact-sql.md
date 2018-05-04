---
title: sp_prepare (Transact SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 38093990d6b011113ca63764cb43a08c664c7fe5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Prepara una parametri [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione e restituisce un'istruzione *gestire* per l'esecuzione. è possibile richiamare sp_prepare specificando ID = 11 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un articolo](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Argomenti  
 *Handle*  
 SQL Server generato da *handle preparato* identificatore. *gestire* è un parametro obbligatorio con un **int** valore restituito.  
  
 *Params*  
 Identifica le istruzioni con parametri. Il *params* definizione delle variabili viene sostituita per i marcatori di parametro nell'istruzione. *params* è un parametro obbligatorio che richiede un **ntext**, **nchar**, o **nvarchar** valore di input. Immettere un valore NULL se l'istruzione non è con parametri.  
  
 *stmt*  
 Definisce il set di risultati del cursore. Il *stmt* parametro è obbligatorio e richiede un **ntext**, **nchar**, o **nvarchar** valore di input.  
  
 *options*  
 Parametro facoltativo tramite cui viene restituita una descrizione delle colonne dei set di risultati del cursore. *opzioni* richiede il valore di input int seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene preparata ed eseguita un'istruzione semplice.  
  
```  
Declare @P1 int;  
Exec sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
Exec sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```  

  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

