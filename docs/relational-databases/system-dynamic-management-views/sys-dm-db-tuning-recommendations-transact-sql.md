---
title: sys.dm_db_tuning_recommendations (Transact-SQL) | Microsoft Docs
description: Informazioni su come trovare i potenziali problemi di prestazioni e soluzioni consigliate in SQL Server e Database SQL di Azure
ms.custom: 
ms.date: 07/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_tuning_recommendations
- dm_db_tuning_recommendations
- sys.dm_db_tuning_recommendations_TSQL
- dm_db_tuning_recommendations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database tuning recommendations feature [SQL Server], sys.dm_db_tuning_recommendations dynamic management view
- sys.dm_db_tuning_recommendations dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
caps.latest.revision: 
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43acc4c2bfbcb9458f93f2ad89414e3781a7836d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>sys.dm\_db\_tuning\_recommendations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni dettagliate su indicazioni di ottimizzazione.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro.

| **Nome colonna** | **Tipo di dati** | **Description** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Nome univoco della raccomandazione. |
| **type** | **nvarchar(4000)** | Il nome dell'opzione di ottimizzazione automatica che ha generato la raccomandazione, ad esempio,`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Motivo fornita perché questa raccomandazione. |
| **valido\_poiché** | **datetime2** | Questa indicazione è stata generata la prima volta. |
| **last\_refresh** | **datetime2** | Questa indicazione è stata generata l'ultima volta. |
| **state** | **nvarchar(4000)** | Documento JSON che descrive lo stato dell'indicazione. Sono disponibili i seguenti campi:<br />-   `currentValue`-stato corrente dell'indicazione.<br />-   `reason`-Costante che descrive perché la raccomandazione è nello stato corrente.|
| **è\_eseguibile\_azione** | **bit** | 1 = l'indicazione possa essere eseguita sul database tramite [!INCLUDE[tsql_md](../../includes/tsql_md.md)] script.<br />0 = la raccomandazione non possa essere eseguita sul database (ad esempio: indicazione di informazioni solo o ripristinato) |
| **is\_revertable\_action** | **bit** | 1 = le indicazioni possono essere monitorate e ripristinate dal motore di Database automaticamente.<br />0 = la raccomandazione non può essere monitorata e ripristinata automaticamente. La maggior parte delle &quot;eseguibile&quot; azioni saranno &quot;revertable&quot;. |
| **eseguire\_azione\_avviare\_ora** | **datetime2** | Viene applicata l'indicazione di Data. |
| **execute\_action\_duration** | **time** | Durata dell'azione di esecuzione. |
| **eseguire\_azione\_avviato\_da** | **nvarchar(4000)** | `User`= Utente forzato manualmente piano nell'indicazione. <br /> `System`= Sistema applicate automaticamente raccomandazione. |
| **eseguire\_azione\_avviato\_ora** | **datetime2** | È stato applicato l'indicazione di Data. |
| **revert\_action\_start\_time** | **datetime2** | Data che l'indicazione è stata annullata. |
| **revert\_action\_duration** | **time** | Durata dell'azione di annullamento. |
| **ripristinare\_azione\_avviato\_da** | **nvarchar(4000)** | `User`= Piano consigliato manualmente unforced utente. <br /> `System`= Sistema ripristinato automaticamente l'indicazione. |
| **ripristinare\_azione\_avviato\_ora** | **datetime2** | Data che l'indicazione è stata annullata. |
| **score** | **int** | Previsto valore/impatto di questa raccomandazione su 0-100 scala (più grande è preferibile) |
| **details** | **nvarchar(max)** | Documento JSON che contiene ulteriori dettagli sulla raccomandazione. Sono disponibili i seguenti campi:<br /><br />`planForceDetails`<br />-    `queryId`-query\_id della query regredite.<br />-    `regressedPlanId`-plan_id del piano di regredite.<br />-   `regressedPlanExecutionCount`-Numero di esecuzioni della query regredite piano prima la regressione è stata rilevata.<br />-    `regressedPlanAbortedCount`-Numero di errori rilevati durante l'esecuzione del piano di regredite.<br />-    `regressedPlanCpuTimeAverage`-Tempo di CPU medio utilizzato dalla query regredite prima che venga rilevata la regressione.<br />-    `regressedPlanCpuTimeStddev`-È stata rilevata deviazione Standard tempo della CPU utilizzato dalla query regredite prima la regressione.<br />-    `recommendedPlanId`-plan_id del piano a cui deve essere forzato.<br />-   `recommendedPlanExecutionCount`-Numero di esecuzioni della query con il piano deve essere forzata prima che venga rilevata la regressione.<br />-    `recommendedPlanAbortedCount`-Numero di errori rilevati durante l'esecuzione del piano a cui deve essere forzato.<br />-    `recommendedPlanCpuTimeAverage`-Tempo di CPU medio utilizzato dalla query eseguita con il piano deve essere forzato (calcolato prima che venga rilevata la regressione).<br />-    `recommendedPlanCpuTimeStddev`È stata rilevata la deviazione standard tempo della CPU utilizzato dalla query regredite prima la regressione.<br /><br />`implementationDetails`<br />-  `method`-Il metodo che deve essere utilizzato per correggere la regressione. Valore è sempre `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql_md.md)]script da eseguire per forzare il piano consigliato. |
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni restituite da `sys.dm_db_tuning_recommendations` viene aggiornato quando identifica potenziali regressione delle prestazioni di query motore di database e non è persistente. Indicazioni vengono mantenute solo fino al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene riavviato. Gli amministratori di database devono periodicamente copie di backup l'indicazione di ottimizzazione se desiderano mantenere, dopo il riciclo del server. 

 `currentValue`campo di `state` colonna potrebbe disporre i valori seguenti:
 | Stato | Description |
 |--------|-------------|
 | `Active` | Raccomandazione è attivo e non ancora applicate. È possibile eseguire script delle indicazioni ed eseguirlo manualmente. |
 | `Verifying` | Indicazione viene applicato dal [!INCLUDE[ssde_md](../../includes/ssde_md.md)] e processo di verifica interna consente di confrontare le prestazioni del piano forzato con il piano regredito. |
 | `Success` | Indicazione viene applicato correttamente. |
 | `Reverted` | Raccomandazione è annullata perché non esistono alcun miglioramenti significativi delle prestazioni. |
 | `Expired` | Raccomandazione è scaduto e non può essere applicato più. |

Il documento JSON in `state` colonna contiene il motivo che descrive perché è l'indicazione dello stato corrente. I valori nel campo motivo potrebbero essere: 

| Motivo | Description |
|--------|-------------|
| `SchemaChanged` | Raccomandazione è scaduta perché lo schema di una tabella di riferimento viene modificato. |
| `StatisticsChanged`| Indicazione scaduto a causa della modifica di statistiche in una tabella di riferimento. |
| `ForcingFailed` | È possibile forzare il piano consigliato su una query. Trovare il `last_force_failure_reason` nel [Sys. query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) vista per individuare il motivo dell'errore. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`opzione è disabilitata dall'utente durante il processo di verifica. Abilitare `FORCE_LAST_GOOD_PLAN` tramite [ALTER DATABASE SET AUTOMATIC_TUNING &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) istruzione o il piano manualmente tramite lo script in vigore `[details]` colonna. |
| `UnsupportedStatementType` | È possibile forzare piano sulla query. Esempi di query non supportate sono i cursori e `INSERT BULK` istruzione. |
| `LastGoodPlanForced` | Indicazione viene applicato correttamente. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] identificare potenziali regressione delle prestazioni, ma la `FORCE_LAST_GOOD_PLAN` opzione non è abilitata – vedere [ALTER DATABASE SET AUTOMATIC_TUNING &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Abilitare o applicare manualmente indicazione `FORCE_LAST_GOOD_PLAN` opzione. |
| `VerificationAborted`| Processo di verifica è interrotto a causa del riavvio o di pulizia dell'archivio Query. |
| `VerificationForcedQueryRecompile`| Query viene ricompilata perché non comporta miglioramenti significativi delle prestazioni. |
| `PlanForcedByUser`| Utente forzata manualmente il piano utilizzando [sp_query_store_force_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) procedura. |
| `PlanUnforcedByUser` | Utente manualmente annullare la forzatura di piano utilizzando [sp_query_store_unforce_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) procedura. |

 Statistiche della colonna dettagli non vengono visualizzate le statistiche di runtime piano (ad esempio, tempo CPU corrente). I dettagli della raccomandazione vengono acquisiti al momento del rilevamento di regressione e descrivere il motivo [!INCLUDE[ssde_md](../../includes/ssde_md.md)] identificato regressione delle prestazioni. Utilizzare `regressedPlanId` e `recommendedPlanId` query [viste del catalogo di archivio Query](../../relational-databases/performance/how-query-store-collects-data.md) per trovare le statistiche piano esatto di runtime.

## <a name="using-tuning-recommendations-information"></a>Utilizzando le informazioni indicazioni di ottimizzazione  
 Per ottenere lo script T-SQL che può risolvere il problema, è possibile utilizzare la query seguente:  
 
```
SELECT name, reason, score,
        JSON_VALUE(details, '$.implementationDetails.script') as script,
        details.* 
FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(details, '$.planForceDetails')
                WITH (  query_id int '$.queryId',
                        regressed_plan_id int '$.regressedPlanId',
                        last_good_plan_id int '$.recommendedPlanId') as details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active'
```
  
 Per ulteriori informazioni sulle funzioni JSON che può essere utilizzato per i valori di query nella vista raccomandazione, vedere [supporto JSON](../../relational-databases/json/index.md) in [!INCLUDE[ssde_md](../../includes/ssde_md.md)].
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il `Server admin` o `Azure Active Directory admin` account.  
  
## <a name="see-also"></a>Vedere anche  
 [L'ottimizzazione automatica](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Supporto JSON](../../relational-databases/json/index.md)
 
