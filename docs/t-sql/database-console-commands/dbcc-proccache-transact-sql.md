---
title: DBCC PROCCACHE (Transact-SQL) | Documenti Microsoft
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
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 97e617e7867c90bf1e66c5e64e37b9039087d463
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

