---
title: Visualizzare informazioni sui filtri (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e194fa956ba1f43ae53ee37f3be15af2dfa7d4a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600399"
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
  
  
