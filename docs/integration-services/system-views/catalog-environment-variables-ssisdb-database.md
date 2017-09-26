---
title: Catalog. environment_variables (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 40e31b9697c453f6a9d60dfcc8d9302dfefe0ac4
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i dettagli delle variabili di ambiente di tutti gli ambienti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|Identificatore (ID) univoco della variabile di ambiente.|  
|environment_id|**bigint**|ID univoco dell'ambiente a cui è associata la variabile.|  
|name|**sysname**|Nome della variabile di ambiente.|  
|description|**nvarchar (1024)**|Descrizione della variabile di ambiente.|  
|tipo|**nvarchar (128)**|Tipo di dati della variabile di ambiente.|  
|sensitive|**bit**|Quando il valore è `1`, la variabile è importante e viene crittografata quando viene archiviata. Quando il valore è `0`, la variabile non è importante e il valore viene archiviato non crittografato.|  
|Valore|**sql_variant**|Valore della variabile di ambiente. Quando sensibili è `0`, viene visualizzato il valore di testo normale. Quando sensibili è `1`, **NULL** valore viene visualizzato.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni variabile di ambiente nel catalogo.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ sull'ambiente corrispondente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
