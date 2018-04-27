---
title: catalog.move_environment (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c488ab03eb895257e90367db7c06476ba96d2c6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="catalogmoveenvironment-ssisdb-database"></a>catalog.move_environment (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene spostato un ambiente da una cartella a un'altra all'interno del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @source_folder = ] *source_folder*  
 Nome della cartella di origine, in cui si trova l'ambiente prima dello spostamento. *source_folder* è di tipo **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Nome dell'ambiente che deve essere spostato. *environment_name* è di tipo **nvarchar(128)**.  
  
 [ @destination_folder = ] *destination_folder*  
 Nome della cartella di destinazione, in cui si trova l'ambiente dopo lo spostamento. *destination_folder* è di tipo **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Ambiente inesistente nella cartella di origine  
  
-   Ambiente con stesso nome già presente nella cartella di destinazione  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Remarks  
 I riferimenti all'ambiente dai progetti non seguono l'ambiente durante lo spostamento, pertanto è necessario aggiornarli di conseguenza. Questa stored procedure verrà completata anche se i riferimenti all'ambiente vengono interrotti spostando un ambiente. I riferimenti all'ambiente devono essere aggiornati dopo il completamento di questa stored procedure.  
  
> [!NOTE]  
>  Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella. Tali riferimenti fanno riferimento agli ambienti che si trovano in una cartella diversa da quella del progetto.  
  
  
