---
title: catalog.set_environment_property (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 718fb5596fb85876fae5023603039b8bf4ef177b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogsetenvironmentproperty-ssisdb-database"></a>catalog.set_environment_property (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene impostata la proprietà di un ambiente nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name = ] *folder_name*  
 Nome della cartella in cui è contenuto l'ambiente. *folder_name* è di tipo **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Nome dell'ambiente. *environment_name* è di tipo **nvarchar(128)**.  
  
 [ @property_name = ] *property_name*  
 Nome di una proprietà dell'ambiente. *property_name* è di tipo **nvarchar(128)**.  
  
 [ @property_value = ] *property_value*  
 Valore della proprietà dell'ambiente. *property_value* è di tipo **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome della cartella non valido  
  
-   Nome della proprietà non valido  
  
-   Nome dell'ambiente non valido  
  
## <a name="remarks"></a>Osservazioni  
 In questa versione è possibile impostare solo la proprietà `Description`. Il valore della proprietà `Description` non può superare i 4000 caratteri.  
  
  
