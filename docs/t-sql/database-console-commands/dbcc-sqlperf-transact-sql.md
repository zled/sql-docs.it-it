---
title: DBCC SQLPERF (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQLPERF
- DBCC_SQLPERF_TSQL
- SQLPERF_TSQL
- DBCC SQLPERF
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], transaction logs
- transaction logs [SQL Server], space usage
- space [SQL Server], transaction logs
- DBCC SQLPERF statement
ms.assetid: ec9225ce-e20f-4b03-8b3a-7bcad8a649df
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 41f854ce5ff1261829df621931d3a736426f32c8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-sqlperf-transact-sql"></a>DBCC SQLPERF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Fornisce statistiche relative all'utilizzo dello spazio nel log delle transazioni per tutti i database. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e può essere utilizzato per reimpostare le statistiche di latch e attese.
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([anteprima in alcune aree](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC SQLPERF   
(  
     [ LOGSPACE ]  
     |  
          [ "sys.dm_os_latch_stats" , CLEAR ]  
     |  
     [ "sys.dm_os_wait_stats" , CLEAR ]  
)   
     [WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
LOGSPACE  
Restituisce la dimensione corrente del log delle transazioni e la percentuale di spazio del log utilizzata per ogni database. È possibile utilizzare queste informazioni per monitorare la quantità di spazio utilizzato in un log delle transazioni.  
  
**"** **Sys.dm os_latch_stats",** Cancella  
Reimposta le statistiche relative ai latch. Per ulteriori informazioni, vedere [Sys.dm os_latch_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md). Questa opzione non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
**"Sys.dm os_wait_stats",** Cancella  
Reimposta le statistiche relative alle attese. Per ulteriori informazioni, vedere [Sys.dm os_wait_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). Questa opzione non è disponibile in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
WITH NO_INFOMSGS  
Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="result-sets"></a>Set di risultati  
 Nella tabella seguente vengono descritte le colonne del set di risultati.  
  
|Nome colonna|Definizione|  
|---|---|
|**Nome database**|Nome del database a cui si riferiscono le statistiche del log visualizzate.|  
|**Dimensioni log (MB)**|Dimensione corrente allocata al log. Questo valore è sempre inferiore rispetto alla quantità di spazio allocata inizialmente per il log in quanto [!INCLUDE[ssDE](../../includes/ssde-md.md)] riserva una piccola quantità di spazio su disco per informazioni di intestazione interne.|  
|**Lo spazio del log utilizzato (%)**|Percentuale del file di log attualmente in uso per archiviare le informazioni di log delle transazioni.|  
|**Stato**|Stato del file di log. Sempre 0.|  
  
## <a name="remarks"></a>Osservazioni  
Nel log delle transazioni viene registrata ogni transazione eseguita in un database. Per ulteriori informazioni vedere [Log delle transazioni &#40; SQL Server &#41; ](../../relational-databases/logs/the-transaction-log-sql-server.md).
  
## <a name="permissions"></a>Permissions  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione di DBCC SQLPERF (LOGSPACE) è necessaria l'autorizzazione VIEW SERVER STATE nel server. Per reimpostare le statistiche relative a latch e attese è richiesta l'autorizzazione ALTER SERVER STATE per il server.
  
In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Premium richiede l'autorizzazione VIEW DATABASE STATE nel database. In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Standard e Basic richiede il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] account amministratore. Le statistiche di reimpostazione di latch e attese non sono supportate.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-log-space-information-for-all-databases"></a>A. Visualizzazione delle informazioni relative allo spazio del log per tutti i database  
Nell'esempio seguente vengono visualizzate le informazioni relative a `LOGSPACE` per tutti i database inclusi nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
```sql  
DBCC SQLPERF(LOGSPACE);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Database Name Log Size (MB) Log Space Used (%) Status        
------------- ------------- ------------------ -----------   
master         3.99219      14.3469            0   
tempdb         1.99219      1.64216            0   
model          1.0          12.7953            0   
msdb           3.99219      17.0132            0   
AdventureWorks 19.554688    17.748701          0  
```  
  
### <a name="b-resetting-wait-statistics"></a>B. Reimpostazione delle statistiche relative alle attese  
Nell'esempio seguente vengono reimpostate le statistiche relative alle attese per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
```sql  
DBCC SQLPERF("sys.dm_os_wait_stats",CLEAR);  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)
  
  


