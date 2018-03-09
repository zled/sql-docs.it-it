---
title: Sys. Endpoints (Transact-SQL) | Documenti Microsoft
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
- endpoints
- sys.endpoints
- endpoints_TSQL
- sys.endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoints catalog view
ms.assetid: e6dafa4e-e47e-43ec-acfc-88c0af53c1a1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ded68aefc2121f651b9005fe3e75b64ec80dc0c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysendpoints-transact-sql"></a>sys.endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni endpoint creato nel sistema. Esiste sempre un solo endpoint SYSTEM.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome dell'endpoint. Valore univoco all'interno del server. Non ammette i valori Null.|  
|**endpoint_id**|**int**|ID dell'endpoint. Valore univoco all'interno del server. Un endpoint con ID minore di 65536 è un endpoint di sistema. Non ammette i valori Null.|  
|**principal_id**|**int**|ID dell'entità server che ha creato l'endpoint e ne è proprietaria. Ammette i valori Null.|  
|**protocollo**|**tinyint**|Protocollo dell'endpoint.<br /><br /> 1 = HTTP<br /><br /> 2 = TCP<br /><br /> 3 = Named pipe<br /><br /> 4 = Memoria condivisa<br /><br /> 5 = VIA (Virtual Interface Adapter)<br /><br /> Non ammette i valori Null.|  
|**protocol_desc**|**nvarchar(60)**|Descrizione del protocollo dell'endpoint. Ammette valori Null. I valori validi sono:<br /><br /> **HTTP**<br /><br /> **TCP**<br /><br /> **NAMED_PIPES**<br /><br /> **SHARED_MEMORY**<br /><br /> **TRAMITE** Nota: il protocollo VIA è deprecato. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|**tipo**|**tinyint**|Tipo di payload dell'endpoint.<br /><br /> 1 = SOAP<br /><br /> 2 = TSQL<br /><br /> 3 = SERVICE_BROKER<br /><br /> 4 = DATABASE_MIRRORING<br /><br /> Non ammette i valori Null.|  
|**type_desc**|**nvarchar(60)**|Descrizione del tipo di payload dell'endpoint. Ammette i valori Null. I valori validi sono:<br /><br /> **SOAP**<br /><br /> **TSQL**<br /><br /> **SERVICE_BROKER**<br /><br /> **DATABASE_MIRRORING**|  
|**stato**|**tinyint**|Stato dell'endpoint.<br /><br /> 0 = STARTED: l'endpoint è in attesa ed elabora le richieste.<br /><br /> 1 = STOPPED: l'endpoint è in attesa, ma non elabora le richieste.<br /><br /> 2 = DISABLED: l'endpoint non è in attesa.<br /><br /> Il valore predefinito è 1. Ammette i valori Null.|  
|**state_desc**|**nvarchar(60)**|Descrizione dello stato dell'endpoint:<br /><br /> STARTED = L'endpoint è in attesa ed elabora le richieste.<br /><br /> STOPPED = L'endpoint è in attesa, ma non elabora le richieste.<br /><br /> DISABLED = L'endpoint non è in attesa.<br /><br /> Il valore predefinito è STOPPED.<br /><br /> Ammette i valori Null.|  
|**is_admin_endpoint**|**bit**|Specifica se l'endpoint è destinato a un utilizzo amministrativo.<br /><br /> 0 = Endpoint non amministrativo.<br /><br /> 1 = Endpoint amministrativo.<br /><br /> Non ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo degli endpoint &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
