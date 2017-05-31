---
title: Oggetto ExecStatistics di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 709d44983ef7010b36de6238ce99b2d20397017a
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-execstatistics-object"></a>Oggetto ExecStatistics di SQL Server
  L'oggetto **SQLServer:ExecStatistics** di Microsoft SQL Server include contatori che consentono di monitorare diversi tipi di esecuzioni.  
  
 Nella tabella seguente vengono descritti i contatori **Exec Statistics** di SQL Server.  
  
|Contatori Exec Statistics di SQL Server|Descrizione|  
|-----------------------------------------|-----------------|  
|**Query distribuite**|Statistiche relative all'esecuzione di query distribuite.|  
|**Chiamate DTC**|Statistiche relative all'esecuzione di chiamate DTC.|  
|**Procedure estese**|Statistiche relative all'esecuzione di procedure estese.|  
|**Chiamate OLEDB**|Statistiche relative all'esecuzione di chiamate OLEDB.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Elemento|Descrizione|  
|----------|-----------------|  
|**Tempo di esecuzione (ms) medio**|Durata media per il tipo di esecuzione selezionato.|  
|**Tempo di esecuzione (ms) cumulativo al secondo**|Tempo di esecuzione complessivo al secondo per il tipo di esecuzione selezionato.|  
|**Esecuzioni in corso**|Numero di esecuzioni in corso per il tipo di esecuzione selezionato.|  
|**Esecuzioni avviate al secondo**|Numero di esecuzioni avviate al secondo per il tipo di esecuzione selezionato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
