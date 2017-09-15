---
title: Architetture di accesso ai Database standard | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff9ebb61d8a0446f4c6015dd5c0ae56c22ebfc45
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="standard-database-access-architectures"></a>Architetture di accesso ai Database standard
Osservando i componenti di accesso database descritti nella sezione precedente, si scopre che due di essi, protocolli di flusso di dati e le interfacce di programmazione, sono buoni candidati per la standardizzazione. I due componenti: IPC meccanismo e protocolli di rete, non solo si trovano in un livello troppo basso, ma sono entrambi elevata dipendenti della rete e il sistema operativo. È anche un terzo approccio-gateway, che fornisce il possibilità per la standardizzazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Interfaccia di programmazione standard](../../odbc/reference/standard-programming-interface.md)  
  
-   [Protocollo del flusso di dati standard](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Gateway standard](../../odbc/reference/standard-gateway.md)
