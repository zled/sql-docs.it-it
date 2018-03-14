---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1fed5d48e7c67bda97017732b7231c4d051ac4a6
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng021075"></a>MSSQL_ENG021075
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21075|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Lo snapshot iniziale per la pubblicazione '%s' non è ancora disponibile.|  
  
## <a name="explanation"></a>Spiegazione  
 L'errore MSSQL_ENG021075 viene generato in caso di avvio dell'agente di distribuzione o di merge prima che l'agente snapshot abbia completato la generazione dello snapshot.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se l'agente snapshot per la pubblicazione non è stato avviato dopo la creazione della sottoscrizione oppure dall'ultima reinizializzazione della sottoscrizione, avviare l'agente snapshot e attenderne il completamento prima di avviare l'agente di distribuzione o di merge. Per altre informazioni, vedere [Creare e applicare lo snapshot](../../relational-databases/replication/create-and-apply-the-snapshot.md).  
  
 Se l'agente snapshot non viene completato, controllarne la cronologia per individuare eventuali errori e risolverli. Per informazioni sui dettagli di stato e di errore dell'agente di visualizzazione in Monitoraggio replica, vedere [Visualizzare le informazioni ed eseguire attività relative agli agenti associati a una pubblicazione &#40;Monitoraggio replica&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
 Se l'errore continua a verificarsi, aumentare il livello di dettaglio per la registrazione delle operazioni dell'agente e specificare un file di output per il log. A seconda del contesto dell'errore, in questo modo si potrebbero ottenere ulteriori informazioni sui passaggi che conducono all'errore e/o messaggi di errore aggiuntivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
