---
title: Contatori delle prestazioni XTP (OLTP In memoria) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2362807e8e033fbc55e75a08d9dec80bf3782e03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084051"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Contatori delle prestazioni XTP (OLTP in memoria)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce oggetti e contatori utilizzabili da Performance Monitor per il monitoraggio dell'attività OLTP in memoria.  
  
##  <a name="SQLServerPOs"></a> Oggetti prestazione XTP (OLTP In memoria) di  
 Nella seguente tabella vengono descritti gli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Oggetto prestazione|Description|  
|------------------------|-----------------|  
|[Cursori XTP](../cursors.md)|L'oggetto prestazione XTP Cursors contiene contatori correlati ai cursori interni del motore XTP. I cursori sono gli utilizzi del motore XTP per elaborare di blocchi predefiniti di basso livello [!INCLUDE[tsql](../../includes/tsql-md.md)] le query. Di conseguenza, in genere non si ha controllo diretto su di essi.|  
|[XTP Garbage Collection](sql-server-xtp-garbage-collection.md)|L'oggetto prestazione XTP Garbage Collection contiene contatori correlati al Garbage Collector del motore XTP.|  
|[XTP Phantom Processor](sql-server-xtp-phantom-processor.md)|L'oggetto prestazione XTP Phantom Processor contiene contatori correlati al sottosistema di elaborazione fantasma del motore XTP. Con questo componente è possibile rilevare le righe fantasma nelle transazioni in esecuzione a livello di isolamento SERIALIZABLE.|  
|[Archiviazione XTP](sql-server-xtp-storage.md)|L'oggetto prestazione XTP Storage contiene contatori correlati all'archiviazione XTP di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Log delle transazioni XTP](sql-server-xtp-transaction-log.md)|L'oggetto prestazione XTP Transaction Log contiene contatori correlati alla registrazione transazioni XTP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Transazioni XTP](sql-server-xtp-transactions.md)|L'oggetto prestazione XTP Transactions contiene contatori correlati alle transazioni del motore XTP in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
