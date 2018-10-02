---
title: catalog.packages (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1558aeed5266d573fcf7b99ced456a4d2de09940
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818959"
---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli di tutti i pacchetti visualizzati nel catalogo di **SSISDB**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Identificatore (ID) univoco del pacchetto.|  
|NAME|**nvarchar(256)**|Nome univoco del pacchetto.|  
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
  
## <a name="remarks"></a>Remarks  
 In questa vista viene visualizzata una riga per ogni pacchetto nel catalogo.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per il progetto corrispondente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
> [!NOTE]  
>  Se si dispone dell'autorizzazione READ per un progetto, si dispone anche dell'autorizzazione READ per tutti i pacchetti e i riferimenti all'ambiente associati a tale progetto. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
