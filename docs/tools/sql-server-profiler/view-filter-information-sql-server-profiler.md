---
title: Visualizzare informazioni sui filtri (SQL Server Profiler) | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c28d0daafecb0ef187a965f06e3477c7db08cb6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33076268"
---
# <a name="view-filter-information-sql-server-profiler"></a>Visualizzare informazioni sui filtri (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come visualizzare i filtri impostati sulle colonne di dati per le classi di evento utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Per visualizzare informazioni sui filtri  
  
1.  Aprire un file di traccia, una tabella di traccia o uno script SQL e scegliere **Proprietà** dal menu **File**. Se si intende modificare un modello di traccia o creare una nuova traccia, ignorare questo passaggio.  
  
2.  Nella scheda **Selezione eventi** fare clic con il pulsante destro del mouse sul nome della colonna di dati relativa al filtro da visualizzare e scegliere **Modifica filtro colonne**.  
  
3.  Nella finestra di dialogo **Modifica filtro** espandere gli operatori di confronto del filtro per visualizzare il valore assegnato al criterio specificato. Ripetere i passaggi 2 e 3 per tutte le colonne per le quali si desidera visualizzare le informazioni sui filtri.  
  
> [!NOTE]  
>  Gli operatori di confronto per i quali sono disponibili valori assegnati sono formattati in grassetto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
