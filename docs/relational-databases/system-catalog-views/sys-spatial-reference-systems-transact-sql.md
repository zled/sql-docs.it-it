---
title: spatial_reference_systems (Transact-SQL) | Documenti Microsoft
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4490cc6d28ee06193436de8b57cde8e7ac04402
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Consente di elencare i sistemi di riferimento spaziale (SRID) supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|Identificatore SRID supportato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar (128)**|Autorità dell'identificatore SRID.|  
|authorized_spatial_reference_id|**int**|L'identificatore SRID fornito dall'autorità denominata in **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Rappresentazione WKT dell'identificatore SRID.|  
|unit_of_measure|**nvarchar (128)**|Nome dell'unità di misura.|  
|unit_conversion_factor|**float**|Lunghezza dell'unità di misura in metri.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
