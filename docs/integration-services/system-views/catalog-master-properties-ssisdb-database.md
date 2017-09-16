---
title: Catalog.master_properties (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: 0fcbdca57c7764eaec758d2ad9ef3ab8675a3a9b
ms.contentlocale: it-it
ms.lasthandoff: 09/08/2017

---
# <a name="catalogmasterproperties-ssisdb-database"></a>Catalog.master_properties (Database SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Visualizza le proprietà del [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] scala Out Master.

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Nome della proprietà master di scalabilità.|  
|property_value|**nvarchar(max)**|Il valore della proprietà master di scalabilità.|

## <a name="remarks"></a>Osservazioni
Questa vista viene visualizzata una riga per ogni proprietà master di scalabilità. Nelle proprietà visualizzate da questa vista sono inclusi gli elementi seguenti:

|Nome proprietà|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Consente di individuare SQL Server in cui i database di log in.|
|**LAST_ONLINE_TIME**|Ora dell'ultima quando scala Out Master è online.|
|**MACHINE_IP**|L'indirizzo IP del computer.|
|**NOME_COMPUTER**|Nome del computer.|
|**MASTER_ADDRESS**|L'endpoint di scala Out Master.|
|**MASTER_SERVICE_PORT**|La porta nell'endpoint di scala Out Master.|
|**SSLCERT_THUMBPRINT**|L'identificazione personale del certificato di scala Out Master.|

## <a name="permissions"></a>Permissions
Autorizzazione per la visualizzazione di lettura a tutti i membri del ruolo di database public. 

