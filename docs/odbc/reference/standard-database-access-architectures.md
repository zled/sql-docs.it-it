---
title: Architetture di accesso ai Database standard | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a699116279ebbc5711d5aa15ac0c921be8baaa7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="standard-database-access-architectures"></a>Architetture di accesso ai Database standard
Osservando i componenti di accesso database descritti nella sezione precedente, si scopre che due di essi, protocolli di flusso di dati e le interfacce di programmazione, sono buoni candidati per la standardizzazione. I due componenti: IPC meccanismo e protocolli di rete, non solo si trovano in un livello troppo basso, ma sono entrambi elevata dipendenti della rete e il sistema operativo. È anche un terzo approccio-gateway, che fornisce il possibilità per la standardizzazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Interfaccia di programmazione standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocollo del flusso di dati standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Gateway standard](../../odbc/reference/standard-gateway.md)
