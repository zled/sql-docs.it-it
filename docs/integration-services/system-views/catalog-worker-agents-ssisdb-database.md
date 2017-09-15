---
title: Catalog.worker_agents (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d56af0ab150255c53746898a638a32112938755c
ms.contentlocale: it-it
ms.lasthandoff: 09/08/2017

---
# <a name="catalogworkeragents-ssisdb-database"></a>Catalog.worker_agents (Database SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Visualizza le informazioni per il [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] scala il lavoro.

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|L'agente di lavoro, ID di scala il lavoro.|
|IsEnabled|**bit**|Indica se è abilitata la scala il lavoro.|
|DisplayName|**nvarchar(256)**|Il nome visualizzato della scala il lavoro.|
|Description|**nvarchar(256)**|Descrizione della scala il lavoro.|
|MachineName|**nvarchar(256)**|Nome del computer di scala i thread di lavoro.|
|Tag|**nvarchar(max)**|I tag di scala Out Worker.|
|UserAccount|**nvarchar(256)**|L'account utente che esegue il servizio di scala il lavoro.|
|LastOnlineTime|**DateTimeOffset(7)**|L'ultima volta che la scala Out thread di lavoro è in linea.|

## <a name="remarks"></a>Osservazioni
Questa vista viene visualizzata una riga per ogni scala Out lavoro connessione per la scala Out Master che lavora con il catalogo SSISDB.

## <a name="permissions"></a>Permissions
Per questa vista è necessaria una delle autorizzazioni seguenti:

- L'appartenenza al **ssis_admin** ruolo del database

- L'appartenenza al **ssis_cluster_executor** ruolo del database

- L'appartenenza al **sysadmin** ruolo del server

