---
title: Modificare modelli di traccia | Documenti Microsoft
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
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08c08bd8838380ce1054e13697aa6873a8e98860
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171346"
---
# <a name="modify-trace-templates"></a>Modificare modelli di traccia
  È possibile modificare i modelli salvati in un file nel computer locale che esegue [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e inoltre modificare i modelli da essi derivati. Per modificare i modelli esistenti, è possibile modificarne le proprietà, ad esempio le classi di evento e le colonne di dati, nell'ordine in cui sono state originariamente impostate nella scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia** . È possibile aggiungere o rimuovere classi di evento e colonne di dati, nonché modificare i filtri. Dopo avere modificato il modello, viene creato un modello specifico dell'utente e il modello di sistema originale rimarrà inalterato. Per altre informazioni, vedere [Salvare tracce e modelli di traccia](save-traces-and-trace-templates.md).  
  
 Potrebbe essere necessario ricavare un modello da un file di traccia esistente nel caso non sia possibile risalire al modello originale utilizzato per creare la traccia oppure se si desidera rieseguire la stessa traccia in un momento successivo. Quando si utilizzano tracce esistenti, è possibile visualizzare le proprietà ma non modificarle. Per modificare le proprietà, arrestare o sospendere la traccia. Per altre informazioni, vedere [Derivare un modello da un file di traccia o da una tabella di traccia &#40;SQL Server Profiler&#41;](sql-server-profiler.md) e [Ottenere un modello da una traccia in esecuzione &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Per creare un modello di traccia**  
  
 [Creare un modello di traccia &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)  
  
 **Per eseguire una traccia da un modello di traccia**  
  
 [Creare una traccia &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)  
  
 **Per modificare un modello di traccia**  
  
 [Utilizzo di SQL Server Profiler](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [Utilizzo di Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Per aggiungere o rimuovere eventi da un modello di traccia o da un file di traccia**  
  
 [Utilizzo di SQL Server Profiler](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Utilizzo di Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare una traccia](start-a-trace.md)  
  
  
