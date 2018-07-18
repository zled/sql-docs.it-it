---
title: Risolvere i problemi relativi a processi multiserver che usano proxy | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 107b6f5fb2605a8c8091006abad976cceea24392
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33044908"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Risolvere i problemi relativi a processi multiserver che utilizzano proxy
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

I processi distribuiti con passaggi associati a un proxy vengono eseguiti nel contesto dell'account proxy nel server di destinazione. Se si verificano errori quando i passaggi di processo che usano account proxy vengono scaricati dal server master, controllare la colonna **error_message** nella tabella **sysdownloadlist** del database **msdb** per verificare l'eventuale presenza dei messaggi di errore seguenti:  
  
-   "Per questo passaggio del processo è necessario un account proxy, ma l'individuazione dei proxy è disabilitata nel server di destinazione."  
  
    Per risolvere questo problema, impostare la sottochiave del Registro di sistema **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>** \SQLServerAgent\AllowDownloadedJobsToMatchProxyName** su **1 (vero)**. Per impostazione predefinita, questa sottochiave è impostata su **0** (**falso**). Il valore di **MSSQL.**\<*n*> è il nome dell'istanza, ad esempio, **MSSQL.1** o **MSSQL.3**.  
  
-   "Impossibile trovare il proxy."  
  
    Per risolvere il problema, verificare che nel server di destinazione sia disponibile un account proxy con lo stesso nome dell'account proxy del server master utilizzato per l'esecuzione del passaggio del processo.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)  
  
