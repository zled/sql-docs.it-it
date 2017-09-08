---
title: DBCC DROPCLEANBUFFERS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs:
- TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1a7a1507e230995df1c2b67a8499a12270b535c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Rimuove tutti i buffer vuoti dal pool di buffer e oggetti columnstore dal pool di oggetti dell'archivio colonne.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi
Sintassi per SQL Server: 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Sintassi per il Warehouse SQL Azure e Parallel Data Warehouse:

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 WITH NO_INFOMSGS  
 Disattiva tutti i messaggi informativi. Messaggi informativi vengono soppressi sempre su [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 COMPUTE  
 Cancellare la cache dei piani di query da ogni nodo di calcolo.  
  
 ALL  
 Cancellare la cache dei piani di query da ogni nodo di calcolo e dal nodo di controllo. Questo è il valore predefinito se non si specifica un valore.  
  
## <a name="remarks"></a>Osservazioni  
Utilizzare DBCC DROPCLEANBUFFERS per testare le query con una cache dei buffer "a freddo" senza arrestare e riavviare il server.
Per eliminare i buffer vuoti tra gli oggetti di pool e columnstore buffer dal pool di oggetti di columnstore, utilizzare innanzitutto CHECKPOINT per produrre una cache buffer a freddo. In questo modo tutte le pagine dirty del database corrente verranno scritte su disco e i buffer verranno svuotati. A questo punto sarà possibile eseguire il comando DBCC DROPCLEANBUFFERS per rimuovere tutti i buffer dal pool dei buffer.
  
## <a name="result-sets"></a>Set di risultati  
DBCC DROPCLEANBUFFERS su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  

Si applica a: SQL Server, Parallel Data Warehouse 

- È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  

Si applica a: Azure SQL Data Warehouse

- Richiede l'appartenenza al ruolo predefinito del server del database DB_OWNER.  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  

