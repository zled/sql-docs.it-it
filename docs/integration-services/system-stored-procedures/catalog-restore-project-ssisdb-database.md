---
title: Catalog. restore_project (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 23074fc664591411666315036e3493e1b7b26134
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene ripristinata la versione precedente di un progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto il progetto. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project Name =] *project_name*  
 Nome del progetto. Il *project_name* è **nvarchar (128)**.  
  
 [ @object_version_lsn =] *valore object_version_lsn*  
 Versione del progetto. Il *valore object_version_lsn* è **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Vengono restituiti i dettagli di progetto come **varbinary (max)** come parte del set di risultati se la *project_name* viene trovato.  
  
 **SET di risultati** viene restituito se il progetto non è possibile ripristinare la cartella specificata.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Versione del progetto inesistente o non corrispondente al nome del progetto  
  
-   Progetto inesistente  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene ripristinato un progetto, a tutti i parametri vengono assegnati i valori predefiniti mentre tutti i riferimenti all'ambiente rimangono invariati. Il numero massimo di versioni del progetto vengono mantenute nel catalogo è determinato dalla proprietà del catalogo **MAX_VERSIONS_PER_PROJECT**, come illustrato nel [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) visualizzazione.  
  
> [!WARNING]  
>  I riferimenti all'ambiente potrebbero non essere più validi dopo il ripristino di un progetto.  
  
  
