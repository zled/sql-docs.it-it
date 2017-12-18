---
title: catalog.object_versions (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b50e91381182bf2462c8f784a71e811f3bb8efe9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzate le versioni di oggetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. In questa versione sono supportate solo le versioni di progetto in questa vista.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Identificatore (ID) univoco della versione dell'oggetto. La sequenzialità di questo numero non è garantita.|  
|object_id|**bigint**|ID univoco dell'oggetto.|  
|object_type|**smallint**|Tipo di oggetto. Per i progetti verrà visualizzato un valore pari a `20`.|  
|object_name|**sysname(nvarchar(128))**|Nome dell'oggetto .|  
|description|**nvarchar(1024)**|Descrizione del progetto.|  
|created_by|**nvarchar(128)**|Nome dell'utente che ha aggiunto l'oggetto al catalogo.|  
|created_time|**datetimeoffset**|Data e ora di aggiunta dell'oggetto al catalogo.|  
|restored_by|**nvarchar(128)**|Nome dell'utente che ha ripristinato l'oggetto.|  
|last_restored_time|**datetimeoffset**|Data e ora dell'ultimo ripristino dell'oggetto.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni versione di un oggetto nel catalogo.  
  
## <a name="permissions"></a>Permissions  
 Per visualizzare le righe di questa vista, è necessario disporre di una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ sull'oggetto  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
> [!NOTE]  
>  È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
