---
title: Visualizzare informazioni sui filtri (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0c040ead976dc02e8309cb65dbd615acd11ae3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253833"
---
# <a name="view-filter-information-sql-server-profiler"></a>Visualizzare informazioni sui filtri (SQL Server Profiler)
  In questo argomento viene descritto come visualizzare i filtri impostati sulle colonne di dati per le classi di evento utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Per visualizzare informazioni sui filtri  
  
1.  Aprire un file di traccia, una tabella di traccia o uno script SQL e scegliere **Proprietà** dal menu **File**. Se si intende modificare un modello di traccia o creare una nuova traccia, ignorare questo passaggio.  
  
2.  Nella scheda **Selezione eventi** fare clic con il pulsante destro del mouse sul nome della colonna di dati relativa al filtro da visualizzare e scegliere **Modifica filtro colonne**.  
  
3.  Nella finestra di dialogo **Modifica filtro** espandere gli operatori di confronto del filtro per visualizzare il valore assegnato al criterio specificato. Ripetere i passaggi 2 e 3 per tutte le colonne per le quali si desidera visualizzare le informazioni sui filtri.  
  
> [!NOTE]  
>  Gli operatori di confronto per i quali sono disponibili valori assegnati sono formattati in grassetto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
