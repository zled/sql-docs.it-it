---
title: Catalog.delete_customized_logging_level | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 0aec1e34-f30b-4e5f-bba1-c26665cf2da6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a2c53009bfbd2f0876d4cf0a01cf8fa2b5bc738e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeletecustomizedlogginglevel"></a>Catalog.delete_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Elimina un livello di registrazione personalizzato esistente. Per ulteriori informazioni sui livelli di registrazione personalizzati, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
delete_customized_logging_level [ @level_name = ] level_name  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @level_name =] *level_name*  
 Il nome dell'oggetto esistente personalizzate a livello di registrazione da eliminare.  
  
 Il *level_name* è **nvarchar (128)**.  
  
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
  
  
