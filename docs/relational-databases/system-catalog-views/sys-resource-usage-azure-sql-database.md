---
title: Sys. resource_usage (Database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_usage_TSQL
- resource_usage
- sys.resource_usage
- resource_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- resource_usage
- sys.resource_usage
ms.assetid: b90147a3-fd8e-408e-961d-5c7000e068ad
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0a79eed306e8920ece4cc6ea1de97352c4706622
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604619"
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Questa funzionalità si trova nello stato anteprima. Non specificare una dipendenza dall'implementazione specifica di questa funzionalità perché potrebbe essere modificata o rimossa in una versione successiva.  
>   
>  Nello stato anteprima, il team operativo del [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] potrebbe abilitare e disabilitare la raccolta dati per questa DMV:  
>   
>  -   Quando è abilitata, la DMV restituisce i dati correnti man mano che vengono aggregati.  
> -   Quando è disabilitata, la DMV restituisce i dati cronologici, che potrebbero non essere aggiornati.  
  
 Fornisce il riepilogo orario dei dati di utilizzo delle risorse per i database utente nel server corrente. Dati cronologici vengono mantenuti per 90 giorni.  
  
 Per ogni database utente è presente una riga per ogni ora in modo continuo. Anche se il database è inattivo durante quest'ora, è presente una riga e il valore di usage_in_seconds per il database sarà 0. Il rollup delle informazioni SKU e dell'utilizzo dell'archiviazione viene eseguito per l'ora in modo appropriato.  
  
|Colonne|Tipo di dati|Description|  
|-------------|---------------|-----------------|  
|time|**datetime**|Ora (UTC) in incrementi di un'ora.|  
|database_name|**nvarchar**|Nome del database utente.|  
|sku|**nvarchar**|Nome della SKU. Di seguito sono indicati i valori possibili:<br /><br /> Web<br /><br /> Business<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|Somma del tempo della CPU utilizzato nell'ora.<br /><br /> Nota: Questa colonna è deprecata per V11 e non si applica alla versione 12. **Valore è sempre impostato su 0.**|  
|storage_in_megabytes|**decimal**|Capacità di archiviazione massima per l'ora, inclusi dati del database, indici, stored procedure e metadati.|  
  
## <a name="permissions"></a>Permissions  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni sufficienti per connettersi a virtual **master** database.  
  
  
