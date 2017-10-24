---
title: Catalog. validate_package (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 869b758e3ac922762c293eb8aa9a9537a4397bd6
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene convalidato in modo asincrono un pacchetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql
catalog.validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nella della cartella in cui è contenuto il pacchetto. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto in cui è contenuto il pacchetto. Il *project_name* è **nvarchar (128)**.  
  
 [ @package_name =] *nome_pacchetto*  
 Nome del pacchetto. Il *nome_pacchetto* è **nvarchar (260)**.  
  
 [ @validation_id =] *validation_id*  
 Viene restituito l'identificatore (ID) univoco della convalida. Il *validation_id* è **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Viene indicato se il runtime a 32 bit deve essere utilizzato per eseguire il pacchetto in un sistema operativo a 64 bit. Utilizzare il valore di `1` per eseguire il pacchetto con il runtime a 32 bit quando in esecuzione in un sistema operativo a 64 bit. Utilizzare il valore pari a `0` per eseguire il pacchetto con il runtime a 64 bit quando in esecuzione in un sistema operativo a 64 bit. Questo parametro è facoltativo. Il *use32bitruntime* è **bit**.  
  
 [ @environment_scope =] *environment_scope*  
 Vengono indicati i riferimenti all'ambiente considerati dalla convalida. Quando il valore è `A`, tutti i riferimenti all'ambiente associati al progetto sono inclusi nella convalida. Quando il valore è `S`, è incluso solo un singolo riferimento all'ambiente. Quando il valore è `D`, non è incluso alcun riferimento all'ambiente e ogni parametro deve disporre di un valore predefinito letterale per passare la convalida. Questo parametro è facoltativo. Il carattere `D` viene utilizzato per impostazione predefinita. Il *environment_scope* è **char (1)**.  
  
 [ @reference_id =] *reference_id*  
 ID univoco del riferimento all'ambiente. Questo parametro è obbligatorio solo quando un singolo riferimento all'ambiente è incluso nella convalida, quando *environment_scope* è `S`. Il *reference_id* è **bigint**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ sul progetto e, se applicabile, autorizzazioni READ su ambienti a cui si fa riferimento  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome del progetto o del pacchetto non valido  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Uno o più ambienti utilizzati come riferimento inclusi nella convalida in cui non sono contenute variabili di riferimento  
  
-   Convalida del pacchetto non completata  
  
-   Ambiente a cui viene fatto riferimento non disponibile  
  
-   Impossibile trovare variabili utilizzate come riferimento negli ambienti a cui viene fatto riferimento inclusi nella convalida  
  
-   Riferimento alla variabili effettuato nei parametri del pacchetto, ma nessuna inclusione di ambienti di riferimento nella convalida.  
  
## <a name="remarks"></a>Osservazioni  
 La convalida consente di identificare i problemi che potrebbero impedire il completamento dell'esecuzione del pacchetto. Utilizzare il [Catalog. validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) o [Catalog. Operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) viste per monitorare lo stato di convalida.  
  
  
