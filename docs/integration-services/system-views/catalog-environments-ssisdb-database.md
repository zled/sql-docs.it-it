---
title: Catalog. Environments (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6e7ba1ba0bd8a444e4609a2f3d011da9cd233b73
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli relativi all'ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Negli ambienti sono contenute variabili che possono fare riferimento ai progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Identificatore (ID) univoco dell'ambiente.|  
|name|**sysname**|Nome dell'ambiente.|  
|folder_id|**bigint**|ID univoco della cartella in cui si trova l'ambiente.|  
|description|**nvarchar (1024)**|Descrizione dell'ambiente. Questo valore è facoltativo.|  
|created_by_sid|**varbinary (85)**|ID di sicurezza (SID) dell'utente che ha creato l'ambiente.|  
|created_by_name|**nvarchar (128)**|Nome dell'utente che ha creato l'ambiente.|  
|created_time|**datetimeoffset**|Data e ora di creazione dell'ambiente.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni ambiente nel catalogo. I nomi degli ambienti sono univoci solo per quanto riguarda la cartella in cui vengono individuati. Ad esempio, un ambiente denominato `E1` può esistere in più cartelle nel catalogo, ma ogni cartella può disporre solo di un ambiente denominato `E1`.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ sull'ambiente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
