---
title: catalog.check_schema_version | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 69e47e57b6732fa5c616c9ef2ddf165d394ddd14
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331855"
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Determina se lo schema del catalogo SSISDB e i file binari (assembly ISServerExec e SQLCLR) di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono compatibili.  
  
 ISServerExec.exc registra un messaggio di errore quando lo schema e i file binari sono incompatibili.  
  
 La versione dello schema SSISDB viene incrementata quando lo schema cambia durante l'applicazione di patch e aggiornamenti. È consigliabile eseguire questa stored procedure dopo il ripristino di un backup di SSISDB per assicurarsi che lo schema e i file binari siano compatibili.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @use32bitruntime= ] *use32bitruntime*  
 Quando il parametro è impostato su **True**, viene chiamata la versione a 32 bit di dtexec. *use32bitruntime* è di tipo **Bool**.  
  
## <a name="result-set"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria l'autorizzazioni seguente:  
  
-   Appartenenza al ruolo del database **ssis_admin**.  
  
  
