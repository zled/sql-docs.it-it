---
title: Catalog. set_object_parameter_value (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: fb887543-f92f-404d-9495-a1dd23a6716e
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3a5dc70b1e955b3c702dc9e9dbe4776cc4ebd5ac
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetobjectparametervalue-ssisdb-database"></a>catalog.set_object_parameter_value (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene impostato il valore di un parametro nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Associa il valore di una variabile di ambiente o assegna un valore letterale che viene utilizzato per impostazione predefinita, quando nessun altro valore assegnato.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.set_object_parameter_value [@object_type =] object_type   
    , [@folder_name =] folder_name   
    , [@project_name =] project_name   
    , [@parameter_name =] parameter _name   
    , [@parameter_value =] parameter_value   
 [  , [@object_name =] object_name ]  
 [  , [@value_type =] value_type ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [@object_type =] *object_type*  
 Tipo di parametro. Utilizzare il valore `20` per indicare un parametro del progetto o il valore `30` per indicare un parametro del pacchetto. Il *object_type* è **smallInt**.  
  
 [@folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto il parametro. Il *nome_cartella* è **nvarchar (128)**.  
  
 [@project_name =] *project_name*  
 Nome del progetto in cui è contenuto il parametro. Il *project_name* è **nvarchar (128)**.  
  
 [@parameter_name =] *parameter_name*  
 Nome del parametro. Il *parameter_name* è **nvarchar (128)**.  
  
 [@parameter_value =] *parameter_value*  
 Valore del parametro. Il *parameter_value* è **sql_variant**.  
  
 [@object_name =] *object_name*  
 Nome del pacchetto. Questo argomento è necessario quando il parametro è un parametro del pacchetto. Il *object_name* è **nvarchar (260)**.  
  
 [@value_type =] *value_type*  
 Tipo di valore del parametro. Utilizzare il carattere `V` per indicare che *parameter_value* è un valore letterale che viene utilizzato per impostazione predefinita, quando nessun altro valore assegnato prima dell'esecuzione. Utilizzare il carattere `R` per indicare che *parameter_value* è un valore di riferimento ed è stata impostata sul nome di una variabile di ambiente. Questo argomento è facoltativo. Per impostazione predefinita, viene utilizzato il carattere `V`. Il *value_type* è **char (1)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono determinare la generazione di un errore da parte della stored procedure:  
  
-   Tipo di parametro non valido  
  
-   Nome del progetto non valido  
  
-   Per parametri del pacchetto, nome del pacchetto non valido  
  
-   Tipo di valore non valido  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Osservazioni  
  
-   Se non *value_type* viene specificato un valore letterale per *parameter_value* viene utilizzato per impostazione predefinita. Quando viene utilizzato un valore letterale, la *value_set* nel [object_parameters](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) visualizzazione è impostata su `1`. Un valore di parametro NULL non è consentito.  
  
-   Se *value_type* contiene il carattere `R`, che indica un valore di riferimento, *parameter_value* fa riferimento al nome di una variabile di ambiente.  
  
-   Il valore `20` possono essere utilizzati per *object_type* per indicare un parametro del progetto. In questo caso, un valore per *object_name* non è necessario e qualsiasi valore specificato per *object_name* viene ignorato. Questo valore viene utilizzato quando l'utente desidera impostare un parametro del progetto.  
  
-   Il valore `30` possono essere utilizzati per *object_type* per indicare un parametro del pacchetto. In questo caso, un valore per *object_name* viene utilizzato per indicare il pacchetto corrispondente. Se *object_name* viene omesso, la stored procedure restituisce un errore e termina.  
  
  
