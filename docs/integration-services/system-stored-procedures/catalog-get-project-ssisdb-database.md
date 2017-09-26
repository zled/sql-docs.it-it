---
title: Catalog. get_project (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f263c9e4-a7db-4888-a458-70ae99b1f729
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: adb3542d50db426d5908aa8786145406d7263ad6
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetproject-ssisdb-database"></a>catalog.get_project (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Recupera il flusso binario di un progetto che è stato distribuito nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
get_project [ @folder_name = ] folder_name , [ @project_name = ] project_name   
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto il progetto. *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto. *PROJECT_NAME* è **nvarchar (128)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Il flusso binario del progetto viene restituito come **varbinary (max)**. Non viene restituito alcun risultato se la cartella o il progetto non viene trovato.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ sul progetto  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che potrebbero causare la procedura get_project archiviati generare un errore:  
  
-   Progetto inesistente  
  
-   Cartella inesistente  
  
-   Utente senza autorizzazioni appropriate.  
  
  
