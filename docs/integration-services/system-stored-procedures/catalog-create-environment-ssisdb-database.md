---
title: catalog.create_environment (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b0ff9e5c2a5874b5ff01e8da19fa6015e28b5e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778559"
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
  
## <a name="permissions"></a>Permissions  
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
  
  
