---
title: Catalog. validate_project (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5270689a-46d4-4847-b41f-3bed1899e955
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 83439015694f4235af4a67e994e916651ec63cc1
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidateproject-ssisdb-database"></a>catalog.validate_project (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene convalidato in modo asincrono un progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
validate_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @validate_type = ] validate_type  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome di una cartella in cui è contenuto il progetto. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto. Il *project_name* è **nvarchar (128)**.  
  
 [ @validate_type =] *validate_type*  
 Viene indicato il tipo di convalida da eseguire. Utilizzare il carattere `F` per eseguire una convalida completa. Il *validate_type* è **char (1)**.  
  
 [ @validation_id =] *validation_id*  
 Viene restituito l'identificatore (ID) univoco della convalida. Il *validation_id* è **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Viene indicato se il runtime a 32 bit deve essere utilizzato per eseguire il pacchetto in un sistema operativo a 64 bit. Utilizzare il valore di `1` per eseguire il pacchetto con il runtime a 32 bit quando in esecuzione in un sistema operativo a 64 bit. Utilizzare il valore pari a `0` per eseguire il pacchetto con il runtime a 64 bit quando in esecuzione in un sistema operativo a 64 bit. Questo parametro è facoltativo. Il *use32bitruntime* è **bit**.  
  
 [ @environment_scope =] *environment_scope*  
 Vengono indicati i riferimenti all'ambiente considerati dalla convalida. Quando il valore è `A`, tutti i riferimenti all'ambiente associati al progetto sono inclusi nella convalida. Quando il valore è `S`, è incluso solo un singolo riferimento all'ambiente. Quando il valore è `D`, non è incluso alcun riferimento all'ambiente e ogni parametro deve disporre di un valore predefinito letterale per passare la convalida. Questo parametro è facoltativo. Per impostazione predefinita, verrà utilizzato il carattere `D`. Il *environment_scope* è **char (1)**.  
  
 [ @reference_id =] *reference_id*  
 ID univoco del riferimento all'ambiente. Questo parametro è obbligatorio solo quando un singolo riferimento all'ambiente è incluso nella convalida, quando *environment_scope* è `S`. Il *reference_id* è **bigint**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 L'output dei passaggi di convalida viene restituito sotto forma di sezioni diverse del set di risultati.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ sul progetto e, se applicabile, autorizzazioni READ su ambienti a cui si fa riferimento  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Convalida non riuscita per uno o più pacchetti nel progetto  
  
-   Convalida non riuscita se in uno o più ambienti utilizzati come riferimento inclusi nella convalida non sono contenute variabili di riferimento  
  
-   Tipo di convalida specificato non valido  
  
-   Nome del progetto o ID di riferimento all'ambiente non valido  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Osservazioni  
 La convalida consente di identificare i problemi che impediscono il completamento dell'esecuzione dei pacchetti nel progetto. Utilizzare il [Catalog. validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) o [Catalog. Operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) viste per monitorare lo stato di convalida.  
  
 Solo ambienti che sono accessibili dall'utente possono essere utilizzati nella convalida. L'output della convalida viene inviato al client come set di risultati.  
  
 In questa versione la convalida del progetto non supporta la convalida della dipendenza.  
  
 Tramite la convalida completa viene confermato che tutte le variabili di ambiente a cui si fa riferimento si trovano all'interno degli ambienti di riferimento inclusi nella convalida. Tramite la convalida completa viene generato un elenco di riferimenti all'ambiente che non sono validi e variabili di ambiente a cui si fa riferimento che non sono state trovate in alcun ambiente di riferimento incluso nella convalida.  
  
  
