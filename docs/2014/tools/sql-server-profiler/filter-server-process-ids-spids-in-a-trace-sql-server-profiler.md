---
title: Filtrare gli ID del processo server (SPID) in una traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e2a74ded1d393932ee85075c932c06babdd980af
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169537"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>Filtrare gli ID del processo server (SPID) in una traccia (SQL Server Profiler)
  In questo argomento viene descritta la procedura per il filtraggio degli identificatori del processo server (SPID) in una traccia mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Per filtrare gli ID di sistema in una traccia  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella casella **Nome traccia** digitare un nome per la traccia.  
  
3.  Nell'elenco dei nomi di **modello**selezionare un modello di traccia.  
  
4.  Facoltativamente, è possibile specificare un file o una tabella di destinazione in cui salvare i risultati della traccia.  
  
5.  Nella scheda **Selezione eventi**fare clic sull'intestazione di colonna **SPID**per visualizzare la finestra di dialogo **Modifica filtro** . È anche possibile fare clic con il pulsante destro del mouse sull'intestazione di colonna e scegliere **Modifica filtro colonne**. Se non viene visualizzata la colonna **SPID** , selezionare la casella **Mostra tutte le colonne** .  
  
6.  Nella finestra di dialogo **Modifica filtro** espandere l'operatore di confronto appropriato e immettere uno SPID come valore di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  