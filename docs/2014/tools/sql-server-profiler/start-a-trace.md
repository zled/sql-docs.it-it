---
title: Avviare una traccia | Microsoft Docs
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
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb735810bcf265076fde9e3834dc7404d1f45079
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156827"
---
# <a name="start-a-trace"></a>Avviare una traccia
  Dopo aver definito una nuova traccia o creato un modello con [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è possibile avviare, sospendere o arrestare l'acquisizione dei dati in base alla nuova definizione di traccia o modello.  
  
## <a name="starting-a-trace"></a>Avvio di una traccia  
 Quando viene avviata una traccia e l'origine definita è un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea una coda come posizione temporanea per gli eventi del server acquisiti.  
  
 Se si utilizza [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per accedere a Traccia SQL, l'avvio di una traccia comporta l'apertura di una nuova finestra di traccia (se non vi è una finestra già aperta) e i dati vengono acquisiti immediatamente.  
  
 Quando si utilizzano le stored procedure di sistema di [!INCLUDE[tsql](../../includes/tsql-md.md)] per l'accesso a Traccia SQL, perché i dati vengano acquisiti è necessario avviare una traccia a ogni avvio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dopo l'avvio di una traccia è possibile modificarne unicamente il nome.  
  
> [!NOTE]  
>  Quando si utilizzano tracce esistenti, è possibile visualizzare le proprietà ma non modificarle. Per modificare le proprietà, arrestare o sospendere la traccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare una traccia automaticamente dopo la connessione a un Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Sospendere una traccia &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md)   
 [Arrestare una traccia &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md)   
 [Cancellare il contenuto di una finestra di traccia &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md)   
 [Eseguire una traccia dopo la sospensione o l'arresto &#40;SQL Server Profiler&#41;](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  