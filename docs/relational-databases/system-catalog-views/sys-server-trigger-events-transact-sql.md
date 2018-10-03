---
title: Sys.server_trigger_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_trigger_events_TSQL
- server_trigger_events_TSQL
- sys.server_trigger_events
- server_trigger_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_trigger_events catalog view
ms.assetid: be7d8a59-3c00-4f1b-b4b0-3dcd5572e002
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2065fbb7c84adbfc521e5622e8826bedebf5a11
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679739"
---
# <a name="sysservertriggerevents-transact-sql"></a>sys.server_trigger_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni evento per cui viene attivato un trigger sincrono a livello di server.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**colonne ereditate**||Eredita tutte le colonne da [server_events](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md).|  
|**is_first**|**bit**|Contrassegna il trigger come il primo da attivare per questo evento.|  
|**is_last**|**bit**|Contrassegna il trigger come l'ultimo da attivare per questo evento.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
