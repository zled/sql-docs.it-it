---
title: Catalog.deploy_packages | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8e861df6-d103-4d84-8438-e822533f6849
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1839430dd7fb83ab16c4de46011819e3ce28e835
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeploypackages"></a>Catalog.deploy_packages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di distribuire uno o più pacchetti in una cartella di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] del catalogo o aggiorna un pacchetto esistente che è stato distribuito in precedenza.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
[catalog].[deploy_packages]     [ @folder_name = ] folder_name,    [ @project_name = ] project_name,    [ @packages_table = ] packages_table,     [ @operation_id OUTPUT ] operation_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Il nome del progetto nella cartella. Il *project_name* è **nvarchar (128)**.  
  
 [ @packages_table =] *packages_table*  
 Il contenuto binario di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] file (con estensione dtsx) del pacchetto. Il *packages_table* è **[catalog]. [ Package_Table_Type]**  
  
 [ @operation_id =] *operation_id*  
 Viene restituito l'identificatore univoco dell'operazione di distribuzione. Il *operation_id* è **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni CREATE_OBJECTS il progetto o le autorizzazioni di modifica del pacchetto per aggiornare un pacchetto.  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono determinare la generazione di un errore da parte della stored procedure:  
  
-   Un parametro fa riferimento a un oggetto che non esiste, un parametro che tenta di creare un oggetto già esistente o un parametro non è valido in un altro modo.  
  
-   Utente senza autorizzazioni sufficienti.  
  
  

