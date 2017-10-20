---
title: Catalog.set_customized_logging_level_description | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3899e02c6b1eaa2cc76ad4411d9be3aded817728
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetcustomizedloggingleveldescription"></a>Catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Modifica la descrizione di un livello di registrazione personalizzato esistente. Per ulteriori informazioni sui livelli di registrazione personalizzati, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @level_name =] *level_name*  
 Il nome di un livello di registrazione personalizzato.  
  
 Il *level_name* è **nvarchar (128)**.  
  
 [ @level_description =] *level_description*  
 La nuova descrizione per il livello di registrazione personalizzato.  
  
 Il *level_description* è **nvarchar (1024)**.  
  
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
  
  
