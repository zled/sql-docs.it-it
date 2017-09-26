---
title: Catalog.create_customized_logging_level | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 20b3ba0a-126f-49bf-b70f-61b2a0fcb750
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 126fa0af811033bb0be035b1f4c550620c696bb3
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreatecustomizedlogginglevel"></a>Catalog.create_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo livello di registrazione personalizzato. Per ulteriori informazioni sui livelli di registrazione personalizzati, vedere [Integration Services &#40; SSIS &#41; Registrazione](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
create_customized_logging_level [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
    , [ @profile_value = ] profile_value  
    , [ @event_value = ] event_value  
    , [ @level_id = ] level_id OUT  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @level_name =] *level_name*  
 Il nome esistente nuovo livello di registrazione personalizzato.  
  
 Il *level_name* è **nvarchar (128)**.  
  
 [ @level_description =] *level_description*  
 La descrizione esistente nuovo livello di registrazione personalizzato.  
  
 Il *level_description* è **nvarchar (1024)**.  
  
 [ @profile_value =] *profile_value*  
 Le statistiche che si desidera impostare il nuovo personalizzato a livello di registrazione per l'accesso.  
  
 I valori validi per le statistiche seguenti: Questi valori corrispondono ai valori nel **statistiche** scheda della finestra di **gestione livello di registrazione personalizzato** la finestra di dialogo.  
  
-   Esecuzione = 0  
  
-   Volume = 1  
  
-   Prestazioni = 2  
  
 Il *profile_value* è un **bigint**.  
  
 [ @event_value =] *event_value*  
 Gli eventi che si desidera impostare il nuovo personalizzate a livello di registrazione per l'accesso.  
  
 I valori validi per gli eventi seguenti: Questi valori corrispondono ai valori nel **eventi** scheda della finestra di **gestione livello di registrazione personalizzato** la finestra di dialogo.  
  
|Eventi senza un contesto dell'evento|Eventi con un contesto dell'evento|  
|----------------------------------|-------------------------------|  
|OnVariableValueChanged = 0<br /><br /> OnExecutionStatusChanged = 1<br /><br /> OnPreExecute = 2<br /><br /> OnPostExecute = 3<br /><br /> OnPreValidate = 4<br /><br /> OnPostValidate = 5<br /><br /> OnWarning = 6<br /><br /> OnInformation = 7<br /><br /> OnError = 8<br /><br /> OnTaskFailed = 9<br /><br /> OnProgress = 10<br /><br /> OnQueryCancel = 11<br /><br /> OnBreakpointHit = 12<br /><br /> OnCustomEvent = 13<br /><br /> Diagnostica = 14<br /><br /> DiagnosticEx = 15<br /><br /> NonDiagnostic = 16|OnVariableValueChanged_IncludeContext = 32<br /><br /> OnExecutionStatusChanged_IncludeContext = 33<br /><br /> OnPreExecute_IncludeContext = 34<br /><br /> OnPostExecute_IncludeContext = 35<br /><br /> OnPreValidate_IncludeContext = 36<br /><br /> OnPostValidate_IncludeContext = 37<br /><br /> OnWarning_IncludeContext = 38<br /><br /> OnInformation_IncludeContext = 39<br /><br /> OnError_IncludeContext = 40<br /><br /> OnTaskFailed_IncludeContext = 41<br /><br /> OnProgress_IncludeContext = 42<br /><br /> OnQueryCancel_IncludeContext = 43<br /><br /> OnBreakpointHit_IncludeContext = 44<br /><br /> OnCustomEvent_IncludeContext = 45<br /><br /> Diagnostic_IncludeContext = 46<br /><br /> DiagnosticEx_IncludeContext = 47<br /><br /> NonDiagnostic_IncludeContext = 48|  
  
 Il *event_value* è un **bigint**.  
  
 [ @level_id =] *level_id* OUT  
 L'id del nuovo livello di registrazione personalizzato.  
  
 Il *level_id* è un **bigint**.  
  
## <a name="remarks"></a>Osservazioni  
 Per combinare più valori in Transact-SQL per il *profile_value* o *event_value* argomento, seguire questo esempio. Per acquisire lo OnError (8) e gli eventi DiagnosticEx (15), la formula per calcolare *event_value* è `2^8 + 2^15 = 33024`.  
  
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
  
  
