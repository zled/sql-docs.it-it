---
title: catalog.configure_catalog (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 72690c61-f462-4c25-9fce-08a687b0bd41
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 739144b31538b088b278563e26b503858ceafb75
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="catalogconfigurecatalog-ssisdb-database"></a>catalog.configure_catalog (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene configurato il catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] impostando una proprietà del catalogo su un valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```sql
catalog.configure_catalog [ @property_name = ] property_name , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @property_name = ] *property_name*  
 Nome della proprietà del catalogo. *property_name* è di tipo **nvarchar(255)**. Per altre informazioni sulle proprietà disponibili, vedere [catalog.catalog_properties &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
 [ @property_value = ] *property_value*  
 Valore della proprietà del catalogo. *property_value* è di tipo **nvarchar(255)**. Per altre informazioni sui valori delle proprietà, vedere [catalog.catalog_properties &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Remarks  
 Questa stored procedure determina se *property_value* è valido per ogni *property_name*.  
  
 La stored procedure può essere eseguita solo se non esiste alcuna esecuzione attiva, ad esempio in sospeso, in coda, in esecuzione e sospesa.  
  
 Mentre viene configurato il catalogo, tutte le relative altre stored procedure non vengono completate e generano il messaggio di errore "Server attualmente in fase di esecuzione".
  
 Quando il catalogo viene configurato, nel log delle operazioni viene scritta una voce.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Proprietà inesistente  
  
-   Valore della proprietà non valido.  
  
  
