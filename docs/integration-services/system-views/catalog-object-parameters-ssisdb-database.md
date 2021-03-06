---
title: catalog.object_parameters (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0afd8f494474c54eaf911f6cd7b8f74c9ec1a287
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729559"
---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i parametri per tutti i pacchetti e progetti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|parameter_id|**bigint**|Identificatore (ID) univoco del parametro.|  
|project_id|**bigint**|ID univoco del progetto.|  
|object_type|**smallint**|Tipo di parametro. Il valore è `20` per un parametro del progetto e `30` per un parametro del pacchetto.|  
|object_name|**sysname**|Nome del progetto o pacchetto corrispondente.|  
|parameter_name|**sysname(nvarchar(128))**|Nome del parametro.|  
|data_type|**nvarchar(128)**|Tipo di dati del parametro.|  
|required|**bit**|Quando il valore è `1`, il valore del parametro è necessario per avviare l'esecuzione. In caso contrario, il valore è `0`.|  
|sensitive|**bit**|Quando il valore è `1`, il valore del parametro è importante. In caso contrario, il valore è `0`.|  
|description|**nvarchar(1024)**|Descrizione del pacchetto (facoltativa).|  
|design_default_value|**sql_variant**|Valore predefinito per il parametro assegnato durante la progettazione del progetto o del pacchetto.|  
|default_value|**sql_variant**|Valore predefinito utilizzato attualmente nel server.|  
|value_type|**char(1)**|Viene indicato il tipo di valore del parametro. In questo campo viene visualizzato `V` quando parameter_value è un valore letterale e `R` quando il valore viene assegnato facendo riferimento a una variabile di ambiente.|  
|value_set|**bit**|Quando il valore è `1`, il valore del parametro è stato assegnato. In caso contrario, il valore è `0`.|  
|referenced_variable_name|**nvarchar(128)**|Nome della variabile di ambiente assegnata al valore del parametro. Il valore predefinito è **NULL**.|  
|validation_status|**char(1)**|Identificato solo a scopo informativo. Non utilizzato in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|last_validation_time|**datetimeoffset(7)**|Identificato solo a scopo informativo. Non utilizzato in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 Per visualizzare le righe di questa vista, è necessario disporre di una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per il progetto  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
 È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
