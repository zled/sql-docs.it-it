---
title: CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_CLEANUP_VERSION
- CHANGE_TRACKING_CLEANUP_VERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHANGE_TRACKING_MIN_VALID_VERSION
- change tracking [SQL Server], CHANGE_TRACKING_MIN_VALID_VERSION
ms.assetid: 5a43d23f-adcf-4c0b-95ad-07cee03c1f9d
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57e66ef862d98da7ee9d6d3cdadf3ebb290d152f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="changetrackingminvalidversion-transact-sql"></a>CHANGE_TRACKING_MIN_VALID_VERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce la versione minima nel client valido da utilizzare per ottenere informazioni sul rilevamento dalla tabella specificata, quando si utilizza il [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) (funzione).  
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CHANGE_TRACKING_MIN_VALID_VERSION ( table_object_id )  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_object_id*  
 ID oggetto della tabella. *table_object_id* è un **int**.  
  
## <a name="return-type"></a>Tipo restituito  
 **bigint**  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare questa funzione per convalidare il valore di *last_sync_version* parametro per CHANGETABLE. Se *last_sync_version* è inferiore al valore riportato da questa funzione, i risultati restituiti da una chiamata successiva a CHANGETABLE potrebbero non essere validi.  
  
 CHANGE_TRACKING_MIN_VALID_VERSION utilizza le informazioni seguenti per determinare il valore restituito:  
  
-   Quando è stato abilitato il rilevamento delle modifiche per la tabella.  
  
-   Quando è stata eseguita l'attività di pulizia in background per rimuovere le informazioni sul rilevamento delle modifiche anteriori al periodo di memorizzazione specificato per il database.  
  
-   Se la tabella è stata troncata. In questo modo vengono rimosse tutte le informazioni sul rilevamento delle modifiche associate alla tabella.  
  
 La funzione restituisce NULL se si verifica una delle condizioni seguenti:  
  
-   Rilevamento modifiche non abilitato per il database.  
  
-   ID oggetto della tabella specifica non valido per il database corrente.  
  
-   Autorizzazione insufficiente per la tabella specificata dall'ID oggetto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come determinare la validità della versione specificata. È necessario ottenere la minima versione valida della tabella `dbo.Employees`, confrontandola quindi con il valore della variabile `@last_sync_version`. Se il valore di `@last_sync_version` è inferiore al valore di `@min_valid_version`, l'elenco delle righe modificate non sarà valido.  
  
> [!NOTE]  
>  È possibile ottenere il valore da una tabella o da un altro percorso in cui è stato memorizzato l'ultimo numero di versione utilizzato per sincronizzare i dati.  
  
```  
-- The tracked change is tagged with the specified context   
DECLARE @min_valid_version bigint, @last_sync_version bigint;  
  
SET @min_valid_version =   
CHANGE_TRACKING_MIN_VALID_VERSION(OBJECT_ID('dbo.Employees'));  
  
SET @last_sync_version = 11  
IF (@last_sync_version < @min_valid_version)  
-- Error � do not obtain changes  
ELSE  
-- Obtain changes using CHANGETABLE(CHANGES ...)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di rilevamento delle modifiche &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [sys.change_tracking_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables.md)  
  
  
