---
title: La serializzabilità è infatti | Documenti Microsoft
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
helpviewer_keywords:
- transaction isolation [ODBC]
- transactions [ODBC], serialization
- serialization [ODBC]
- transactions [ODBC], isolation
ms.assetid: 142e4ac0-2977-4a2b-96ae-c9e5bd2c448a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa983da3ad05b6f4c4ac29fbdf986a7a8a350e34
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="serializability"></a>Serializzabilità è infatti
In teoria, le transazioni devono essere *serializzabile*. Le transazioni vengono considerate serializzabile se i risultati dell'esecuzione di transazioni contemporaneamente sono gli stessi, come i risultati dell'esecuzione di tali in modo seriale, vale a dire, una dopo l'altra. Non è importante la transazione viene eseguito per primo, solo che il risultato non rifletta qualsiasi combinazione delle transazioni.  
  
 Si supponga, ad esempio, la transazione A Moltiplica i valori dei dati per 2 e 1 transazione B aggiunge i valori dei dati. Si supponga ora che sono presenti due valori di dati: 0 e 10. Se queste operazioni vengono eseguite una dopo l'altro, i nuovi valori verranno 1 e 21 se la transazione viene eseguita per prima, o 2 e 22 se transazione B viene eseguito per primo. Ma cosa accade se l'ordine in cui vengono eseguite due operazioni è diverso per ogni valore? Se l'oggetto viene eseguito primo del primo valore di transazione e transazione B viene eseguiti per primo al secondo valore, i nuovi valori sono 1 e 22. Se questo ordine è invertito, i nuovi valori sono 2 e 21. Le transazioni sono serializzabili se 1, 21 e 2, 22 sono riportati i risultati solo possibili. Le transazioni non sono serializzabile se 1, 22 o 2, 21 è un risultato possibili.  
  
 Pertanto, perché è la serializzabilità è infatti consigliabile? In altre parole, perché è importante che venga visualizzato di una transazione termina prima dell'avvio della transazione successiva? Si consideri il seguente problema. Un agente sta entrando ordini allo stesso tempo che un clerk verrà inviati distinte. Si supponga che l'agente inserisce un ordine di azienda X ma non esegue il commit. l'agente è continuano a comunicare con il rappresentante dall'azienda X. Il clerk richiede un elenco di tutti gli ordini aperti e consente di individuare l'ordine per l'azienda X e li invia una fattura. Ora il rappresentante X società decide che desiderano modificare l'ordine, in modo che l'agente viene modificato prima di eseguire il commit della transazione. Società X Ottiene un effetto non corretto.  
  
 Se le transazioni del venditore e del clerk serializzabile, il problema non sarebbe state eseguite. Transazione del venditore potrebbe avere prima dell'avvio transazione del clerk, nel qual caso il clerk verrà hanno inviata la fattura corretta o potrebbe avere la transazione del clerk prima dell'avvio transazione del venditore, nel qual caso il Clerk sarebbe non hai inviato una fattura a X società affatto.
