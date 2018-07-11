---
title: MSSQL_ENG014160 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 416d632ab8c4ba1efb7b38e4cd4912f5cd5b0ca1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148592"
---
# <a name="mssqleng014160"></a>MSSQL_ENG014160
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14160|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|È stata impostata la soglia [%s:%s] per la pubblicazione [%s]. Una o più sottoscrizioni della pubblicazione sono scadute.|  
  
## <a name="explanation"></a>Spiegazione  
 La replica consente di attivare avvisi per numerose condizioni, tra cui la scadenza imminente della sottoscrizione. Le sottoscrizioni possono scadere se non vengono sincronizzate entro il *periodo di memorizzazione*specificato. Per altre informazioni, vedere [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 Quando si attiva un avviso utilizzando Monitoraggio replica o [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), viene specificata una soglia che determina quando è generato l'avviso. Quando tale soglia viene raggiunta o superata, viene visualizzato un avviso in Monitoraggio replica e viene registrato un evento nel registro eventi di Windows. Il raggiungimento di una soglia può inoltre generare un avviso SQL Server Agent. Per altre informazioni, vedere [Impostare valori di soglia e avvisi in Monitoraggio replica](monitor/set-thresholds-and-warnings-in-replication-monitor.md) e [Monitorare la replica a livello di programmazione](monitor/monitoring-replication-overview.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 La risoluzione del problema dipende dal motivo per il quale è stato generato l'avviso:  
  
-   Se la soglia è stata superata ma la sottoscrizione non è ancora scaduta, sincronizzare la sottoscrizione. Per altre informazioni, vedere [Sincronizzare i dati](synchronize-data.md).  
  
-   È possibile che la sottoscrizione scada se l'agente è stato eseguito ma la replica delle modifiche non è stata completata correttamente. Per la replica transazionale verificare che l'agente di distribuzione e l'agente di lettura log siano in esecuzione. Per la replica di tipo merge verificare che l'agente di merge sia in esecuzione. Per altre informazioni su come avviare questi agenti, vedere [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [Concetti di base relativi ai file eseguibili dell'agente di replica](concepts/replication-agent-executables-concepts.md).  
  
-   Se la sottoscrizione è scaduta, sarà necessario reinizializzarla oppure eliminarla e ricrearla, a seconda del tipo di sottoscrizione e da quanto tempo è scaduta. Per altre informazioni, vedere [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  
