---
title: Catalog. configure_catalog (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 15bec231bf1de825cea952e07827074d56751386
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="catalogconfigurecatalog-ssisdb-database"></a>catalog.configure_catalog (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene configurato il catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] impostando una proprietà del catalogo su un valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @property_name =] *property_name*  
 Nome della proprietà del catalogo. Il *property_name* è **nvarchar (255)**. Per ulteriori informazioni sulle proprietà disponibili, vedere [Catalog. catalog_properties &#40; Database SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value =] *property_value*  
 Valore della proprietà del catalogo. Il *property_value* è **nvarchar (255)**. Per ulteriori informazioni sui valori delle proprietà, vedere [Catalog. catalog_properties &#40; Database SSISDB &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure determina se il *property_value* è valido per ogni *property_name*.  
  
 La stored procedure può essere eseguita solo se non esiste alcuna esecuzione attiva, ad esempio in sospeso, in coda, in esecuzione e sospesa.  
  
 Mentre viene configurato il catalogo, tutte le relative altre stored procedure esito negativo con messaggio di errore "Server è attualmente configurato."
  
 Quando il catalogo viene configurato, nel log delle operazioni viene scritta una voce.  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Proprietà inesistente  
  
-   Valore della proprietà non valido.  
  
  

