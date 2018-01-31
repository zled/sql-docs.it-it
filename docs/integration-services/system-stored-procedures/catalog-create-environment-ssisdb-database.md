---
title: catalog.create_environment (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87099d08212705034db52a030e2cb1012b23c1a8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene creato un ambiente nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [@folder_name =] *folder_name*  
 Nome della cartella in cui sarà contenuto l'ambiente. *folder_name* è di tipo **nvarchar(128)**.  
  
 [@environment_name =] *environment_name*  
 Nome dell'ambiente. *environment_name* è di tipo **nvarchar(128)**.  
  
 [@environment_description=] *environment_description*  
 Descrizione dell'ambiente (facoltativa). *environment_description* è di tipo **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sulla cartella  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   ruolo del database  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Impossibile trovare il nome della cartella  
  
-   Ambiente che dispone dello stesso nome già presente nella cartella specificata  
  
## <a name="remarks"></a>Remarks  
 Il nome dell'ambiente deve essere univoco all'interno della cartella.  
  
  
