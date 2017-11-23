---
title: Architetture di accesso ai Database standard | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2cb4ddb3b51763772b00b7d17691e60109d1d6aa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="standard-database-access-architectures"></a>Architetture di accesso ai Database standard
Osservando i componenti di accesso database descritti nella sezione precedente, si scopre che due di essi, protocolli di flusso di dati e le interfacce di programmazione, sono buoni candidati per la standardizzazione. I due componenti: IPC meccanismo e protocolli di rete, non solo si trovano in un livello troppo basso, ma sono entrambi elevata dipendenti della rete e il sistema operativo. È anche un terzo approccio-gateway, che fornisce il possibilità per la standardizzazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Interfaccia di programmazione standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocollo del flusso di dati standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Gateway standard](../../odbc/reference/standard-gateway.md)
