---
title: Catalog.set_customized_logging_level_value | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: d83fb763-c7c6-4e20-bd10-0f995598b198
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75ef405fe4550e81ec2d5178a1d3242d405755af
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedlogginglevelvalue"></a>Catalog.set_customized_logging_level_value
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Modifica le statistiche o gli eventi registrati da un livello di registrazione personalizzato esistente. Per ulteriori informazioni sui livelli di registrazione personalizzati, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.set_customized_logging_level_value [ @level_name = ] level_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @level_name =] *level_name*  
 Il nome di un livello di registrazione personalizzato.  
  
 Il *level_name* è **nvarchar (128)**.  
  
 [ @property_name =] *property_name*  
 Il nome della proprietà da modificare. I valori validi sono **profilo** e **eventi**.  
  
 Il *property_name* è **nvarchar (128)**.  
  
 [ @property_value =] *property_value*  
 Il nuovo valore per la proprietà specificata dell'oggetto specificato livello di registrazione personalizzato.  
  
 Per un elenco di valori validi per i profili e gli eventi, vedere [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).  
  
 Il *property_value* è un **bigint**.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="return-codes"></a>Codici restituiti  
 0 (esito positivo)  
  
 Quando la stored procedure ha esito negativo viene generato un errore.  
  
## <a name="result-set"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte le condizioni che causano la mancata riuscita della stored procedure.  
  
-   L'utente non dispone delle autorizzazioni necessarie.  
  
  
