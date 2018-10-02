---
title: catalog.master_properties (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85b3388be32ac33382ad34f12ec135e84313cb33
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687443"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Consente di visualizzare le proprietà di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master.

|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Nome della proprietà di Scale Out Master.|  
|property_value|**nvarchar(max)**|Valore della proprietà di Scale Out Master.|

## <a name="remarks"></a>Remarks
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
