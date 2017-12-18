---
title: catalog.packages (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e544436126d299182760f94ef46304c334d448b6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli di tutti i pacchetti visualizzati nel catalogo di **SSISDB**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Identificatore (ID) univoco del pacchetto.|  
|name|**nvarchar(256)**|Nome univoco del pacchetto.|  
|package_guid|**uniqueidentifier**|GUID tramite cui viene identificato il pacchetto.|  
|description|**nvarchar(1024)**|Descrizione del pacchetto (facoltativa).|  
|package_format_version|**int**|Versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzata per lo sviluppo del pacchetto.|  
|version_major|**int**|Versione principale del pacchetto.|  
|version_minor|**int**|Versione secondaria del pacchetto.|  
|version_build|**int**|Versione di build del pacchetto.|  
|version_comments|**nvarchar(1024)**|Commenti facoltativi sulla versione del pacchetto.|  
|version_guid|**uniqueidentifier**|GUID tramite cui viene identificata in modo univoco la versione del pacchetto.|  
|project_id|**bigint**|ID univoco del progetto.|  
|entry_point|**bit**|Il valore `1` indica che il pacchetto deve essere avviato direttamente. Il valore `0` indica che il pacchetto deve essere avviato direttamente da un altro pacchetto con l'attività Esegui pacchetto. Il valore predefinito è `1`.|  
|validation_status|**char(1)**|Stato della convalida.|  
|last_validation_time|**datetimeoffset(7)**|Ora dell'ultima convalida.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni pacchetto nel catalogo.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per il progetto corrispondente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
> [!NOTE]  
>  Se si dispone dell'autorizzazione READ per un progetto, si dispone anche dell'autorizzazione READ per tutti i pacchetti e i riferimenti all'ambiente associati a tale progetto. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
