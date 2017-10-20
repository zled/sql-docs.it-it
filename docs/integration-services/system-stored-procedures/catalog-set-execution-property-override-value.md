---
title: Catalog.set_execution_property_override_value | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20f2c882a78f5e60931b0152d5877898e1972d0a
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetexecutionpropertyoverridevalue"></a>catalog.set_execution_property_override_value
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Imposta il valore di una proprietà per un'istanza di esecuzione nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @execution_id =] *valore di execution_id*  
 Identificatore univoco per l'istanza di esecuzione. Il *valore di execution_id* è **bigint**.  
  
 [ @property_path =] *percorso_proprietà*  
 Percorso alla proprietà nel pacchetto. Il *percorso_proprietà* è **nvarchar (4000)**.  
  
 [ @property_value =] *property_value*  
 Valore di override da assegnare alla proprietà. Il *property_value* è **nvarchar (max)**.  
  
 [ @sensitive =] *sensibili*  
 Quando il valore è 1, la proprietà è importante e viene crittografata quando viene archiviata. Quando il valore è 0, la proprietà non è importante e il valore viene archiviato non crittografato. Il *sensibili* argomento **bit**.  
  
## <a name="remarks"></a>Osservazioni  
 Questa routine esegue la stessa funzione di **esegue l'override di proprietà** sezione il **avanzate** scheda del **Esegui pacchetto** finestra di dialogo. Il percorso della proprietà è derivato dal **percorso pacchetto** proprietà dell'attività del pacchetto.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Utente senza autorizzazioni appropriate.  
  
-   Identificatore di esecuzione non valido  
  
-   Percorso di proprietà non valido  
  
-   Il tipo di dati del valore della proprietà non corrisponde al tipo di dati della proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  
