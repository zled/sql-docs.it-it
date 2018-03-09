---
title: remote_service_bindings (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccfb729fd864449b0df9468167a76d591b7e6520
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa vista del catalogo contiene una riga per associazione al servizio remoto. 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome dell'associazione al servizio remoto. Non ammette i valori Null.|  
|**remote_service_binding_id**|**int**|ID dell'associazione al servizio remoto. Non ammette i valori Null.|  
|**principal_id**|**int**|ID dell'entità di database proprietaria dell'associazione al servizio remoto. Ammette valori Null.|  
|**remote_service_name**|**nvarchar(256)**|Nome del servizio remoto a cui viene applicata l'associazione corrente. Ammette valori Null.|  
|**service_contract_id**|**int**|ID del contratto a cui viene applicata l'associazione corrente. Il valore 0 corrisponde a un carattere jolly che indica che l'associazione viene applicata a tutti i contratti per il servizio. Non ammette i valori Null.|  
|**remote_principal_id**|**int**|ID dell'utente specificato nell'associazione al servizio remoto. Service Broker utilizza un certificato di proprietà di tale utente per comunicare con il servizio specificato nei contratti specificati. Ammette valori Null.|  
|**is_anonymous_on**|**bit**|L'associazione al servizio remoto utilizza la sicurezza ANONYMOUS. L'identità dell'utente che inizia la conversazione non viene fornita al servizio di destinazione. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
