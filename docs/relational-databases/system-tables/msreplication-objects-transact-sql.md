---
title: MSreplication_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cfced92c3cd2cd789ebafb9ee7b03919b4a28612
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785574"
---
# <a name="msreplicationobjects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSreplication_objects** tabella contiene una riga per ogni oggetto che è associato con la replica nel database del sottoscrittore. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**object_name**|**sysname**|Nome dell'oggetto .|  
|**object_type**|**char(2)**|Tipo di oggetto:<br /><br /> **u** = tabella.<br /><br /> **t** = Trigger.<br /><br /> **p** = Stored Procedure.|  
|**article**|**sysname**|Nome dell'articolo a cui è associato l'oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
