---
title: MSSQL_ENG014164 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014164 error
ms.assetid: cd81b601-2ec3-4358-ad58-c2655496e6a1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2535871ca1ddb129d34adac088d5e9be3d6ed61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197151"
---
# <a name="mssqleng014164"></a>MSSQL_ENG014164
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14164|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|È stata impostata la soglia [%s:%s] per la pubblicazione [%s]. Verificare che l'agente di merge sia in esecuzione e sia in grado di rispettare i requisiti previsti.|  
  
## <a name="explanation"></a>Spiegazione  
 La replica consente di attivare avvisi per numerose condizioni, tra cui la mancata elaborazione di un numero di righe sufficiente durante la sincronizzazione delle modifiche tra un server di pubblicazione e un Sottoscrittore. È possibile specificare momenti diversi per connessioni LAN e remote.  
  
 Quando si attiva un avviso utilizzando Monitoraggio replica o [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), viene specificata una soglia che determina quando è generato l'avviso. Quando tale soglia viene raggiunta o superata, viene visualizzato un avviso in Monitoraggio replica e viene registrato un evento nel registro eventi di Windows. Il raggiungimento di una soglia può inoltre generare un avviso SQL Server Agent. Per altre informazioni, vedere [Impostare valori di soglia e avvisi in Monitoraggio replica](monitor/set-thresholds-and-warnings-in-replication-monitor.md) e [Monitorare la replica a livello di programmazione](monitor/monitoring-replication-overview.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 Se una sottoscrizione non è conforme a una soglia di elaborazione delle righe, è necessario stabilire se il fenomeno dipende da un problema di prestazioni del sistema o se la soglia deve essere regolata. Dopo avere configurato la replica, sviluppare dati di riferimento per le prestazioni in modo da poter stabilire il comportamento della replica in presenza del carico di lavoro tipico delle applicazioni e della topologia in uso. Includere nei dati di riferimento anche il numero di righe elaborate al fine di poter impostare un valore appropriato per la soglia.  
  
 Se il valore soglia è appropriato ma viene superato, è necessario individuare l'area del sistema a cui è dovuto il collo di bottiglia a livello di prestazioni. Per ulteriori informazioni sul monitoraggio e la risoluzione dei problemi delle prestazioni di replica, vedere gli argomenti seguenti:  
  
-   [Monitorare le prestazioni con Monitoraggio replica](monitor/monitor-performance-with-replication-monitor.md) (in particolare la sezione "Visualizzazione di statistiche dettagliate sulle prestazioni di sincronizzazione per la replica di tipo merge")  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  
