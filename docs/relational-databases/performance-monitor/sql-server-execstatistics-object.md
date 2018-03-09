---
title: Oggetto ExecStatistics di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 837b52d5d457a4466a46d08df918e25616d14bff
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-execstatistics-object"></a>Oggetto ExecStatistics di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L'oggetto **SQLServer:ExecStatistics** di Microsoft SQL Server include contatori che consentono di monitorare diversi tipi di esecuzioni.  
  
 Nella tabella seguente vengono descritti i contatori **Exec Statistics** di SQL Server.  
  
|Contatori Exec Statistics di SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Query distribuite**|Statistiche relative all'esecuzione di query distribuite.|  
|**Chiamate DTC**|Statistiche relative all'esecuzione di chiamate DTC.|  
|**Procedure estese**|Statistiche relative all'esecuzione di procedure estese.|  
|**Chiamate OLEDB**|Statistiche relative all'esecuzione di chiamate OLEDB.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Elemento|Description|  
|----------|-----------------|  
|**Tempo di esecuzione (ms) medio**|Durata media per il tipo di esecuzione selezionato.|  
|**Tempo di esecuzione (ms) cumulativo al secondo**|Tempo di esecuzione complessivo al secondo per il tipo di esecuzione selezionato.|  
|**Esecuzioni in corso**|Numero di esecuzioni in corso per il tipo di esecuzione selezionato.|  
|**Esecuzioni avviate al secondo**|Numero di esecuzioni avviate al secondo per il tipo di esecuzione selezionato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
