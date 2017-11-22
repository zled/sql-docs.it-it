---
title: DBCC PROCCACHE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs: TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f818e3204f16892cb3bde8e8570a219abbd48aa3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Visualizza in formato di tabella le informazioni sulla cache delle procedure.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 con  
 Consente di specificare opzioni.  
  
 NO_INFOMSGS  
 Disattiva la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="remarks"></a>Osservazioni  
La cache delle procedure viene utilizzata per inserire nella cache i piani compilati e piani di esecuzione per velocizzare l'esecuzione di batch. Le voci in una cache delle procedure si trovano a livello di batch. La cache delle procedure include le voci seguenti:
-   Piani compilati  
-   Piani di esecuzione  
-   Albero di algebrizzazione  
-   Procedure estese  
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le colonne del set di risultati.
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**Num proc esperti**|Numero totale di pagine utilizzate da tutte le voci nella cache delle procedure.|  
|**Num proc esperti utilizzati**|Numero totale di pagine utilizzate da tutte le voci in uso.|  
|**Num proc esperti active**|Disponibile solo per compatibilità con le versioni precedenti. Numero totale di pagine utilizzate da tutte le voci in uso.|  
|**dimensione della cache proc**|Numero totale di voci nella cache delle procedure.|  
|**proc cache utilizzata**|Numero totale di voci in uso.|  
|**proc cache attiva**|Disponibile solo per compatibilità con le versioni precedenti. Numero totale di voci in uso.|  
  
## <a name="permissions"></a>Permissions  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** o al ruolo predefinito del database **db_owner** .
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
