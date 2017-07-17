---
title: MSSQLSERVER_2814 | Microsoft Docs
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 109b5a18604b2111f3344ba216a6d3d98131d116
ms.openlocfilehash: 3bca883d9f5b13b81e021014193df43fc3f5f6e3
ms.contentlocale: it-it
ms.lasthandoff: 07/12/2017

---
# MSSQLSERVER_2814
<a id="mssqlserver2814" class="xliff"></a>
  
## Dettagli
<a id="details" class="xliff"></a>  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2814|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PR_POSSIBLE_INFINITE_RECOMPILE|  
|Testo del messaggio|Rilevata una possibile ricompilazione infinita per SQLHANDLE %hs, PlanHandle %hs, offset iniziale %d, offset finale %d. Motivo dell'ultima ricompilazione: % d.|  
  
## Spiegazione
<a id="explanation" class="xliff"></a>  
Una o più istruzioni ha determinato la ricompilazione del batch di query almeno 50 volte. Per evitare ulteriori ricompilazioni, è necessario correggere l'istruzione specificata.  
  
I motivi della ricompilazione sono elencati nella tabella seguente.  
  
|Codice motivo|Description|  
|---------------|---------------|  
|1|Schema modificato|  
|2|Statistiche modificate|  
|3|Compilazione posticipata|  
|4|Opzione impostata modificata|  
|5|Tabella temporanea modificata|  
|6|Set di righe remoto modificato|  
|7|Autorizzazioni FOR BROWSE modificate|  
|8|Ambiente di notifica query modificato|  
|9|Vista partizionata modificata|  
|10|Opzioni cursore modificate|  
|11|Opzione (recompile) richiesta|  
  
## Azione dell'utente
<a id="user-action" class="xliff"></a>  
  
1.  Visualizzare l'istruzione che determina la ricompilazione mediante l'esecuzione della query seguente. Sostituire i segnaposto *sql_handle*, *starting_offset*, *ending_offset* e *plan_handle* con i valori specificati nel messaggio di errore. Le colonne **database_name** e **object_name** sono NULL per le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc e preparate.  
  
    ```sql   
    SELECT DB_NAME(st.dbid) AS database_name,  
        OBJECT_NAME(st.objectid) AS object_name,  
        st.text  
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st  
    WHERE qs.statement_start_offset = *starting_offset*  
    AND qs.statement_end_offset = *ending_offset*  
    AND qs.plan_handle = *plan_handle*;
    ```
  
2.  In base alla descrizione del codice motivo, modificare l'istruzione, il batch o la procedura per evitare ricompilazioni. Una stored procedure può contenere, ad esempio, uno o più istruzioni SET. Queste istruzioni devono essere rimosse dalla procedura. Per esempi aggiuntivi sulle cause e sulle risoluzioni dei problemi di ricompilazione, vedere [Problematiche di compilazione batch, ricompilazione e memorizzazione dei piani nella cache in SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=69175).  
  
3.  Se il problema persiste, contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
## Vedere anche
<a id="see-also" class="xliff"></a>  
[Classe di evento SQL:StmtRecompile](../event-classes/sql-stmtrecompile-event-class.md)  
  

