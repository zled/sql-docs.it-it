---
title: Catalog. revoke_permission (Database SSISDB) | Documenti Microsoft
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
- revoke_permission stored procedure [Integration Services]
- catalog.revoke_permission stored procedure [Integration Services]
ms.assetid: 850b9c26-5c7c-47b9-a61c-5cf9bb5948cf
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f058368bdd39b31a569d8810cccfc4d03d9f875e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrevokepermission-ssisdb-database"></a>catalog.revoke_permission (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene revocata un'autorizzazione su un oggetto a protezione diretta nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
revoke_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @object_type =] *object_type*  
 Tipo di oggetto a protezione diretta. Tipi di oggetti a protezione diretta sono inclusi cartelle (`1`), progetti (`2`), ambiente (`3`) e l'operazione (`4`). Il *object_type* è **smallint***.*  
  
 [ @object_id =] *object_id*  
 Identificatore (ID) univoco dell'oggetto a protezione diretta. Il *object_id* è **bigint**.  
  
 [ @principal_id =] *principal_id*  
 ID dell'entità a cui revocare l'autorizzazione. Il *principal_id* è **int**.  
  
 [ @permission_type =] *permission_type*  
 Tipo di autorizzazione. Il *permission_type* è **smallint**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo)  
  
 1 (object_class non è valido)  
  
 2 (object_id non esiste)  
  
 3 (entità non esiste)  
  
 4 (autorizzazione non è valida)  
  
 5 (altro errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni ASSIGN_PERMISSIONS sull'oggetto  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato permission_type, la stored procedure viene rimossa l'autorizzazione viene assegnata in modo esplicito all'entità per l'oggetto. Anche se non esiste nessuna di tali istanze, tramite la routine viene restituito un valore di codice con esito positivo (`0`). Se permission_type viene omesso, la stored procedure rimuove tutte le autorizzazioni dell'entità per l'oggetto.  
  
> [!NOTE]  
>  L'entità può disporre ancora dell'autorizzazione specificata sull'oggetto se è membro di un ruolo che dispone dell'autorizzazione specificata.  
  
 Questa stored procedure consente all'utente di revocare i tipi di autorizzazione descritti nella tabella seguente:  
  
|Valore di permission_type|Nome dell'autorizzazione|Descrizione dell'autorizzazione|Tipi di oggetti applicabili|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Consente all'entità di leggere le informazioni considerate parte dell'oggetto, ad esempio le proprietà. Non consente all'entità di enumerare o leggere il contenuto di altri oggetti inseriti all'interno dell'oggetto.|Cartella, progetto, ambiente, operazione|  
|`2`|MODIFY|Consente all'entità di modificare le informazioni considerate parte dell'oggetto, ad esempio le proprietà. Non consente all'entità di modificare gli altri oggetti contenuti all'interno dell'oggetto.|Cartella, progetto, ambiente, operazione|  
|`3`|Eseguire|Consente all'entità di eseguire tutti i pacchetti nel progetto.|Progetto|  
|`4`|MANAGE_PERMISSIONS|Consente all'entità di assegnare autorizzazioni agli oggetti.|Cartella, progetto, ambiente, operazione|  
|`100`|CREATE_OBJECTS|Consente all'entità di creare oggetti nella cartella.|Cartella|  
|`101`|READ_OBJECTS|Consente all'entità di leggere tutti gli oggetti nella cartella.|Cartella|  
|`102`|MODIFY_OBJECTS|Consente all'entità di modificare tutti gli oggetti nella cartella.|Cartella|  
|`103`|EXECUTE_OBJECTS|Consente all'entità di eseguire tutti i pacchetti di tutti i progetti contenuti nella cartella.|Cartella|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Consente all'entità di gestire le autorizzazioni su tutti gli oggetti nella cartella.|Cartella|  
  
  
