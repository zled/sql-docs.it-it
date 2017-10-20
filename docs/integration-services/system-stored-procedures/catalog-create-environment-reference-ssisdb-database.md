---
title: Catalog. create_environment_reference (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 496136e8a0073ba93f003d8dfa539afb48d2c5dc
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene creato un riferimento all'ambiente per un progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_location = ] reference_location  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella del progetto che fa riferimento all'ambiente. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto che fa riferimento all'ambiente. Il *project_name* è **nvarchar (128)**.  
  
 [ @environment_name =] *environment_name*  
 Nome dell'ambiente a cui viene fatto riferimento. Il *environment_name* è **nvarchar (128)**.  
  
 [ @reference_location =] *reference_location*  
 Viene indicato se l'ambiente può essere individuato nella stessa cartella del progetto (riferimento relativo) o in una cartella diversa (riferimento assoluto). Utilizzare il valore `R` per indicare un riferimento relativo. Utilizzare il valore `A` per indicare un riferimento assoluto. Il *reference_location* è **char (1)**.  
  
 [ @environment_folder_name =] *environment_folder_name*  
 Nome della cartella in cui si trova l'ambiente a cui viene fatto riferimento. Questo valore è richiesto per i riferimenti assoluti. Il *environment_folder_name* è **nvarchar (128)**.  
  
 [ @reference_id =] *reference_id*  
 Viene restituito l'identificatore univoco per il nuovo riferimento. Questo parametro è facoltativo. Il *reference_id* è **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto e autorizzazione READ sull'ambiente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome della cartella non valido  
  
-   Nome del progetto non valido  
  
-   Utente senza autorizzazioni appropriate  
  
-   Un riferimento assoluto specificato con il `A` carattere nel *reference_location* parametro, ma il nome della cartella non è stato specificato con il *environment_folder_name* parametro.  
  
## <a name="remarks"></a>Osservazioni  
 Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella e possono fare riferimento ad ambienti che si trovano in una cartella di destinazione diversa da quella del progetto. Un progetto può fare riferimento a più ambienti.  
  
  
