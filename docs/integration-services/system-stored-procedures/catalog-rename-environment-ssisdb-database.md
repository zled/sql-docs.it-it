---
title: Catalog. rename_environment (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: c73d7452-31c5-4f4e-afcc-e9eca760c826
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 504d3ca0f18c9ea11105ebb575d2f5db449f91e4
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenameenvironment-ssisdb-database"></a>catalog.rename_environment (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene rinominato un ambiente nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.rename_environment [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @new_environment_name= ] new_environment_name  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto l'ambiente. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nome originale dell'ambiente. Il *environment_name* è **nvarchar (128)**.  
  
 [ @new_environment_name =] *new_environment_name*  
 Nuovo nome dell'ambiente. Il *new_environment_name* è **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni MODIFY sull'ambiente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome originale dell'ambiente non valido  
  
-   Nome nuovo già utilizzato in un ambiente esistente  
  
## <a name="remarks"></a>Osservazioni  
 I riferimenti all'ambiente dai progetti non vengono aggiornati automaticamente quando si rinomina l'ambiente, pertanto è necessario aggiornarli di conseguenza. Questa stored procedure verrà completata anche se i riferimenti all'ambiente vengono interrotti modificando il nome dell'ambiente. I riferimenti all'ambiente devono essere aggiornati dopo il completamento di questa stored procedure.  
  
> [!NOTE]  
>  Quando un riferimento all'ambiente non è valido, la convalida e l'esecuzione dei pacchetti corrispondenti in cui vengono utilizzati tali riferimenti non verranno completate.  
  
  
