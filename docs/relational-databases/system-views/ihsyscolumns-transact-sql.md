---
title: IHsyscolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0e9e69891e759468ab0ae62a59c2fc61a19a9bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668879"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHsyscolumns** Vista espone informazioni sulla colonna per gli articoli pubblicati da un Server di pubblicazione non SQL. Questa vista è archiviata nel databasedistribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome della colonna o del parametro della procedura.|  
|**id**|**int**|ID di oggetto della tabella a cui appartiene la colonna o ID della stored procedure a cui è associato il parametro.|  
|**tipoX**|**tinyint**|Il tipo di archiviazione fisica [Sys. systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|ID del tipo di dati esteso definito dall'utente.|  
|**Lunghezza**|**bigint**|La lunghezza massima di archiviazione fisica dal [Sys. systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|ID di colonna o di parametro.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|ID del valore predefinito della colonna.|  
|**domain**|**int**|ID della regola o vincolo CHECK per la colonna.|  
|**Numero**|**int**|Il numero di sottoprocedura quando la procedura è raggruppata (**0** per voci non di procedura).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Offset nella riga in cui appare la colonna.|  
|**collationid**|**int**|ID delle regole di confronto della colonna. NULL per colonne non di tipo carattere.|  
|**Lingua**|**int**|Identificatore di lingua per la colonna.|  
|**status**|**int**|Mappa di bit utilizzata per descrivere una proprietà della colonna o del parametro:<br /><br /> **0x08** = colonna ammette valori null.<br /><br /> **0x10** = ANSI padding era attivata quando **varchar** oppure **varbinary** sono state aggiunte colonne. Gli spazi vuoti finali vengono mantenuti per consentire **varchar** e gli zeri finali vengono mantenuti per **varbinary** colonne.<br /><br /> **0x40** = è un parametro OUTPUT.<br /><br /> **0x80** = colonna è una colonna identity.|  
|**type**|**int**|Il tipo di archiviazione fisica [Sys. systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**usertype**|**tinyint**|L'ID del tipo di dati definito dall'utente dal [Sys. systypes &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Prec**|**int**|Livello di precisione della colonna|  
|**Scalabilità**|**int**|Scala della colonna.|  
|**iscomputed**|**int**|Flag che indica se si tratta di una colonna calcolata:<br /><br /> **0** = non calcolata.<br /><br /> **1** = calcolata.|  
|**isoutparam**|**int**|Indica se il parametro della procedura è un parametro di output:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Indica se la colonna ammette valori Null:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**regole di confronto**|**int**|Nome delle regole di confronto della colonna. NULL per colonne non di tipo carattere.|  
|**tdscollation**|**int**|Nome delle regole di confronto della colonna quando restituite in un flusso di dati tabulare (TDS, Tabular Data Stream).|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
