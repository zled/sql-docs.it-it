---
title: Filtrare gli eventi in base all'ora di inizio (SQL Server Profiler) | Microsoft Docs
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
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f52726d45b27dfc9a4a7f86f4a0261219e26c7e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063220"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>Filtrare gli eventi in base all'ora di inizio (SQL Server Profiler)
  In questo argomento viene descritta la procedura per filtrare gli eventi di traccia in base all'ora di inizio mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>Per filtrare un evento in base all'ora di inizio  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella casella **Nome traccia** digitare un nome per la traccia.  
  
3.  Nell'elenco dei nomi di **modello**selezionare un modello di traccia.  
  
4.  Facoltativamente, specificare una destinazione per i risultati della traccia.  
  
5.  Nella scheda **Selezione eventi**fare clic sull'intestazione di colonna **StartTime** . È inoltre possibile fare clic con il pulsante destro del mouse sull'intestazione di colonna e quindi scegliere **Modifica filtro colonne** per avviare la finestra di dialogo **Modifica filtro** .  
  
6.  Espandere **maggiore** oppure **minore**, quindi immettere un `datetime` valore nel campo visualizzato sotto l'operatore di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  