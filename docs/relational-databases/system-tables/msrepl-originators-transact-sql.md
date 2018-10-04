---
title: MSrepl_originators (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e731baa8a0c0bbff2cea638712fcad10b9ec58e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647889"
---
# <a name="msreploriginators-transact-sql"></a>MSrepl_originators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSrepl_originators** tabella contiene una riga per ogni sottoscrittore aggiornabile da cui ha origine la transazione. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifica il Sottoscrittore aggiornabile.|  
|**publisher_database_id**|**int**|Identifica il database di pubblicazione.|  
|**srvname**|**sysname**|Nome del server aggiornabile.|  
|**dbname**|**sysname**|Nome del database aggiornabile.|  
|**publication_id**|**int**|Identifica la pubblicazione.|  
|**dbversion**|**int**|Identifica la versione del database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
