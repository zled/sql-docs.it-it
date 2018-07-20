---
title: MSmerge_settingshistory (Transact-SQL) | Microsoft Docs
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
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61d69b6a6c6c965e5737d185c0e4b936fea797fc
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102129"
---
# <a name="msmergesettingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_settingshistory** tabella viene utilizzata per memorizzare una cronologia delle modifiche apportate alle proprietà di articolo e pubblicazione di replica di tipo merge con una riga per ogni modifica apportata a una topologia di replica di tipo merge. Nella tabella sono inoltre archiviate informazioni sulle impostazioni iniziali delle proprietà. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**EventTime**|**datetime**|Data e ora in cui è stato generato l'evento.|  
|**pubid**|**uniqueidentifier**|Identificatore univoco per la pubblicazione specificata.|  
|**artid**|**uniqueidentifier**|Identificatore univoco per l'articolo specificato.|  
|**il tipo di evento**|**tinyint**|Specifica il tipo di evento registrato. I possibili valori sono i seguenti:<br /><br /> **1** – impostazione proprietà del livello di pubblicazione iniziale.<br /><br /> **2** -modifica di una proprietà di pubblicazione.<br /><br /> **101** -impostazione di proprietà di articolo iniziale.<br /><br /> **102** -modifica di una proprietà di articolo.|  
|**propertyname**|**sysname**|Nome della proprietà impostata o modificata.|  
|**valore previousvalue**|**sysname**|Valore precedente di una proprietà modificata.|  
|**NewValue**|**sysname**|Valore con cui viene modificata o creata la proprietà.|  
|**eventtext**|**nvarchar(2000)**|Stringa di caratteri che descrive l'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
