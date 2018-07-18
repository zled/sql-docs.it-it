---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78f4184937f6bf052b2c9bf8a4c434eabb5b192e
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357233"
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
  
  
