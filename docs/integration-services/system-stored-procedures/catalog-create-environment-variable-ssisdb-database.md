---
title: Catalog. create_environment_variable (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91ed017b-6567-4bf2-b9f1-e2b5c70a5343
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 5636651cccbb43c6c1627d1f28eccd9b3f9b5b0d
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreateenvironmentvariable-ssisdb-database"></a>catalog.create_environment_variable (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crea una variabile di ambiente nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.create_environment_variable [@folder_name =] folder_name  
    , [@environment_name =] environment_name  
    , [@variable_name =] variable_name  
    , [@data_type =] data_type  
    , [@sensitive =] sensitive  
    , [@value =] value  
    , [@description =] description  
```  
  
## <a name="arguments"></a>Argomenti  
 [@folder_name =] *nome_cartella*  
 Nome della cartella in cui è contenuto l'ambiente. Il *nome_cartella* è **nvarchar (128)**.  
  
 [@environment_name =] *environment_name*  
 Nome dell'ambiente. Il *environment_name* è **nvarchar (128)**.  
  
 [@variable_name =] *nome_variabile*  
 Nome della variabile di ambiente. Il *nome_variabile* è **nvarchar (128)**.  
  
 [@data_type =] *data_type*  
 Tipo di dati della variabile. Supportati includono tipi di dati variabili dell'ambiente **booleano**, **Byte**, **DateTime**, **doppie**, **Int16**, **Int32**, **Int64**, **singolo**, **stringa**, **UInt32**e  **UInt64**. Tipi di dati della variabile di ambiente non supportati includono **Char**, **DBNull**, **oggetto**, e **Sbyte**. Il tipo di dati di *data_type* parametro **nvarchar (128)**.  
  
 [@sensitive =] *sensibili*  
 Viene indicato se nella variabile è contenuto o meno un valore importante. Utilizzare un valore pari a `1`, per indicare che il valore della variabile di ambiente è importante o, in caso contrario, un valore pari a `0`. Un valore, se importante, viene crittografato quando viene archiviato; Un valore non viene archiviato in testo non crittografato. *Sensibili* è **bit**.  
  
 [@value =] *valore*  
 Valore della variabile di ambiente. Il *valore* è **sql_variant**.  
  
 [@description =] *descrizione*  
 Descrizione della variabile di ambiente. Il *valore* è **nvarchar (1024)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'ambiente  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome della cartella, nome dell'ambiente o nome della variabile di ambiente non valido  
  
-   Nome della variabile già esistente nell'ambiente  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Osservazioni  
 Una variabile di ambiente può essere utilizzata per assegnare in modo efficace un valore a un parametro del progetto o a un parametro del pacchetto da utilizzare nell'esecuzione di un pacchetto. Le variabili di ambiente consentono l'organizzazione dei valori del parametro. I nomi della variabile devono essere univoci all'interno di un ambiente.  
  
 La stored procedure consente di convalidare il tipo di dati della variabile per assicurarsi che sia supportato dal catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!TIP]  
>  È consigliabile utilizzare il **Int16** del tipo di dati [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] anziché il non supportato **Sbyte** tipo di dati.  
  
 Il valore passato a questa stored procedure con il *valore* parametro viene convertito da un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tipo di dati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il tipo di dati in base alla tabella seguente:  
  
|Tipo di dati di Integration Services|Tipo di dati di SQL Server|  
|------------------------------------|--------------------------|  
|**Boolean**|**bit**|  
|**Byte**|**binario**, **varbinary**|  
|**DateTime**|**DateTime**, **datetime2**, **datetimeoffset**, **smalldatetime**|  
|**Double**|Numerico esatto: **decimale**, **numerico**; Numerico approssimato: **float**, **reale**|  
|**Int16**|**smallint**|  
|**Int32**|**int**|  
|**Int64**|**bigint**|  
|**Singolo**|Numerico esatto: **decimale**, **numerico**; Numerico approssimato: **float**, **reale**|  
|**String**|**varchar**, **nvarchar**, **char**|  
|**UInt32**|**int** (**int** è il mapping disponibile più vicino al **Uint32**.)|  
|**UInt64**|**bigint** (**int** è il mapping disponibile più vicino al **Uint64**.)|  
  
  

