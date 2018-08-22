---
title: Procedure consigliate per chiamare stored procedure compilate in modo nativo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3c867721b0e7868a57f4a76108e2b9029dc22172
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394274"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Procedure consigliate per chiamare stored procedure compilate in modo nativo
  Le stored procedure compilate in modo nativo:  
  
-   Vengono in genere utilizzate nelle parti critiche per le prestazioni di un'applicazione.  
  
-   Vengono eseguite di frequente.  
  
-   Devono essere molto veloci.  
  
 Il vantaggio a livello di prestazioni garantito dall'utilizzo di una stored procedure compilata in modo nativo aumenta con il numero di righe e la quantità di logica elaborata dalla procedura. Ad esempio, tramite una stored procedure compilata in modo nativo vengono garantite prestazioni migliori se si utilizzato uno o più degli elementi seguenti:  
  
-   Aggregazione.  
  
-   Join a cicli annidati.  
  
-   Operazioni di selezione, inserimento, aggiornamento ed eliminazione a più istruzioni.  
  
-   Espressioni complesse.  
  
-   Logica procedurale, ad esempio cicli e istruzioni condizionali.  
  
 Se è necessario elaborare una sola riga, l'utilizzo di una stored procedure compilata in modo nativo non può garantire un vantaggio in termini di prestazioni.  
  
 Per evitare che nel server debbano essere eseguiti il mapping dei nomi di parametro e la conversione dei tipi:  
  
-   Associare i tipi dei parametri passati alla stored procedure ai tipi nella definizione della stored procedure.  
  
-   Utilizzare i parametri ordinali (senza nome) per chiamare le stored procedure compilate in modo nativo. Per un'esecuzione ottimale, non utilizzare parametri denominati.  
  
 L'utilizzo di parametri denominati (inefficiente) con stored procedure compilate in modo nativo può essere rilevato tramite l'XEvent `hekaton_slow_parameter_passing` con `reason=named_parameters`.  
  
 Analogamente, è possibile rilevare l'utilizzo di tipi non corrispondenti tramite lo stesso XEvent `hekaton_slow_parameter_passing`, con `reason=parameter_conversion`.  
  
 Poiché è necessario implementare la logica per eseguire nuovi tentativi quando si utilizzano le tabelle ottimizzate per la memoria (in molti scenari) e poiché è necessario aggirare le limitazioni di alcune funzionalità, è possibile creare una stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] interpretata dal wrapper. Per un esempio, vedere [linee guida per la logica di tentativi per le transazioni nelle tabelle ottimizzate per la memoria](memory-optimized-tables.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](natively-compiled-stored-procedures.md)  
  
  
