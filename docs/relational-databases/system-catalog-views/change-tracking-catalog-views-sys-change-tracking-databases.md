---
title: Sys. change_tracking_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9f41b9f1888f17c48f5bf33154c974ef829953e3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555971"
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>Modificare viste del catalogo di rilevamento - Sys. change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni database con il rilevamento delle modifiche abilitato.  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database. È univoco all'interno dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Indica se i dati di rilevamento delle modifiche vengono rimossi automaticamente una volta trascorso il periodo di memorizzazione configurato:<br /><br /> 0 = Off<br /><br /> 1 = On|  
|retention_period|**int**|Se si utilizza la rimozione automatica, il periodo di memorizzazione specifica per quanto tempo i dati di rilevamento delle modifiche verranno conservati nel database.|  
|retention_period_units_desc|**nvarchar(60)**|Specifica la descrizione del periodo memorizzazione:<br /><br /> Minutes<br /><br /> Ore<br /><br /> Giorni|  
|retention_period_units|**tinyint**|Unità di tempo relativa al periodo di memorizzazione:<br /><br /> 1 = Minuti<br /><br /> 2 = Ore<br /><br /> 3 = Giorni|  
  
## <a name="permissions"></a>Permissions  
 Gli stessi controlli dell'autorizzazione vengono effettuati per sys.change_tracking_databases, così come per sys.databases. Se il chiamante di sys.change_tracking_databases non è il proprietario del database, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o VIEW ANY DATABASE a livello di server, oppure l'autorizzazione CREATE DATABASE nel database master o corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di rilevamento delle modifiche &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
