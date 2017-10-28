---
title: Risolvere i problemi relativi a processi multiserver che usano proxy | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6a02ace1fe1ba285bc340b9dca87112325f97210
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Risolvere i problemi relativi a processi multiserver che utilizzano proxy
I processi distribuiti con passaggi associati a un proxy vengono eseguiti nel contesto dell'account proxy nel server di destinazione. Se si verificano errori quando i passaggi di processo che usano account proxy vengono scaricati dal server master, controllare la colonna **error_message** nella tabella **sysdownloadlist** del database **msdb** per verificare l'eventuale presenza dei messaggi di errore seguenti:  
  
-   "Per questo passaggio del processo è necessario un account proxy, ma l'individuazione dei proxy è disabilitata nel server di destinazione."  
  
    Per risolvere questo problema, impostare la sottochiave del registro **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** su **1 (vero)**. Per impostazione predefinita, questa sottochiave è impostata su **0** (**falso**). Il valore di **MSSQL.**\<*n*> è il nome dell'istanza, ad esempio, **MSSQL.1** o **MSSQL.3**.  
  
-   "Impossibile trovare il proxy."  
  
    Per risolvere il problema, verificare che nel server di destinazione sia disponibile un account proxy con lo stesso nome dell'account proxy del server master utilizzato per l'esecuzione del passaggio del processo.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)  
  

