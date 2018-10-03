---
title: catalog.executables | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cca22286db2bb959a3aecb6524528292a207eedc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817519"
---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa vista viene visualizzata una riga per ogni eseguibile nell'esecuzione specificata.  
  
 Un eseguibile è un'attività o un contenitore aggiunto al flusso di controllo di un pacchetto.  
  
|Nome colonna|**Data type**|Descrizione|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Identificatore univoco per l'eseguibile.|  
|execution_id|**bigint**|Identificatore univoco per l'istanza di esecuzione.|  
|executable_name|**nvarchar(4000)**|Nome dell'eseguibile.|  
|executable_guid|**nvarchar(38)**|GUID dell'eseguibile.|  
|package_name|**nvarchar(260)**|Nome del pacchetto.|  
|package_path|**nvarchar(max)**|Percorso del pacchetto.|  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza di esecuzione  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
## <a name="remarks"></a>Remarks  
  
