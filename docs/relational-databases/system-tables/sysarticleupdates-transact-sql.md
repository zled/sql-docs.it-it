---
title: sysarticleupdates (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 384e6abd93369bd1913bddf31b8dec6f8541e0d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005578"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni articolo che supporta sottoscrizioni ad aggiornamento immediato. Questa tabella è archiviata nel database replicato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Colonna Identity che include un numero di ID univoco per l'articolo.|  
|**pubid**|**int**|ID della pubblicazione a cui appartiene l'articolo.|  
|**sync_ins_proc**|**int**|ID della stored procedure che gestisce le transazioni di sincronizzazione per gli inserimenti.|  
|**sync_upd_proc**|**int**|ID della stored procedure che gestisce le transazioni di sincronizzazione per gli aggiornamenti.|  
|**sync_del_proc**|**int**|ID della stored procedure che gestisce le transazioni di sincronizzazione per le eliminazioni.|  
|**spettacolari**|**bit**|Indica che vengono generate automaticamente stored procedure:<br /><br /> **0** = false, generazione non automatica.<br /><br /> **1** = true, automatica.|  
|**sync_upd_trig**|**int**|ID del trigger per la gestione automatica delle versioni nella tabella degli articoli.|  
|**conflict_tableid**|**int**|ID della tabella dei conflitti.|  
|**ins_conflict_proc**|**int**|L'ID della procedura utilizzata per scrivere il conflitto per il **conflict_table**.|  
|**identity_support**|**bit**|Specifica se la gestione automatica degli intervalli di valori Identity è attivata quando si utilizza l'aggiornamento in coda. **0** significa che non vi è alcuna identità intervalli di valori supportati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
