---
title: catalog.master_properties (database SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28f72cd6a5ea50bdc310d89bf16dbe498e06a638
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Consente di visualizzare le proprietà di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master.

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Nome della proprietà di Scale Out Master.|  
|property_value|**nvarchar(max)**|Valore della proprietà di Scale Out Master.|

## <a name="remarks"></a>Osservazioni
Questa vista mostra una riga per ogni proprietà di Scale Out Master. Nelle proprietà visualizzate da questa vista sono inclusi gli elementi seguenti:

|Nome proprietà|Descrizione|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Server SQL in cui si trova il database del log.|
|**LAST_ONLINE_TIME**|Ultima esecuzione online di Scale Out Master.|
|**MACHINE_IP**|IP del computer.|
|**MACHINE_NAME**|Nome del computer.|
|**MASTER_ADDRESS**|Endpoint di Scale Out Master.|
|**MASTER_SERVICE_PORT**|Porta nell'endpoint di Scale Out Master.|
|**SSLCERT_THUMBPRINT**|Identificazione personale di Scale Out Master.|

## <a name="permissions"></a>Permissions
Tutti i membri del ruolo del database pubblico hanno l'autorizzazione di lettura per questa vista. 
