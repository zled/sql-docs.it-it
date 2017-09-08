---
title: Operazione DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 461ee87f41692172b31125e36553c0eab0b09772
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>Operazione DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Consente di visualizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] piano di esecuzione per una query in esecuzione in uno specifico [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] del nodo di controllo o del nodo di calcolo. Consente di risolvere i problemi relativi alle prestazioni di query durante l'esecuzione di query sui nodi di calcolo e nodo del controllo.
  
Una volta che vengono riconosciuti i problemi di prestazioni di query per SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query in esecuzione nei nodi di calcolo, esistono diversi modi per migliorare le prestazioni. Possibili soluzioni per migliorare le prestazioni delle query sui nodi di calcolo includono la creazione di statistiche su più colonne, la creazione di indici non cluster o utilizzando l'hint per la query.
  
![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
Sintassi per SQL Server:

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Sintassi Azure Parallel Data Warehouse:
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *distribution_id*  
 Identificatore per la distribuzione in cui è in esecuzione il piano di query. Questo è un numero intero e non può essere NULL. Utilizzato quando la destinazione [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 *pdw_node_id*  
 Identificatore per il nodo che esegue il piano di query. Questo è un numero intero e non può essere NULL. Utilizzato quando un dispositivo di destinazione.  
  
 *SPID*  
 Identificatore per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sessione che esegue il piano di query. Questo è un numero intero e non può essere NULL.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione CONTROL su [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
È richiesta l'autorizzazione SERVER-dello stato di visualizzazione nel dispositivo.
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>Esempi:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. Sintassi di base operazione DBCC PDW_SHOWEXECUTIONPLAN  
 Durante l'esecuzione su un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] dell'istanza, modificare la query precedente per selezionare anche la distribution_id.  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
Verrà restituito il valore di spid per l'esecuzione di ogni attivamente la distribuzione. Se si desidera che le distribuzione 1 era in esecuzione nella sessione 375, sarà necessario eseguire il comando seguente.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>B. Sintassi di base operazione DBCC PDW_SHOWEXECUTIONPLAN  
 La query che è in esecuzione da troppo tempo è in esecuzione un DMS query operazione del piano o un'operazione di piano di query SQL.  
  
Se la query viene eseguita un'operazione di piano di query DMS, è possibile utilizzare la query seguente per recuperare un elenco degli ID di nodo e gli ID di sessione per i passaggi che non sono completi.
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
In base ai risultati della query precedente, usare il sql_spid e pdw_node_id come parametri PDW_SHOWEXEUCTIONPLAN DBCC. Ad esempio, il comando seguente viene illustrato il piano di esecuzione per pdw_node_id 201001 e sql_spid 375.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>Vedere anche
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)
