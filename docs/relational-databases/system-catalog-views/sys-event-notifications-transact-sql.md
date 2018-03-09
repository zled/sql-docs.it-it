---
title: Sys. event_notifications (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- event_notifications_TSQL
- event_notifications
- sys.event_notifications_TSQL
- sys.event_notifications
dev_langs:
- TSQL
helpviewer_keywords:
- sys.event_notifications catalog view
ms.assetid: 136a76ee-2b35-4418-ab46-fda2d51f7d99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef927e091f15027d8e2fd965cc50955adf7092d1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="syseventnotifications-transact-sql"></a>sys.event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni oggetto che rappresenta una notifica degli eventi, con **sys** = EN.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome della notifica degli eventi.|  
|**object_id**|**int**|Numero di identificazione dell'oggetto. Valore univoco all'interno di un database.|  
|**parent_class**|**tinyint**|Classe padre.<br /><br /> 0 = Database<br /><br /> 1 = Oggetto o colonna|  
|**parent_class_desc**|**nvarchar(60)**|DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_ID**|**int**|ID diverso da zero dell'oggetto padre.<br /><br /> 0 = Il database rappresenta la classe padre.|  
|**create_date**|**datetime**|Data di creazione.|  
|**modify_date**|**datetime**|È sempre uguale a **create_date**.|  
|**SERVICE_NAME**|**nvarchar(256)**|Nome del servizio di destinazione a cui viene inviata la notifica.|  
|**BROKER_INSTANCE**|**nvarchar (128)**|Istanza di Service Broker a cui viene inviata la notifica.|  
|**principal_id**|**int**|ID dell'entità di database proprietaria della notifica degli eventi.|  
|**creator_sid**|**varbinary (85)**|SID dell'account di accesso che ha creato la notifica degli eventi.<br /><br /> È NULL se non si specifica l'opzione FAN_IN.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
