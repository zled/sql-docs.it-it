---
title: MSpublisher_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7904bd3b6d629daf65d97bf88bba26cbb02bd93f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620749"
---
# <a name="mspublisherdatabases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSpublisher_databases** tabella contiene una riga per ogni coppia database del server di pubblicazione/server di pubblicazione servito dal server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**id**|**int**|ID della riga|  
|**publisher_engine_edition**|**int**|L'edizione del server di pubblicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], che può essere una delle seguenti:<br /><br /> **10** = personal Edition<br /><br /> **11** = desktop Engine (MSDE)<br /><br /> **20** = standard<br /><br /> **21** = gruppo di lavoro<br /><br /> **30** = Enterprise (valutazione)<br /><br /> **31** = per gli sviluppatori<br /><br /> **40** = express (Express non può essere un server di pubblicazione. Questo valore è presente per motivi di completezza).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
