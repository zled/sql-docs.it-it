---
title: sys.dm_xe_object_columns (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc39214e7902da325e228630fcfdbb780a49c8d2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni sullo schema per tutti gli oggetti.  
  
> [!NOTE]  
>  Gli oggetti evento espongono schemi fissi per i dati di sola lettura e di lettura/scrittura.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|Nome della colonna. nome è univoco all'interno dell'oggetto. Non ammette i valori Null.|  
|column_id|**int**|Identificatore della colonna. column_id è univoco all'interno dell'oggetto utilizzato con column_type. Non ammette i valori Null.|  
|object_name|**nvarchar(60)**|Nome dell'oggetto a cui appartiene la colonna. Esiste una relazione molti-a-uno con sys.dm_xe_objects.id. Non ammette i valori Null.|  
|object_package_guid|**uniqueidentifier**|GUID del pacchetto che contiene l'oggetto. Non ammette i valori Null.|  
|type_name|**nvarchar(60)**|Nome del tipo per questa colonna. Non ammette i valori Null.|  
|type_package_guid|**uniqueidentifier**|GUID del pacchetto che contiene il tipo di dati della colonna. Non ammette i valori Null.|  
|column_type|**nvarchar(60)**|Indica il modo in cui viene utilizzata la colonna. Non ammette i valori Null. COLUMN_TYPE può essere uno dei valori seguenti:<br /><br /> readonly. La colonna contiene un valore statico che non può essere modificato.<br /><br /> data. La colonna contiene dati runtime esposti dall'oggetto.<br /><br /> customizable. La colonna contiene un valore che può essere modificato.<br /><br /> Nota: Se si modifica questo valore può modificare il comportamento dell'oggetto.|  
|column_value|**nvarchar(256)**|Visualizza valori statici associati alla colonna dell'oggetto. Ammette i valori Null.|  
|capabilities|**int**|Bitmap che descrive le funzionalità della colonna. Ammette i valori Null.|  
|capabilities_desc|**nvarchar(256)**|Descrizione delle funzionalità della colonna dell'oggetto. I valori validi sono i seguenti:<br /><br /> Mandatory. Il valore deve essere impostato in caso di associazione dell'oggetto padre a una sessione dell'evento.<br /><br /> NULL|  
|description|**nvarchar(256)**|Descrizione della colonna dell'oggetto. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
### <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name, sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_objects.package_guid|Molti-a-uno|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

