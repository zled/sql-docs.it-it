---
title: spatial_reference_systems (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f1cb77a5da692f17a790d2eb5ffca6f82a939449
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39538291"
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Consente di elencare i sistemi di riferimento spaziale (SRID) supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|Identificatore SRID supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|Autorità dell'identificatore SRID.|  
|authorized_spatial_reference_id|**int**|L'identificatore SRID fornito dall'autorità denominata nel **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Rappresentazione WKT dell'identificatore SRID.|  
|unit_of_measure|**nvarchar(128)**|Nome dell'unità di misura.|  
|unit_conversion_factor|**float**|Lunghezza dell'unità di misura in metri.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
