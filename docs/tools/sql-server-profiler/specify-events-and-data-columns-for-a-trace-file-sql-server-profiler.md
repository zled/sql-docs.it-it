---
title: Specificare eventi e colonne di dati per un file di traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45184a8741296f43b29029776741def6704a6aaf
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a>Specificare eventi e colonne di dati per un file di traccia (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come specificare classi di evento e colonne di dati per le tracce tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a>Per specificare eventi e colonne di dati per una traccia  
  
1.  Nella finestra di dialogo **Proprietà traccia** o **Proprietà modello di traccia** fare clic sulla scheda **Selezione eventi** .  
  
     La scheda **Selezione eventi** contiene un controllo griglia, ovvero una tabella che include tutte le classi di evento tracciabili. La tabella contiene una riga per ogni classe di evento. Le classi di evento possono differire leggermente a seconda del tipo e della versione del server cui si è connessi. Le classi di eventi sono identificate nella colonna **Eventi**della griglia e sono raggruppate per categoria di eventi. Nelle altre colonne sono elencate le colonne di dati che possono essere restituite per ogni classe di evento.  
  
2.  Nella scheda **Selezione eventi**usare il controllo griglia per aggiungere o rimuovere eventi e colonne di dati dal file di traccia.  
  
3.  Per rimuovere eventi dalla traccia, deselezionare la casella di controllo nella colonna **Eventi** relativa a ogni classe di evento.  
  
4.  Per includere eventi in una traccia, selezionare la casella nella colonna **Eventi** per ogni classe di evento oppure selezionare una colonna di dati corrispondente a un evento.  
  
> [!IMPORTANT]  
>  Se la traccia verrà correlata ai dati di Monitoraggio di sistema o di Performance Monitor, è necessario includere nella traccia le colonne di dati **Ora di inizio** e **Ora di fine** .  
  
 Quando si include una classe di evento, nella traccia vengono inserite tutte le colonne di dati associate se è stata selezionata la casella corrispondente a un evento. Se è stata selezionata la casella per una colonna specifica, nella traccia verrà inclusa solo tale colonna.  
  
1.  Per rimuovere colonne di dati da una classe di evento, deselezionare le caselle di controllo della colonna di dati nella riga della classe oppure fare clic con il pulsante destro del mouse sull'intestazione della colonna e selezionare l'opzione **Deseleziona colonna** .  
  
2.  Applicare facoltativamente filtri alla traccia. Per altre informazioni, vedere [Filtrare eventi in una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
