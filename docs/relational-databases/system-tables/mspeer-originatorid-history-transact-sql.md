---
title: MSpeer_originatorid_history (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 24991d91a43ee00e5999de417d7cc4d44436d408
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mspeeroriginatoridhistory-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni ID origine definito nella topologia. Include gli ID dei nodi che non sono più attivi. La tabella viene utilizzata quando si configura un nuovo nodo per il rilevamento dei conflitti per assicurarsi che l'ID origine specificato non sia già stato utilizzato. Questa tabella è archiviata nel database di pubblicazione. Per ulteriori informazioni sul rilevamento dei conflitti, vedere [il rilevamento dei conflitti nella replica Peer-to-Peer](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Pubblicazione per cui è stato specificato l'ID origine.|  
|originator_id|**int**|Numero che identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti.|  
|originator_node|**sysname**|Istanza del server per cui è stato specificato l'ID origine.|  
|originator_db|**sysname**|Database di pubblicazione per cui è stato specificato l'ID origine.|  
|originator_db_version|**int**|Identifica il numero di versione del database di origine.|  
|originator_version|**int**|Identifica il numero di versione del server di pubblicazione.|  
|inserted_date|**datetime**|Data e ora in cui la riga per l'ID origine è stata inserita in questa tabella.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
