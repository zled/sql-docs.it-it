---
title: Filtrare gli ID del processo Server (SPID) in una traccia (SQL Server Profiler) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b113e50edcd72ff72717cae44166817478c959b9
ms.sourcegitcommit: 34d3497039141d043429eed15d82973b18ad90f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>Filtrare gli ID del processo server (SPID) in una traccia (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In questo argomento viene descritto come filtrare gli identificatori di processo server (SPID) in una traccia utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Per filtrare gli ID di sistema in una traccia  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia** .  
  
    > [!NOTE]  
    >  Se **Avvia traccia non appena viene stabilita una connessione** è selezionata, il **proprietà traccia** non viene visualizzata la finestra di dialogo e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere il **strumenti** menu, fare clic su **opzioni**e deselezionare il **Avvia traccia non appena viene stabilita una connessione** casella di controllo.  
  
2.  Nella casella **Nome traccia** digitare un nome per la traccia.  
  
3.  Nel **utilizzare il modello** elenco dei nomi, selezionare un modello di traccia.  
  
4.  Facoltativamente, è possibile specificare un file o una tabella di destinazione in cui salvare i risultati della traccia.  
  
5.  Nel **selezione eventi** scheda, fare clic su di **SPID** sull'intestazione di colonna per avviare il **Modifica filtro** la finestra di dialogo. È anche possibile fare clic con il pulsante destro del mouse sull'intestazione di colonna e scegliere **Modifica filtro colonne**. Se non viene visualizzata la colonna **SPID** , selezionare la casella **Mostra tutte le colonne** .  
  
6.  Nella finestra di dialogo **Modifica filtro** espandere l'operatore di confronto appropriato e immettere uno SPID come valore di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
