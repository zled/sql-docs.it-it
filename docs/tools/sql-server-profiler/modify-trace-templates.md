---
title: Modificare modelli di traccia | Documenti Microsoft
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 64a49875ae33de199305af4b172acb5e8f234034
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="modify-trace-templates"></a>Modificare modelli di traccia
  È possibile modificare i modelli salvati in un file nel computer locale che esegue [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e inoltre modificare i modelli da essi derivati. Per modificare i modelli esistenti, è possibile modificarne le proprietà, ad esempio le classi di evento e le colonne di dati, nell'ordine in cui sono state originariamente impostate nella scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia** . È possibile aggiungere o rimuovere classi di evento e colonne di dati, nonché modificare i filtri. Dopo avere modificato il modello, viene creato un modello specifico dell'utente e il modello di sistema originale rimarrà inalterato. Per altre informazioni, vedere [Salvare tracce e modelli di traccia](../../tools/sql-server-profiler/save-traces-and-trace-templates.md).  
  
 Potrebbe essere necessario ricavare un modello da un file di traccia esistente nel caso non sia possibile risalire al modello originale utilizzato per creare la traccia oppure se si desidera rieseguire la stessa traccia in un momento successivo. Quando si utilizzano tracce esistenti, è possibile visualizzare le proprietà ma non modificarle. Per modificare le proprietà, arrestare o sospendere la traccia. Per altre informazioni, vedere [Derivare un modello da un file di traccia o da una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) e [Ottenere un modello da una traccia in esecuzione &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
## <a name="to-modify-a-trace-template"></a>Per modificare un modello di traccia  
  
1.  Scegliere **Modelli** dal menu **File**, quindi fare clic su **Modifica modello**.  
  
2.  Nella scheda **Generale** della finestra di dialogo **Proprietà modello di traccia** è possibile modificare il tipo di server e il nome del modello oppure scegliere di usare un modello predefinito per il tipo di server.  
  
3.  Nel **selezione eventi** scheda, utilizzare il controllo griglia per aggiungere o rimuovere eventi e colonne di dati dal file di traccia, come indicato di seguito.  
  
    -   Per aggiungere un evento, espandere la categoria di eventi appropriata nella colonna **Eventi** e quindi selezionare il nome dell'evento.  
  
    -   Quando si aggiunge un evento, tutte le colonne di dati significative vengono incluse per impostazione predefinita. Per rimuovere una colonna di dati per un evento da una traccia, deselezionare la casella di controllo nella colonna di dati per l'evento.  
  
    -   Per aggiungere i filtri, fare clic sul nome della colonna di dati e specificare i criteri del filtro nella finestra di dialogo **Modifica filtro** . È anche possibile fare clic con il pulsante destro del mouse sul nome della colonna di dati e scegliere **Modifica filtro colonne** per avviare la finestra di dialogo **Modifica filtro** . Fare clic su **OK** per aggiungere il filtro.  
  
4.  Fare clic su **salvare**, oppure fare clic su **Salva con nome** per salvare il modello di traccia in un altro nome.  
  
## <a name="next-steps"></a>Passaggi successivi  
[Avviare una traccia](../../tools/sql-server-profiler/start-a-trace.md)  
[Creare una traccia](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
[Modificare una traccia esistente tramite Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
[Specificare eventi e colonne di dati per una traccia utilizzando SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
[SP-traccia-setevent-transact-sql](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  

