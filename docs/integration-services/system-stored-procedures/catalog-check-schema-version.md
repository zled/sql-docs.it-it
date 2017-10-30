---
title: Catalog.check_schema_version | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 56eacb6ed209f34f65ae406fe4dd520284b79e5b
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Determina se lo schema del catalogo SSISDB e i file binari (assembly ISServerExec e SQLCLR) di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono compatibili.  
  
 ISServerExec.exc registra un messaggio di errore quando lo schema e i file binari sono incompatibili.  
  
 La versione dello schema SSISDB viene incrementata quando lo schema cambia durante l'applicazione di patch e aggiornamenti. È consigliabile eseguire questa stored procedure dopo il ripristino di un backup di SSISDB per assicurarsi che lo schema e i file binari siano compatibili.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @use32bitruntime=] *use32bitruntime*  
 Quando il parametro è impostato su **True**, viene chiamata la versione a 32 bit di dtexec. Il *use32bitruntime* è un **Bool**.  
  
## <a name="result-set"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Permissions  
 Per questa stored procedure è necessaria l'autorizzazioni seguente:  
  
-   L'appartenenza al **ssis_admin** ruolo del database.  
  
  

