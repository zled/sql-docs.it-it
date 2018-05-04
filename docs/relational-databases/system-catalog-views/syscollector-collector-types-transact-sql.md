---
title: syscollector_collector_types (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_collector_types
- syscollector_collector_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collector_types view
ms.assetid: d5cd30bb-89fd-4814-a7e8-9074f043f90f
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9c56b03d902a329e47496b81d4f16e7f35f4bd39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorcollectortypes-transact-sql"></a>syscollector_collector_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni su un tipo di agente di raccolta per un elemento della raccolta.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**collector_type_uid**|**uniqueidentifer**|GUID per un tipo di raccolta. Non ammette i valori Null.|  
|**name**|**sysname**|Nome del tipo di raccolta. Non ammette i valori Null.|  
|**parameter_schema**|**xml**|XML Schema che descrive la configurazione del tipo di agente di raccolta specificato. Questo XML Schema è utilizzato per convalidare la configurazione XML effettiva associata a una particolare istanza dell'elemento della raccolta. Ammette i valori Null.|  
|**parameter_formatter**|**xml**|Determina il modello da utilizzare per trasformare l'XML per l'utilizzo nella pagina delle proprietà del set di raccolta. Ammette i valori Null.|  
|**collection_package_id**|**uniqueidentifer**|GUID per un pacchetto di raccolta. Non ammette i valori Null.|  
|**collection_package_path**|**nvarchar(4000)**|Fornisce il percorso al pacchetto di raccolta. Ammette i valori Null.|  
|**collection_package_name**|**sysname**|Nome del pacchetto di raccolta. Non ammette i valori Null.|  
|**upload_package_id**|**uniqueidentifer**|GUID per il pacchetto di caricamento. Non ammette i valori Null.|  
|**upload_package_path**|**nvarchar(4000)**|Fornisce il percorso al pacchetto di caricamento. Ammette i valori Null.|  
|**upload_package_name**|**sysname**|Nome del pacchetto di caricamento. Non ammette i valori Null.|  
|**is_system**|**bit**|Attivato (1) o disattivato (0) per indicare se il tipo di agente di raccolta dati è stato fornito con l'agente di raccolta dati o se è stato aggiunto in un secondo momento dal **dc_admin**. Potrebbe trattarsi di un tipo personalizzato sviluppato internamente o da terze parti. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede SELECT per **dc_operator**, **dc_proxy**.  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Aggiornato **collection_type_uid** nome della colonna **collector_type_uid**.|  
|Correzione della descrizione per il **parameter_schema** colonna per indicare che sono ammessi valori null.|  
|Aggiunta di **parameter_formatter** colonna.|  
|Correzione del tipo di dati per il **collection_package_path** colonna e l'aggiornamento della descrizione per indicare che il valore è nullable.|  
|Correzione del tipo di dati per il **upload_package_path** colonna e l'aggiornamento della descrizione per indicare che il valore è nullable.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Viste dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
