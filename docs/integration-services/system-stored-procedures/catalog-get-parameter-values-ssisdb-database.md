---
title: Catalog. get_parameter_values (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b1aeaf7-c938-4aef-bafc-e4d7a82eb578
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4ad8f0c367e38581db696d2aa32afd5b92d635d2
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="cataloggetparametervalues-ssisdb-database"></a>catalog.get_parameter_values (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono risolti e recuperati i valori predefiniti del parametro da un progetto e dai pacchetti corrispondenti nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
get_parameter_values [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id  ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto il progetto. Il *nome_cartella* è **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nome del progetto in cui si trovano i parametri. Il *project_name* è **nvarchar (128)**.  
  
 [ @package_name =] *nome_pacchetto*  
 Nome del pacchetto. Specificare il nome del pacchetto per recuperare tutti i parametri del progetto e i parametri da un pacchetto specifico. Utilizzare NULL per recuperare tutti i parametri del progetto e i parametri da tutti i pacchetti. Il *nome_pacchetto* è **nvarchar (260)**.  
  
 [ @reference_id =] *reference_id*  
 Identificatore univoco di un riferimento all'ambiente. Questo parametro è facoltativo. Il *reference_id* è **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Viene restituita una tabella con il formato seguente:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Tipo di parametro. Il valore è `20` per un parametro del progetto e `30` per un parametro del pacchetto.|  
|parameter_data_type|**nvarchar (128)**|Tipo di dati del parametro.|  
|parameter_name|**sysname**|Nome del parametro.|  
|parameter_value|**sql_variant**|Valore del parametro.|  
|sensitive|**bit**|Quando il valore è `1`, il valore del parametro è importante. In caso contrario, il valore è `0`.|  
|required|**bit**|Quando il valore è `1`, il valore del parametro è necessario per avviare l'esecuzione. In caso contrario, il valore è `0`.|  
|value_set|**bit**|Quando il valore è `1`, il valore del parametro è stato assegnato. In caso contrario, il valore è `0`.|  
  
> [!NOTE]  
>  I valori letterali vengono visualizzati non crittografati. **NULL** viene visualizzato al posto dei valori sensibili.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ sul progetto e, se applicabile, autorizzazione READ sull'ambiente a cui si fa riferimento  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Impossibile trovare il pacchetto nella cartella o progetto specificato.  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Riferimento all'ambiente specificato inesistente.  
  
  
