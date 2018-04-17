---
title: Sys. Messages (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c254ec33aea82f4587747253eefcf03fbbf4a56f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Viste del catalogo di messaggi (per gli errori) - Sys. Messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni **message_id** o **language_id** dei messaggi di errore nel sistema, per i messaggi sia definita dal sistema e definiti dall'utente. Per altre informazioni, vedere [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|ID del messaggio. Questo valore è univoco nel server. I messaggi con ID minore di 50000 sono messaggi di sistema.|  
|**language_id**|**smallint**|ID di lingua per cui il testo in **testo** viene utilizzato, come definito in **syslanguages**. Questo valore è univoco per un determinato **message_id**.|  
|**severity**|**tinyint**|Livello di gravità del messaggio, compreso tra 1 e 25. Questo è lo stesso per tutte le lingue all'interno dei messaggi un **message_id**.|  
|**is_event_logged**|**bit**|1 = Il messaggio viene registrato nell'evento se viene generato un errore. Questo è lo stesso per tutte le lingue all'interno dei messaggi un **message_id**.|  
|**text**|**nvarchar(2048)**|Testo del messaggio utilizzato per il corrispondente **language_id** è attiva.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [I messaggi &#40;errori&#41; viste del catalogo &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Messaggio di eccezione programmazione della finestra](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Messaggi di errore](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Eventi ed errori di Motore di database](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
