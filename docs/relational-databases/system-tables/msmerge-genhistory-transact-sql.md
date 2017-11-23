---
title: MSmerge_genhistory (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs: TSQL
helpviewer_keywords: MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0408dd3ecc87598117466c03d7b474c23f1ce514
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_genhistory** tabella contiene una riga per ogni generazione nota a un sottoscrittore (entro il periodo di memorizzazione). Viene utilizzata per evitare l'invio di generazioni comuni durante operazioni di scambio e per risincronizzare i Sottoscrittori ripristinati dai backup. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Identificatore globale delle modifiche identificate dalla generazione nel Sottoscrittore.|  
|**pubid**|**uniqueidentifier**|Identificatore della pubblicazione.|  
|**generazione**|**bigint**|Valore di generazione.|  
|**art_nick**|**int**|Nome alternativo dell'articolo.|  
|**nomi alternativi**|**varbinary(1001)**|Elenco di nomi alternativi degli altri Sottoscrittori in cui questa generazione è già presente. Viene utilizzato per evitare l'invio di una generazione a un Sottoscrittore in cui tali modifiche sono già state applicate. L'elenco di nomi alternativi viene mantenuto ordinato per ottimizzare le operazioni di ricerca. Se vi sono altri nomi alternativi da aggiungere a questo campo, essi non trarranno beneficio da tale ottimizzazione.|  
|**colDate**|**datetime**|Data in cui la generazione corrente è stata aggiunta alla tabella.|  
|**genstatus**|**tinyint**|Lo stato della generazione è il seguente:<br /><br /> **0** = aperto.<br /><br /> **1** = chiuso.<br /><br /> **2** = chiuso e generato in un altro sottoscrittore.|  
|**changecount**|**int**|Numero delle modifiche già applicate in una specifica generazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
