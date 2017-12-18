---
title: catalog.environments (database SSISDB) | Microsoft Docs
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
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: edb3360d05e44131d6f30b510ed5dd120e2aeae7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli relativi all'ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Negli ambienti sono contenute variabili che possono fare riferimento ai progetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Identificatore (ID) univoco dell'ambiente.|  
|name|**sysname**|Nome dell'ambiente.|  
|folder_id|**bigint**|ID univoco della cartella in cui si trova l'ambiente.|  
|description|**nvarchar(1024)**|Descrizione dell'ambiente. Questo valore è facoltativo.|  
|created_by_sid|**varbinary(85)**|ID di sicurezza (SID) dell'utente che ha creato l'ambiente.|  
|created_by_name|**nvarchar(128)**|Nome dell'utente che ha creato l'ambiente.|  
|created_time|**datetimeoffset**|Data e ora di creazione dell'ambiente.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni ambiente nel catalogo. I nomi degli ambienti sono univoci solo per quanto riguarda la cartella in cui vengono individuati. Ad esempio, un ambiente denominato `E1` può esistere in più cartelle nel catalogo, ma ogni cartella può disporre solo di un ambiente denominato `E1`.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
> [!NOTE]  
>  È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
