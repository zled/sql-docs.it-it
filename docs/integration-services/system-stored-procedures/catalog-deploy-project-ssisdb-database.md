---
title: Catalog. deploy_project (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2e3439b4-7226-4b61-a993-7a1d161eac7e
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 5682cd23cb65e097bccb8cc69d5f2ec88ece7709
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogdeployproject-ssisdb-database"></a>catalog.deploy_project (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene distribuito un progetto in una cartella del catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] o viene aggiornato un progetto esistente distribuito precedentemente.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.deploy_project [@folder_name =] folder_name   
      , [@project_name =] project_name   
      , [@project_stream =] projectstream   
    [ , [@operation_id ] = operation_id OUTPUT ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [@folder_name =] *nome_cartella*  
 Il nome della cartella in cui viene distribuito il progetto. Il *nome_cartella* è **nvarchar (128)**.  
  
 [@project_name =] *project_name*  
 Nome del progetto nuovo o aggiornato nella cartella. Il *project_name* è **nvarchar (128)**.  
  
 [@projectstream =] *projectstream*  
 Contenuto binario di un file di distribuzione progetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (estensione ispac).  
  
 È possibile utilizzare un'istruzione SELECT con la funzione OPENROWSET e il provider BULK per set di righe per recuperare il contenuto binario del file. Per un esempio, vedere [distribuire Integration Services (SSIS) progetti e pacchetti](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md). Per ulteriori informazioni su OPENROWSET, vedere [OPENROWSET &#40; Transact-SQL &#41; ](../../t-sql/functions/openrowset-transact-sql.md).  
  
 Il *projectstream* è **varbinary (max)**  
  
 [@operation_id =] *operation_id*  
 Viene restituito l'identificatore univoco dell'operazione di distribuzione. Il *operation_id* è **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni CREATE_OBJECTS sulla cartella per distribuire un nuovo progetto o autorizzazioni MODIFY sul progetto per aggiornare un progetto  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono determinare la generazione di un errore da parte della stored procedure:  
  
-   Parametro che fa riferimento a un oggetto inesistente, parametro che tenta di creare un oggetto già esistente o parametro non valido in alcuni altri modi  
  
-   Il valore del parametro  *@project_name*  non corrisponde al nome del progetto nel file di distribuzione  
  
-   Utente senza autorizzazioni sufficienti.  
  
## <a name="remarks"></a>Osservazioni  
 Durante la distribuzione o aggiornamento di un progetto, il livello di protezione dei singoli pacchetti non viene controllato dalla stored procedure.  
  
  
