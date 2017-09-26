---
title: Executables | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: aa0d2d5df7c3c39b1ad33794ae11c1a34ffe72d4
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa vista viene visualizzata una riga per ogni eseguibile nell'esecuzione specificata.  
  
 Un eseguibile è un'attività o un contenitore aggiunto al flusso di controllo di un pacchetto.  
  
|Nome colonna|**Tipo di dati**|Description|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Identificatore univoco per l'eseguibile.|  
|execution_id|**bigint**|Identificatore univoco per l'istanza di esecuzione.|  
|executable_name|**nvarchar(4000)**|Nome dell'eseguibile.|  
|executable_guid|**nvarchar(38)**|GUID dell'eseguibile.|  
|package_name|**nvarchar (260)**|Nome del pacchetto.|  
|package_path|**nvarchar(max)**|Percorso del pacchetto.|  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza di esecuzione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
## <a name="remarks"></a>Osservazioni  
  
