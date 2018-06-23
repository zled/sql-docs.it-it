---
title: Contatori delle prestazioni XTP (OLTP In memoria) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b12c482300ff8908236d1eda9d0e030df4b2e356
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157132"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Contatori delle prestazioni XTP (OLTP in memoria)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce oggetti e contatori utilizzabili da Performance Monitor per il monitoraggio dell'attività OLTP in memoria.  
  
##  <a name="SQLServerPOs"></a> Oggetti prestazione di XTP (OLTP In memoria)  
 Nella seguente tabella vengono descritti gli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Oggetto prestazione|Description|  
|------------------------|-----------------|  
|[XTP Cursors](../cursors.md)|L'oggetto prestazione XTP Cursors contiene contatori correlati ai cursori interni del motore XTP. I cursori sono predefiniti di basso livello blocchi utilizzati dal motore XTP per elaborare [!INCLUDE[tsql](../../includes/tsql-md.md)] query. Di conseguenza, in genere non si ha controllo diretto su di essi.|  
|[XTP Garbage Collection](sql-server-xtp-garbage-collection.md)|L'oggetto prestazione XTP Garbage Collection contiene contatori correlati al Garbage Collector del motore XTP.|  
|[XTP Phantom Processor di](sql-server-xtp-phantom-processor.md)|L'oggetto prestazione XTP Phantom Processor contiene contatori correlati al sottosistema di elaborazione fantasma del motore XTP. Con questo componente è possibile rilevare le righe fantasma nelle transazioni in esecuzione a livello di isolamento SERIALIZABLE.|  
|[Archiviazione XTP](sql-server-xtp-storage.md)|L'oggetto prestazione XTP Storage contiene contatori correlati all'archiviazione XTP di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Log delle transazioni XTP](sql-server-xtp-transaction-log.md)|L'oggetto prestazione XTP Transaction Log contiene contatori correlati alla registrazione transazioni XTP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Transazioni XTP](sql-server-xtp-transactions.md)|L'oggetto prestazione XTP Transactions contiene contatori correlati alle transazioni del motore XTP in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  